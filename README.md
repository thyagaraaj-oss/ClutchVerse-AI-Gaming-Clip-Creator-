# ClutchVerse

**AI-assisted GTA V / GTA VI gameplay highlight clipping and short-form video workflow.**

ClutchVerse is a proposed tool for turning gameplay recordings into engaging gaming highlights. The initial content focus is original GTA V gameplay. GTA VI support is intended only for footage the creator can lawfully access and use after the game's release; leaked or unauthorized material is out of scope.

> **Project status:** Documentation and proposed technical design. The technology choices below are a proposed stack, not a claim that every integration has already been implemented.

## Project purpose

Turn eligible GTA gameplay recordings into short, vertical highlight videos using transcription, highlight discovery, video trimming, and optional AI-assisted editing.

## Proposed capabilities

- Import a locally owned or otherwise authorized gameplay recording.
- Extract audio and generate a timestamped transcript.
- Identify candidate highlight moments using transcript cues and configurable heuristics.
- Review and adjust clip start/end times before rendering.
- Render vertical 9:16 clips with FFmpeg.
- Export MP4 files suitable for creator review and publishing.
- Optionally use an LLM to suggest titles, captions, descriptions, and highlight explanations.

## Proposed technology stack

| Area | Proposed technology | Responsibility |
|---|---|---|
| User interface | Streamlit | Local web interface and workflow controls |
| Application logic | Python | Orchestration, validation, clip metadata |
| Speech recognition | Faster-Whisper | Timestamped speech transcription |
| AI assistance | Google Gemini API | Optional highlight/title/caption suggestions |
| Video processing | FFmpeg / ffprobe | Probe, trim, scale, crop, encode, audio |
| Optional URL ingestion | yt-dlp | Only where the source and platform terms permit downloading |

Do not add a technology to the implemented stack or public project tags until it is actually integrated and tested.

## High-level workflow

1. Select an authorized local gameplay video.
2. Validate the file and inspect its streams and duration.
3. Transcribe speech when audio is available.
4. Generate candidate highlight timestamps.
5. Review candidates in the interface.
6. Render selected clips in vertical format.
7. Inspect the output and export it.

## Proposed output profile

- Aspect ratio: 9:16
- Resolution: 1080 × 1920
- Duration target: approximately 40–50 seconds (configurable)
- Frame rate: preserve source when appropriate or encode to a configured 30/60 FPS target
- Container: MP4
- Video codec: H.264
- Audio codec: AAC

These are starting defaults, not mandatory limits.

## Repository layout

```text
ClutchVerse/
├── app.py
├── config/
│   └── settings.example.toml
├── src/
│   ├── ingestion/
│   ├── transcription/
│   ├── highlights/
│   ├── rendering/
│   └── metadata/
├── tests/
├── data/
│   ├── input/
│   ├── temp/
│   └── output/
├── docs/
├── .env.example
├── .gitignore
├── requirements.txt
└── README.md
```

The layout is a recommended starting structure. Create modules as implementation proceeds.

## Quick start (development outline)

1. Install Python 3.10+ and FFmpeg.
2. Clone the repository after it has been created.
3. Create and activate a virtual environment.
4. Install Python dependencies.
5. Copy `.env.example` to `.env` and add an API key only if Gemini features are enabled.
6. Start the Streamlit app once `app.py` is implemented.

```powershell
python -m venv .venv
.venv\\Scripts\\Activate.ps1
python -m pip install --upgrade pip
pip install -r requirements.txt
streamlit run app.py
```

## Security and responsible use

- Process only gameplay files you own or are authorized to use.
- Respect game publisher policies, platform terms, music rights, and third-party copyrights.
- Do not use leaked GTA VI footage or bypass access controls.
- Keep API keys in environment variables; never commit `.env`.
- Treat downloaded or user-supplied media as untrusted input.
- Validate file extensions, size, duration, and FFmpeg exit status.
- Avoid uploading private recordings to third-party services without informed consent.

## Current known status

- Project name and GTA V / GTA VI focus: established.
- Purpose and proposed output profile: drafted.
- Proposed stack: identified, implementation not verified.
- GitHub repository: created at https://github.com/thyagaraaj-oss/ClutchVerse-AI-Gaming-Clip-Creator-; technical documentation has been added to the `main` branch.

See `docs/PROJECT_STATUS.md` before treating this design as implemented.
