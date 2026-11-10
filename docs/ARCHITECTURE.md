# Technical Architecture

## Architecture style
A modular Python application with a Streamlit presentation layer and separate services for ingestion, transcription, highlight selection, rendering, and metadata generation.

## Component responsibilities

| Component | Responsibility | Input | Output |
|---|---|---|---|
| Streamlit UI | Collect settings and show progress/results | User actions | Workflow requests |
| Ingestion | Validate and stage authorized source media | Local file | Staged media path + metadata |
| Media probe | Read streams, duration, dimensions, frame rate | Media path | Media metadata |
| Transcription | Produce timestamped speech segments | Audio/media | Transcript segments |
| Highlight engine | Rank candidate moments | Transcript + optional signals | Candidate time ranges |
| Review layer | Allow human correction | Candidate ranges | Approved clip ranges |
| Renderer | Trim, crop, scale, encode | Media + approved ranges | MP4 clips |
| Metadata helper | Suggest titles/descriptions | Clip context | Draft metadata |

## Data flow

```text
Creator
  |
  v
Streamlit UI
  |
  v
Input validation --> Media probe
  |                     |
  v                     v
Audio extraction --> Faster-Whisper (optional)
  |                     |
  +-----------> Transcript segments
                         |
                         v
                 Highlight candidate engine
                         |
                         v
                   Human review
                         |
                         v
                  FFmpeg renderer
                         |
                         v
                  MP4 output folder
                         |
                         v
                Creator inspection/export
```

## Suggested module boundaries

- `src/ingestion/`: file validation, staging, metadata probing.
- `src/transcription/`: audio extraction and Faster-Whisper adapter.
- `src/highlights/`: candidate generation, ranking, timestamp validation.
- `src/rendering/`: FFmpeg command construction and output validation.
- `src/metadata/`: optional Gemini adapter and prompt templates.
- `src/common/`: configuration, logging, shared data models.

## Core data models (suggested)

```python
from dataclasses import dataclass

@dataclass
class TranscriptSegment:
    start: float
    end: float
    text: str

@dataclass
class ClipCandidate:
    start: float
    end: float
    score: float
    reason: str

@dataclass
class RenderSettings:
    width: int = 1080
    height: int = 1920
    fps: int = 30
    video_codec: str = "libx264"
    audio_codec: str = "aac"
```

Validate that timestamps are finite, `start >= 0`, `end > start`, and `end` does not exceed source duration.

## Highlight discovery strategy

Start with transparent heuristics rather than promising fully autonomous understanding:
- Transcript phrase and excitement cues, configurable by the creator.
- Speech density or changes in audio energy.
- User-marked timestamps.
- Optional model-generated ranking based on transcript context.

The creator must be able to review and edit every candidate before rendering.

## Rendering strategy

- Use `ffprobe` to inspect source metadata.
- Use `ffmpeg` to trim selected time ranges.
- Scale and crop to 1080×1920 while keeping the important gameplay area visible.
- Normalize or preserve audio according to user settings.
- Capture process exit code and stderr.
- Verify output exists, is non-empty, and can be probed after rendering.

For gameplay with a wide field of view, a center crop can remove important HUD/action. Provide a crop-position option or a fit/blur-background mode in a later iteration.

## Failure handling

- Missing FFmpeg: show installation instructions.
- Unsupported or corrupt media: reject with a clear message.
- No audio stream: allow visual-only clipping.
- Transcription failure: permit manual timestamps.
- Gemini unavailable or quota exceeded: keep local clipping functional.
- Render failure: retain logs and do not report a successful export.
