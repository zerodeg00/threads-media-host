# threads-media-host

Shared **temporary public media host** for Threads Graph API publishing.

The Threads API needs a public HTTPS URL so Meta can fetch images/videos (`image_url` / `video_url`). This repository is a shared drop bucket for that purpose — not a permanent CDN and not tied to a single account.

## How to use

1. Upload media under a dated path, e.g. `YYYY-MM-DD-<slug>/still_1x1.jpg`, `motion_5s.mp4`.
2. Commit and push to `main`.
3. Serve via jsDelivr (pin a commit SHA when possible):

```text
https://cdn.jsdelivr.net/gh/zerodeg00/threads-media-host@<commit>/<path>
```

4. After Meta has finished processing the post, older files can be deleted in a later cleanup.

## Rules

- Public by necessity (Threads fetch). Prefer unguessable dated paths. Never commit secrets, tokens, or `.env` files.
- Prefer official product CDNs when a usable official cut exists; use this repo for motion clips / stills that need a fetchable URL.
- Keep files Threads-friendly: true 1:1 stills when possible; short ~5s mp4 (h264, yuv420p, `+faststart`).
- Do not document private account handles, emails, or bot names in this repo.

## Layout

Use account-agnostic folders so uploads do not collide:

- `YYYY-MM-DD-<slug>/…`
- or a short opaque prefix + date

## Cleanup

Safe to prune old media after posts are live. Older clone URLs may redirect here after a rename.
