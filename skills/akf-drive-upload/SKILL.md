---
name: akf-drive-upload
description: "Upload files to Google Drive with AKF trust metadata — provenance and compliance baked in before upload."
metadata:
  version: 1.0.0
  openclaw:
    category: "compliance"
    requires:
      bins:
        - gws
        - akf
    cliHelp: "akf stamp --help && gws drive +upload --help"
---

# AKF Drive Upload

> Stamp files with trust metadata BEFORE uploading to Google Drive. Every file in Drive carries provenance.

## Why

When AI agents upload files to Google Drive, those files carry zero provenance. Your team opens them with no idea: Was this AI-generated? What model? What sources? Is it compliant?

AKF stamps every file before upload so trust metadata travels with the document — visible in Google Drive file properties.

EU AI Act Article 50 (August 2, 2026) requires this for AI-generated content.

## Usage

### Step 1: Stamp the file

```bash
akf stamp report.pdf --agent claude-code --evidence "quarterly analysis from SEC filings"
```

### Step 2: Upload to Drive

```bash
gws drive +upload report.pdf
```

The trust metadata is embedded IN the file — it survives the upload and is readable by anyone who downloads it.

### One-liner

```bash
akf stamp report.pdf --agent claude-code --evidence "generated from Q3 data" && gws drive +upload report.pdf
```

### Verify after download

```bash
gws drive files get FILE_ID --download ./downloaded.pdf
akf read ./downloaded.pdf
# Shows: agent=claude-code, trust=0.70, evidence="generated from Q3 data"
```

## Compliance Check Before Upload

```bash
akf audit report.pdf --regulation eu_ai_act && gws drive +upload report.pdf
```

Only uploads if the file passes EU AI Act compliance.

## Bulk Stamp + Upload

```bash
for f in reports/*.pdf; do
  akf stamp "$f" --agent batch-upload --evidence "monthly reports"
done
gws drive +upload reports/ --parent FOLDER_ID
```

## Install

```bash
pip install akf        # Trust metadata
npm i -g @anthropic/gws  # Google Workspace CLI (or your preferred install method)
```

## See Also

- [AKF — The AI Native File Format](https://akf.dev)
- [gws-drive-upload](https://github.com/googleworkspace/cli/tree/main/skills/gws-drive-upload)
- [EU AI Act Article 50](https://akf.dev/#compliance)
