# Test Plan

## Unit tests
- File extension and file-size validation.
- Timestamp validation (negative, reversed, non-finite, beyond duration).
- Highlight ranking with empty and non-empty transcripts.
- Render settings validation.
- Safe filename generation.

## Integration tests
- Probe a short sample MP4 with ffprobe.
- Extract audio from a sample with FFmpeg.
- Transcribe a short sample when Faster-Whisper is installed.
- Render a 5–10 second vertical MP4.
- Probe the output and verify resolution, duration, codecs, and audio presence where expected.

## Manual acceptance tests
1. Select a valid GTA gameplay recording.
2. Select an invalid file and confirm a clear validation message.
3. Run transcription and inspect timestamps.
4. Add or adjust a clip manually.
5. Render a vertical output.
6. Play the output and inspect framing, audio sync, and quality.
7. Test a source with no audio.
8. Test behavior when Gemini is unavailable.
9. Confirm `.env` is not tracked by Git.

## Definition of done for an MVP
- Main workflow completes without unhandled exceptions.
- Errors are visible and actionable.
- User can review/edit clip timestamps.
- Output is playable and validated.
- No secrets are committed.
