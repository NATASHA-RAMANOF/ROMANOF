# Emoji Studio v0.4 — Animation development plan

Status: planning only. No animation backend or export has been deployed.

## Isolation and release
- Work exclusively on branch `feature/emoji-studio-animation-v04`, forked from `feature/emoji-studio-preview`.
- Keep existing PNG ZIP exporter unchanged until regression tests pass.
- Do not modify `main`, production Netlify, Telegram bot token/webhook, Cloudflare Workers, or databases.
- The existing Netlify preview is configured to deploy `feature/emoji-studio-preview`, not this v0.4 branch.

## Target outputs
- Seamless 3-second looping animations at 30 fps (90 frames).
- Each tile exactly 100x100 pixels; 2–9 horizontally contiguous tiles.
- Transparent background with alpha.
- Separate WEBM VP9 files for Telegram; APNG and PNG/ZIP for inspection.
- Optional target of <=256 KiB per WEBM tile; check real encodes rather than promising this unconditionally.

## Architecture
1. Browser editor remains on Netlify; preview is client-side.
2. Render backend runs separately on a suitable host with Python/Pillow and FFmpeg with VP9 alpha support.
3. API accepts validated text, tile count, theme and effect only; rate-limit and authenticate requests before public access.
4. Backend renders one consistent 100*N x 100 sequence, then crops each frame into tile sequences so edges remain continuous.
5. Encode alpha-capable VP9 WEBM with `yuva420p`, and validate decoded alpha and loop duration with ffprobe and image inspection.
6. Generate APNG and PNG; package ZIP with manifest, filenames and validation summary.
7. Never put backend API keys or Telegram bot tokens in frontend JavaScript or GitHub.

## Acceptance tests
- Thai tone marks and Kanit font render without clipping.
- All 90 frames and each 100x100 tile align.
- WEBM plays with transparency in Telegram test context; verify actual alpha support.
- 3-second duration, 30 fps, acceptable file size.
- PNG ZIP export still works on Android.
- Errors show useful messages; backend timeouts and invalid inputs fail safely.

## Release gates
- No automatic promotion or merge.
- No bot integration until user approves a separate explicit step.
- Deploy v0.4 only to a distinct test environment after backend and security checks.
