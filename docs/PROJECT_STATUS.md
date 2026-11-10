# Project Status and Assumptions

This document separates established project direction from proposed engineering choices.

## Established
- Project name: ClutchVerse.
- Content focus: GTA V / GTA VI.
- Purpose: turn GTA gameplay into engaging highlights with AI-assisted clipping and editing.
- Initial content recommendation: use original GTA V gameplay.
- GTA VI: use only lawfully accessed footage after release; leaked footage is excluded.
- Proposed short-form target: around 40–50 seconds, vertical 9:16, 1080×1920, 30/60 FPS, energetic English commentary, quick cuts/zooms/sound effects.
- GitHub repository: https://github.com/thyagaraaj-oss/ClutchVerse-AI-Gaming-Clip-Creator-
- Technical documentation has been added to the repository's `main` branch.

## Proposed, not verified as implemented
- Python and Streamlit application.
- Google Gemini API for optional AI assistance.
- Faster-Whisper for speech transcription.
- FFmpeg for media processing.
- yt-dlp for optional URL ingestion, subject to authorization and platform terms.

## Not confirmed
- A runnable end-to-end application.
- Completed integrations with Gemini, Faster-Whisper, FFmpeg, or yt-dlp.
- Passing unit, integration, and Windows acceptance tests.

## Important
The repository currently contains technical planning documentation and starter configuration, not a verified finished executable product. Update this status as code is implemented and tested.
