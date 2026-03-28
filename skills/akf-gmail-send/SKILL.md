---
name: akf-gmail-send
description: Send emails with AKF trust metadata on attachments — recipients know the provenance.
metadata:
  version: 1.0.0
  openclaw:
    category: compliance
    requires:
      bins:
        - gws
        - akf
---

# AKF Gmail Send

Stamp attachments with trust metadata before sending via Gmail.

## Usage

```bash
akf stamp report.docx --agent claude-code --evidence "quarterly data"
gws gmail +send --to team@company.com --subject "Q3 Report" --attach report.docx
```

Recipients download, run akf read report.docx, see full provenance.

## Install

```bash
pip install akf
```

https://akf.dev
