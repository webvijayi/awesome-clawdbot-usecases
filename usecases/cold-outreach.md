# ✉️ Cold Outreach Automation

> Personalized at scale. Not spray-and-pray, but thoughtful outreach multiplied.

---

## The Problem

Cold outreach works when it's personal. But personalization doesn't scale—researching each prospect takes 15 minutes. So you either send generic emails (ignored) or limit your outreach (slow growth).

---

## The Solution

OpenClaw researches prospects automatically, finds personalization hooks, generates custom messages, and manages follow-up sequences. You review and send—personal touch at scale.

---

## Setup Guide

### Step 1: Install Outreach Skills

```bash
openclaw skill install apollo
openclaw skill install linkedin
openclaw skill install gmail
openclaw skill install web-fetch
```

### Step 2: Define Ideal Customer Profile

Create `~/openclaw/outreach/icp.md`:

```markdown
# Ideal Customer Profile

## Company
- Size: 50-500 employees
- Industry: SaaS, Tech, E-commerce
- Growth stage: Series A-C
- Tech stack: Uses [relevant tools]

## Persona
- Title: VP/Director of [department]
- Responsibility: [specific area]
- Pain points: [list]

## Disqualifiers
- Less than 10 employees
- Non-English speaking
- Already using competitor
```

### Step 3: Create Message Templates

Create `~/openclaw/outreach/templates.md`:

```markdown
# Outreach Templates

## First Touch
Subject: {personalization_hook}

Hi {first_name},

{personalized_opener_based_on_research}

[Value prop in 1 sentence]

Would it make sense to chat for 15 minutes?

## Follow-up 1 (Day 3)
Subject: Re: {original_subject}

{name}, wanted to bump this up...

## Follow-up 2 (Day 7)
Subject: Quick question, {name}

Different angle/value prop...

## Break-up (Day 14)
Subject: Should I close your file?

Last attempt, remove friction...
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `apollo` | Prospect research |
| `linkedin` | Profile insights |
| `gmail` | Email sending |
| `web-fetch` | Company research |

---

## Example Prompts

**Research prospect:**
```
Research [person] at [company]. Find personalization hooks: recent news, common connections, content they've shared.
```

**Generate sequence:**
```
Create a 4-email sequence for [persona] at [company type]. Focus on [pain point].
```

**Review and send:**
```
Show me today's outreach queue with draft messages. Let me approve or edit before sending.
```

**Optimize:**
```
Which subject lines and openers got the best response rates? Update my templates.
```

---

## Cron Schedule

```
0 7 * * 1-5    # 7 AM weekdays - prepare daily outreach
0 9 * * 1-5    # 9 AM - send first touch emails
0 14 * * 1-5   # 2 PM - send follow-ups
0 10 * * 1     # Monday - weekly metrics review
```

---

## Expected Results

**Week 1:**
- 5x outreach volume with same effort
- Personalized messages for every prospect

**Month 1:**
- Higher response rates than generic outreach
- Clear data on what messaging works

**Month 3:**
- Predictable meeting pipeline
- Continuously optimized messaging
- Scalable prospecting machine
