# Security, Copyright, and Content Handling

## Media authorization
Only ingest gameplay footage that the user owns or is authorized to process. Do not support leaked or unauthorized GTA VI footage. The project does not grant rights to game assets, music, logos, or third-party content.

## Platform and publisher rules
Before publishing, the creator must review the relevant game publisher policies, platform terms, music rights, and monetization rules. ClutchVerse cannot guarantee that any output is copyright-free, monetizable, or immune from claims.

## URL ingestion
If optional `yt-dlp` support is added, use it only for sources the user is permitted to download and where the platform's terms allow it. Do not implement DRM circumvention, login bypass, or access-control evasion. Local-file ingestion should remain the default.

## Secrets
- Store API keys in environment variables.
- Add `.env` to `.gitignore`.
- Never paste secrets into GitHub issues or screenshots.
- Rotate a key immediately if it is exposed.

## File safety
- Restrict accepted media types and maximum file size.
- Generate safe internal filenames rather than trusting uploaded names.
- Avoid shell-string interpolation; pass FFmpeg arguments as an argument list.
- Apply timeouts and check exit codes.
- Do not expose arbitrary filesystem paths through the UI.

## Privacy
Prefer local processing. Clearly disclose when audio, transcripts, or clip context is sent to a third-party AI service. Do not transmit private recordings without user consent.
