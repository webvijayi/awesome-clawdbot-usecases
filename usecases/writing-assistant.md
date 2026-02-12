# ✍️ Writing Assistant

> From blank page to published post. Your personal editor that never sleeps.

---

## The Problem

Writing quality blog content is exhausting: research, drafting, editing, SEO optimization, formatting, publishing. Most writers either spend 8+ hours per post or publish half-baked content. The editing loop alone kills momentum—you're too close to your own words to see what's wrong.

---

## The Solution

Clawdbot becomes your writing partner: helps research topics, generates first drafts, edits for clarity and style, optimizes for SEO, and handles the publishing workflow. You provide the ideas and voice; Clawdbot handles the heavy lifting.

---

## Setup Guide

### Step 1: Install Writing Skills

```bash
clawdbot skill install gsc           # Google Search Console
clawdbot skill install brave-search  # Research & SERP analysis
clawdbot skill install web-fetch     # Reference gathering
clawdbot skill install ghost         # Blog publishing (if using Ghost)
```

### Step 2: Create Writing Workspace

```bash
mkdir -p ~/clawd/writing/{drafts,published,research}
```

Create `~/clawd/writing/style-guide.md`:

```markdown
# My Writing Style Guide

## Voice
- Conversational but authoritative
- Use contractions (it's, you'll, don't)
- Second person ("you") to speak directly to reader

## Structure
- Short paragraphs (3-4 sentences max)
- Use subheadings every 200-300 words
- Include actionable takeaways

## Avoid
- Passive voice
- Jargon without explanation
- Walls of text

## SEO Requirements
- Target keyword in title
- Keyword in first 100 words
- Include 3-5 internal links
```

### Step 3: Set Up Blog Config

Create `~/clawd/writing/blog-config.json`:

```json
{
  "platform": "ghost",
  "siteUrl": "https://yourblog.com",
  "author": "Your Name",
  "defaultCategory": "Tech",
  "wordCountTarget": "1500-2500",
  "publishDays": ["Tuesday", "Thursday"],
  "seoKeywords": ["main topic", "related topic"]
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `gsc` | Track keyword rankings and opportunities |
| `brave-search` | Research topics and analyze competition |
| `web-fetch` | Pull reference content and citations |
| `ghost` / `wordpress` | Direct blog publishing |
| `grammarly-api` | Grammar and style checking (optional) |

---

## Example Prompts

**Topic research:**
```
I want to write about [topic]. Research the top 10 ranking articles, identify gaps in their coverage, and suggest 5 unique angles I could take.
```

**Draft generation:**
```
Create a first draft for a blog post about [topic]. Target keyword: [keyword]. Follow my style guide in ~/clawd/writing/style-guide.md. Aim for 1800 words.
```

**Editing pass:**
```
Edit this draft for clarity and flow. Remove fluff, strengthen weak sentences, and ensure it matches my voice. Be ruthless—cut anything that doesn't add value.
```

**SEO optimization:**
```
Optimize this post for SEO. Check keyword density, suggest meta description, add internal link opportunities, and ensure headers are properly structured.
```

**Publishing workflow:**
```
This post is ready. Format it for Ghost, generate a featured image prompt, create social media snippets for Twitter and LinkedIn, and schedule for Tuesday 9 AM.
```

---

## Workflow Stages

```
1. RESEARCH    → Clawdbot gathers data, finds angles
2. OUTLINE     → You approve structure
3. DRAFT       → Clawdbot writes first draft
4. EDIT        → Multiple passes for clarity
5. SEO         → Keyword optimization
6. PUBLISH     → Format, schedule, promote
```

---

## Cron Schedule

```
0 9 * * 1      # Monday 9 AM - plan week's content
0 10 * * 3     # Wednesday - editing review
0 8 * * 2,4    # Publish days - final checks
0 14 * * 5     # Friday - performance review
```

---

## Expected Results

**Week 1:**
- 2-3 blog posts drafted vs. usual 1
- Editing time cut by 60%

**Month 1:**
- Consistent publishing schedule
- Higher quality through systematic editing
- SEO improvements visible in GSC

**Month 3:**
- Writing workflow on autopilot
- 10+ hours/week saved
- Measurable traffic growth from SEO
