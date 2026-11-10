# Project Overview

## Name
ClutchVerse

## One-line description
An AI-assisted workflow for finding, editing, and exporting short-form highlights from authorized GTA gameplay recordings.

## Purpose
Reduce the manual effort involved in reviewing long gameplay recordings and preparing concise highlight clips for creator platforms.

## Scope

### In scope
- GTA V gameplay recordings as the initial content source.
- GTA VI footage only when lawfully available to the creator and permitted for the intended use.
- Local file ingestion.
- Timestamped transcription where speech is present.
- Candidate highlight suggestions.
- Human review and clip adjustment.
- Vertical video rendering and export.
- Optional metadata suggestions (titles, descriptions, captions).

### Out of scope
- Leaked, stolen, or unauthorized game footage.
- Circumventing platform restrictions, DRM, or access controls.
- Automatic publishing without explicit creator review and authorization.
- Guaranteeing that a clip is copyright-free or guaranteed to go viral.
- Claiming that AI-generated highlight timestamps are always correct.

## Target users
Gaming creators who record GTA gameplay and want a repeatable workflow for preparing Shorts/Reels/TikTok-style videos.

## Success criteria
- User can select a valid local video file.
- The app can inspect media duration and streams.
- Transcription produces usable timestamps when enabled.
- Candidate clips can be reviewed and edited.
- FFmpeg produces a playable vertical MP4.
- Errors are surfaced with actionable messages.
