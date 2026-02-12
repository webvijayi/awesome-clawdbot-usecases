# 📄 Document Processor

> PDFs, contracts, reports—instantly searchable and summarized.

---

## The Problem

Documents pile up: contracts, reports, receipts, research papers. Finding information means opening dozens of files. Important details get lost. Nobody reads 50-page reports cover to cover.

---

## The Solution

OpenClaw extracts text from any document, summarizes key points, makes everything searchable, and answers questions about your documents instantly.

---

## Setup Guide

### Step 1: Install Document Skills

```bash
openclaw skill install mineru-pdf
openclaw skill install pymupdf-pdf
openclaw skill install llmwhisperer
openclaw skill install excel
```

### Step 2: Set Up Document Folders

Create `~/openclaw/documents/config.json`:

```json
{
  "watchFolders": [
    "~/Documents/Contracts/",
    "~/Documents/Reports/",
    "~/Downloads/*.pdf"
  ],
  "outputDir": "~/openclaw/documents/processed/",
  "autoProcess": true
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `mineru-pdf` | Advanced PDF extraction |
| `pymupdf-pdf` | Fast PDF processing |
| `llmwhisperer` | Handwriting/complex docs |
| `excel` | Spreadsheet processing |

---

## Example Prompts

**Process document:**
```
Process this contract [file]. Extract key terms, dates, and obligations.
```

**Search documents:**
```
Find all documents that mention [term] from the past year.
```

**Summarize report:**
```
Summarize this 40-page report. What are the key findings and recommendations?
```

**Compare documents:**
```
Compare these two contract versions. What changed?
```

---

## Cron Schedule

```
*/30 * * * *   # Every 30 min - process new documents
0 9 * * 1      # Monday 9 AM - document digest
```

---

## Expected Results

- All documents searchable
- 90% faster information retrieval
- Never lose important details again
