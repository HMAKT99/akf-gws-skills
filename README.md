# AKF Skills for Google Workspace CLI

Trust metadata for every file that flows through Google Workspace.

When AI agents use `gws` to upload files to Drive, send Gmail attachments, or write Docs — AKF stamps them with trust scores, source provenance, and compliance metadata first.

## Skills

| Skill | What it does |
|-------|-------------|
| `akf-drive-upload` | Stamp files before uploading to Google Drive |
| `akf-gmail-send` | Stamp attachments before sending via Gmail |

## Install

```bash
pip install akf
npx skills add https://github.com/HMAKT99/akf-gws-skills
```

## Why

- EU AI Act Article 50 (Aug 2, 2026) — AI content must carry transparency metadata
- Every file in your Google Workspace should have provenance
- Trust metadata embeds into the file — survives upload, download, email, format conversion

## Links

- [AKF — The AI Native File Format](https://akf.dev)
- [Google Workspace CLI](https://github.com/googleworkspace/cli)
