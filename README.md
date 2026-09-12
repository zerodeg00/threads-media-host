# threads-media-host

Shared **temporary public media host** for Threads API posts.

Threads Graph API needs a public HTTPS URL so Meta can fetch images/videos (`image_url` / `video_url`). This repo is that bucket for Grok Bot–managed accounts (tipstack, coco, qbter_lab, …) — not tipstack-only.

## How to use

1. Put media under a dated folder, e.g. `YYYY-MM-DD-<slug>/still_1x1.jpg`, `motion_5s.mp4`.
2. Commit + push to `main`.
3. Serve via jsDelivr (pin a commit SHA when possible):

```text
https://cdn.jsdelivr.net/gh/zerodeg00/threads-media-host@<commit>/<path>
```

4. After Meta has processed the post, old files can be deleted in a later cleanup — do not treat this as permanent CDN storage.

## Rules

- Public by necessity (Threads fetch). Prefer unguessable dated paths; do not put secrets here.
- Prefer official product CDNs (e.g. Coupang) for product shots when available; use this repo for motion clips / social stills that need a fetchable URL.
- Keep files small (Threads-friendly). Prefer true 1:1 stills and short ~5s mp4 (h264, yuv420p, faststart).
- Do not commit tokens, `.env`, or private keys.

## Accounts

Any of Youngdo’s Threads bots may upload here. Folder prefix by account/date to avoid collisions:

- `tipstack/…` or `YYYY-MM-DD-tipstack-…`
- `coco/…`
- `qbter/…`

## Cleanup

Safe to prune old media after posts are live. Renamed from `tipstack-threads-media` (GitHub redirects the old name).
