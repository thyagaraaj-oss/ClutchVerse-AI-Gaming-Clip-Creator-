# Development Roadmap

## Phase 0 — Repository and foundation
- [ ] Create the GitHub repository.
- [ ] Add README, license decision, `.gitignore`, and dependency file.
- [ ] Establish Python package structure and logging.
- [ ] Add a small authorized test video.

## Phase 1 — Local media workflow
- [ ] Build Streamlit upload/local-file interface.
- [ ] Validate media and probe metadata with ffprobe.
- [ ] Display duration, resolution, frame rate, and audio stream status.

## Phase 2 — Transcription and candidate clips
- [ ] Integrate Faster-Whisper behind an adapter.
- [ ] Store timestamped transcript segments.
- [ ] Implement simple configurable highlight heuristics.
- [ ] Add manual timestamp entry and candidate review.

## Phase 3 — Vertical rendering
- [ ] Implement FFmpeg trim and encode pipeline.
- [ ] Add 9:16 crop and fit/blur background options.
- [ ] Validate rendered output and expose render logs.

## Phase 4 — Optional AI assistance
- [ ] Add Gemini integration for optional highlight explanations and metadata suggestions.
- [ ] Add graceful fallback when API is unavailable.
- [ ] Document data sent to the provider and obtain user consent.

## Phase 5 — Quality and release
- [ ] Add unit and integration tests.
- [ ] Test Windows setup on a clean environment.
- [ ] Add screenshots and a short demo using authorized footage.
- [ ] Publish release notes and limitations.

## Release gate
Do not describe a feature as available until its implementation and acceptance tests pass.
