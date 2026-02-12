# 🔍 SEO Content Pipeline

> Rank higher with less effort. Data-driven content that Google loves.

---

## The Problem

Creating SEO content is time-consuming: keyword research, competitor analysis, outline creation, writing, optimization. Most content either ignores SEO (no traffic) or over-optimizes (robotic reading). Finding the balance takes expertise and hours.

---

## The Solution

Clawdbot handles the entire SEO content workflow: finds keyword opportunities, analyzes what's ranking, creates optimized outlines, and helps you write content that ranks AND reads well.

---

## Setup Guide

### Step 1: Install SEO Skills

```bash
clawdbot skill install gsc  # Google Search Console
clawdbot skill install brave-search
clawdbot skill install web-fetch
```

### Step 2: Configure Your Site

Create `~/clawd/seo/site-config.json`:

```json
{
  "domain": "yourdomain.com",
  "gscPropertyId": "sc-domain:yourdomain.com",
  "targetKeywords": ["main topic", "secondary topic"],
  "competitors": ["competitor1.com", "competitor2.com"],
  "contentGoals": {
    "monthlyPosts": 8,
    "targetWordCount": "1500-2500"
  }
}
```

### Step 3: Create Content Brief Template

Create `~/clawd/seo/brief-template.md`:

```markdown
# Content Brief: {keyword}

## Keyword Data
- Search volume:
- Difficulty:
- Current ranking:

## Top 5 Ranking Pages
1. [URL] - Word count, key points
2. ...

## Content Gaps
- Topics competitors miss:
- Questions not answered:

## Recommended Outline
1. H2:
   - H3:
2. ...

## Optimization Checklist
- [ ] Keyword in title
- [ ] Keyword in first 100 words
- [ ] Related keywords included
- [ ] Internal links
- [ ] External authoritative links
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `gsc` | Google Search Console data |
| `brave-search` | SERP analysis |
| `web-fetch` | Competitor content analysis |

---

## Example Prompts

**Keyword research:**
```
Find 10 keyword opportunities for [topic]. Look for low competition, decent volume, and topics I can write authoritatively about.
```

**Content brief:**
```
Create a content brief for the keyword "[keyword]". Analyze top 5 ranking pages and find gaps I can fill.
```

**Outline review:**
```
Here's my outline for [topic]. Is it comprehensive enough to outrank the current top results?
```

**Post-publish optimization:**
```
My post on [topic] has been live for a month. Check GSC for impressions without clicks - what queries should I better optimize for?
```

---

## Cron Schedule

```
0 8 * * 1      # Monday 8 AM - weekly content planning
0 9 * * *      # Daily - check GSC for quick wins
0 10 * * 5     # Friday - performance review
```

---

## Expected Results

**Month 1:**
- Content calendar with keyword-targeted posts
- 50% reduction in research time per post

**Month 3:**
- New posts ranking within 4-6 weeks
- 30%+ increase in organic traffic

**Month 6:**
- Consistent content production
- Clear ROI from SEO efforts
