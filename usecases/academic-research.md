# 📚 Academic Research Assistant

> From literature search to paper draft. Research without the busywork.

---

## The Problem

Academic research is 80% tedious work: finding papers, managing citations, reading dense PDFs, tracking who cited whom. By the time you've organized everything, you've lost momentum on actual thinking. Citation management tools help but don't understand your research questions.

---

## The Solution

OpenClaw becomes your research assistant: searches academic databases, summarizes papers, manages citations, identifies research gaps, and helps you synthesize findings into coherent arguments.

---

## Setup Guide

### Step 1: Install Research Skills

```bash
openclaw skill install arxiv
openclaw skill install literature-review
openclaw skill install semantic-scholar
openclaw skill install pdf-extractor
openclaw skill install brave-search
```

### Step 2: Define Research Focus

Create `~/openclaw/research/focus.md`:

```markdown
# Research Focus

## Current Project
**Topic:** Transformer architectures for time series forecasting
**Question:** How do attention mechanisms compare to RNNs for irregular time series?
**Keywords:** transformers, attention, time series, forecasting, irregular sampling

## Background
- Started: 2024-01
- Advisor: Prof. Smith
- Related work: Informer, Autoformer, PatchTST

## Citation Style
APA 7th Edition

## Key Authors to Track
- Vaswani et al. (attention)
- Zhou et al. (Informer)
- Wu et al. (Autoformer)
```

### Step 3: Set Up Paper Library

Create `~/openclaw/research/papers/` directory structure:

```
papers/
├── to-read/
├── reading/
├── completed/
├── summaries/
└── citations.bib
```

### Step 4: Configure Paper Tracking

Create `~/openclaw/research/reading-list.md`:

```markdown
# Reading List

## Priority (this week)
- [ ] "Attention Is All You Need" - Foundation paper
- [ ] "Informer" - Efficient transformers for long sequences

## Queue
- [ ] "PatchTST" - Patching approach
- [ ] "Autoformer" - Auto-correlation

## Completed (with summaries)
- [x] "LSTM Survey" → summaries/lstm-survey.md
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `arxiv` | Search and download papers |
| `literature-review` | Systematic review automation |
| `semantic-scholar` | Citation graphs, related papers |
| `pdf-extractor` | Extract text from PDFs |
| `brave-search` | Web search for grey literature |

---

## Example Prompts

**Literature search:**
```
Find the 10 most cited papers on [topic] from the last 3 years. Summarize each in 2-3 sentences.
```

**Paper summarization:**
```
Read this paper and give me: (1) main contribution, (2) methodology, (3) key results, (4) limitations, (5) how it relates to my research.
```

**Citation management:**
```
Add this paper to my citations.bib in BibTeX format. Check if I already have it.
```

**Research gap analysis:**
```
Based on the papers I've read, what gaps exist in the literature? What hasn't been tried?
```

**Writing support:**
```
Help me write the related work section. Group papers by theme and show how they connect to my contribution.
```

**Citation check:**
```
Find who cited [paper] in 2023-2024. Any of them relevant to my research question?
```

---

## Cron Schedule

```
0 9 * * 1      # Monday 9 AM - new papers on arXiv for keywords
0 14 * * 3     # Wednesday 2 PM - citation alerts for key papers  
0 10 1 * *     # 1st of month - literature review update
```

---

## HEARTBEAT.md Config

```markdown
## Research Monitoring
- [ ] New arXiv papers matching keywords?
- [ ] New citations for key papers I'm tracking?
- [ ] Reading list progress check
```

---

## Expected Results

**Week 1:**
- Comprehensive literature map
- 20+ relevant papers identified and organized
- Clear understanding of research landscape

**Month 1:**
- All key papers read and summarized
- Research gaps clearly identified
- Related work section drafted

**Month 3:**
- Citation network deeply understood
- Novel contribution positioned clearly
- Paper draft with solid literature grounding
