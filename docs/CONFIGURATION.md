# Configuration and Environment

## Environment variables

Use `.env` for local development only. Do not commit API keys.

| Variable | Required | Purpose |
|---|---|---|
| `GEMINI_API_KEY` | No | Optional Gemini integration |
| `CLUTCHVERSE_OUTPUT_DIR` | No | Output directory override |
| `CLUTCHVERSE_WHISPER_MODEL` | No | Faster-Whisper model name |

## Example `.env`

```dotenv
GEMINI_API_KEY=
CLUTCHVERSE_OUTPUT_DIR=data/output
CLUTCHVERSE_WHISPER_MODEL=base
```

## Suggested application defaults

- Output size: 1080×1920.
- Target duration: 40–50 seconds.
- Output FPS: 30 by default; allow 60 where source and hardware justify it.
- Video: H.264 MP4.
- Audio: AAC.
- Keep source files unchanged.
- Use a temporary working directory and clean it only after successful export or explicit user confirmation.

## Configuration principles

- Validate all user-supplied paths.
- Keep API keys out of source code and logs.
- Make model selection configurable.
- Provide a local-only mode that does not require Gemini.
