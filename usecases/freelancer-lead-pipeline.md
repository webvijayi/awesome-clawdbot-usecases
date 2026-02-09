# Freelancer Lead Pipeline

> Automate job discovery, lead qualification, proposal drafting, and follow-ups — so you can focus on actual client work.

---

## The Problem

Finding quality freelance gigs is a full-time job on top of your actual work. You spend hours scrolling Upwork, LinkedIn, and niche job boards, only to find most postings don't match your skills, budget, or timeline. By the time you craft a personalized proposal, the best opportunities are already flooded with applicants. Meanwhile, promising leads go cold because you forgot to follow up.

---

## The Solution

Clawdbot monitors job boards on your schedule, filters opportunities against your criteria, drafts personalized proposals using context from each posting, and tracks your entire pipeline in a simple markdown file. It sends you only qualified leads, reminds you to follow up, and can even help generate invoices when you close deals.

**What you get:**
- Morning digest of qualified leads matching your criteria
- Pre-drafted proposals ready to customize and send
- Automatic pipeline tracking with follow-up reminders
- No more missed opportunities or forgotten leads

---

## Setup Guide

### Step 1: Create Your Freelancer Profile (5 minutes)

Create `~/clawd/freelance/PROFILE.md`:

```markdown
# Freelancer Profile

## Identity
- **Name:** [Your Name]
- **Title:** Senior Full-Stack Developer
- **Specialties:** React, Node.js, Python, AWS
- **Experience:** 8 years

## Ideal Client Criteria
- **Budget minimum:** $50/hour or $2,000+ fixed projects
- **Project length:** 1 week to 3 months
- **Industries:** SaaS, fintech, healthtech, e-commerce
- **Red flags:** "equity only", "exposure", "quick test project", budget under $500

## Availability
- **Hours/week:** 20-30
- **Timezone:** EST (UTC-5)
- **Start date:** Can start within 1 week

## Portfolio Links
- GitHub: https://github.com/yourname
- Portfolio: https://yoursite.com
- LinkedIn: https://linkedin.com/in/yourname

## Proposal Style
- Tone: Professional but personable
- Length: 150-250 words
- Always include: Relevant experience, specific approach, timeline estimate
- Avoid: Generic templates, desperation, undercutting
```

### Step 2: Set Up Pipeline Tracking (3 minutes)

Create `~/clawd/freelance/PIPELINE.md`:

```markdown
# Lead Pipeline

## 🔥 Hot Leads (respond today)
<!-- Leads scored 8+/10, posted <24h ago -->

## 📋 Qualified Leads (respond this week)
<!-- Leads scored 6-7/10, good fit but not urgent -->

## ✉️ Proposals Sent
| Date | Client | Project | Amount | Status | Follow-up |
|------|--------|---------|--------|--------|-----------|

## 🤝 Active Projects
| Client | Project | Start | End | Rate | Invoiced |
|--------|---------|-------|-----|------|----------|

## ❌ Rejected/Passed
<!-- Quick notes on why, for pattern learning -->
```

### Step 3: Create Job Board URLs File (5 minutes)

Create `~/clawd/freelance/JOB_SOURCES.md`:

```markdown
# Job Sources to Monitor

## Upwork
- https://www.upwork.com/nx/find-work/best-matches
- https://www.upwork.com/nx/find-work/?q=react%20developer&sort=recency

## LinkedIn Jobs
- https://www.linkedin.com/jobs/search/?keywords=freelance%20developer&f_TPR=r86400

## We Work Remotely
- https://weworkremotely.com/categories/remote-programming-jobs

## Remote OK
- https://remoteok.com/remote-dev-jobs

## Toptal (if approved)
- https://www.toptal.com/developers/jobs

## Niche Boards (customize to your field)
- https://www.workingnomads.com/jobs?category=development
- https://nodesk.co/remote-jobs/engineering/

## Direct Outreach Targets
<!-- Companies you'd love to work with -->
- Company A - Check careers page monthly
- Company B - Follow their engineering blog
```

### Step 4: Create Proposal Templates (5 minutes)

Create `~/clawd/freelance/TEMPLATES.md`:

```markdown
# Proposal Templates

## Quick Web Dev Project
Hi [Name],

I read through your project requirements for [specific thing]. I've built similar [specific type] applications for [relevant client/industry], and I think I can deliver exactly what you need.

**My approach:**
1. [Specific first step based on their needs]
2. [Technical approach]
3. [Delivery/handoff plan]

I can start [timeframe] and estimate [X weeks] for completion. Happy to jump on a quick call to discuss the details.

[Your name]
[Portfolio link]

---

## Larger/Ongoing Project
[Similar structure with more detail on process, communication style, etc.]

---

## Agency/Startup
[Emphasize flexibility, startup experience, fast iteration]
```

### Step 5: Add to HEARTBEAT.md (2 minutes)

Add this section to your `~/clawd/HEARTBEAT.md`:

```markdown
## Freelance Pipeline Check
Every 4-6 hours during business hours:
1. Check `freelance/PIPELINE.md` for follow-ups due today
2. If any proposals sent >3 days ago without response, draft follow-up message
3. If any active projects approaching deadline, remind me

Morning only (first heartbeat after 8am):
1. Quick scan of JOB_SOURCES.md for new high-quality leads
2. Update HOT LEADS section of PIPELINE.md
```

---

## Skills Needed

| Skill | Purpose | Required? |
|-------|---------|-----------|
| **web_search** | Search job boards, company info | ✅ Yes |
| **web_fetch** | Read full job postings | ✅ Yes |
| **browser** | Navigate dynamic job sites (Upwork, LinkedIn) | ⚡ Recommended |
| **Files (read/write)** | Manage pipeline, proposals | ✅ Yes (built-in) |
| **Cron** | Scheduled job scanning | ⚡ Recommended |
| **TTS** | Audio lead summaries while commuting | Optional |

---

## Example Prompts

### 1. Morning Lead Discovery
```
Scan my job sources in freelance/JOB_SOURCES.md for new postings in the last 24 hours. 
Score each lead 1-10 based on my PROFILE.md criteria. 
For anything 7+, add to PIPELINE.md under Hot Leads with:
- Job title and client
- Budget/rate if listed
- Why it's a good fit
- Direct link to apply
```

### 2. Draft Personalized Proposal
```
Read this job posting: [paste URL or description]

Using my PROFILE.md and TEMPLATES.md, draft a personalized proposal that:
1. References something specific from their posting
2. Highlights my most relevant experience
3. Suggests a concrete next step
4. Stays under 200 words

Also suggest what rate/budget to propose based on their signals.
```

### 3. Pipeline Status Check
```
Review my freelance/PIPELINE.md and give me a quick status:
- How many hot leads need responses today?
- Any proposals sent over 3 days ago needing follow-up?
- Any active project milestones coming up this week?

Draft any follow-up messages needed.
```

### 4. Weekly Pipeline Review
```
Analyze my freelance pipeline for the past week:
1. How many leads did I review vs respond to?
2. What's my proposal-to-response rate?
3. Any patterns in what's working or not?
4. Update PIPELINE.md with any leads that should move to Rejected

Suggest 2-3 improvements for next week.
```

### 5. Generate Invoice
```
Create an invoice for [Client Name]:
- Project: [Project description]
- Hours: [X] at $[Y]/hour OR Fixed: $[Amount]
- Due: Net 15

Use my details from PROFILE.md. Format as markdown I can copy into my invoicing tool, 
or generate a simple HTML invoice I can PDF.
```

---

## Cron Schedule

Add these to your Clawdbot cron jobs:

```bash
# Morning lead scan - Monday to Friday at 8:00 AM
0 8 * * 1-5 | freelance-morning | Scan job sources, score and add hot leads to pipeline

# Midday quick check - Weekdays at 1:00 PM  
0 13 * * 1-5 | freelance-midday | Check for urgent leads posted this morning

# Evening proposal reminder - Weekdays at 5:00 PM
0 17 * * 1-5 | freelance-followup | Review sent proposals, draft follow-ups for stale ones

# Weekly pipeline review - Sunday at 7:00 PM
0 19 * * 0 | freelance-weekly | Analyze week's pipeline, clean up old leads, identify patterns
```

### How to Add Cron Jobs

```bash
# List current jobs
clawdbot cron list

# Add morning scan
clawdbot cron add "0 8 * * 1-5" "Scan freelance/JOB_SOURCES.md for leads posted in last 24h. Score against PROFILE.md. Add 7+ scored leads to PIPELINE.md Hot Leads section. Send me a summary of top 3 opportunities."

# Add follow-up reminder
clawdbot cron add "0 17 * * 1-5" "Check freelance/PIPELINE.md Proposals Sent table. For any sent 3+ days ago with status 'waiting', draft a polite follow-up message. Notify me with the drafts."
```

---

## HEARTBEAT.md Config

Add this block to your `HEARTBEAT.md`:

```markdown
## 💼 Freelance Pipeline

### Every Heartbeat (if during business hours 8am-6pm)
- [ ] Check `freelance/PIPELINE.md` for follow-ups due today
- [ ] If I mentioned sending a proposal in recent messages, add it to PIPELINE.md

### Morning Heartbeat Only (first one after 8am)
- [ ] Quick web search for "[your specialty] freelance jobs" posted today
- [ ] Check top 2-3 sources from JOB_SOURCES.md
- [ ] If any high-quality leads found, send me a brief summary

### State Tracking
Track in `memory/freelance-state.json`:
```json
{
  "lastLeadScan": "2024-01-15T08:00:00Z",
  "pendingFollowUps": ["client-a", "client-b"],
  "proposalsSentThisWeek": 5,
  "leadsReviewedToday": 12
}
```

### Notification Rules
- 🔥 Immediate: Lead with budget >$10k matching my exact skills
- 📬 Morning digest: All qualified leads from overnight
- ⏰ Afternoon: Follow-up reminders for proposals >3 days old
- 🔕 Don't notify: Leads under $500, obvious poor fits
```

---

## Expected Results

### Week 1
- **15-25 qualified leads** automatically discovered and scored
- **5-8 personalized proposals** drafted and ready to customize
- **Zero missed opportunities** from popular boards
- **30-60 minutes saved daily** on manual job hunting

### Month 1
- **Clear visibility** into your entire pipeline
- **Higher response rates** from personalized, timely proposals
- **Pattern recognition** - you'll see which job types convert best
- **Consistent follow-up** without mental overhead

### Ongoing Benefits
- **Never miss a hot lead** - Clawdbot scans while you sleep
- **Faster proposal turnaround** - drafts ready when you wake up
- **Data-driven decisions** - track what's working over time
- **More time for actual work** - less time hunting for it

---

## Pro Tips

### 1. Qualify Aggressively
Tell Clawdbot your hard filters upfront. Better to miss a few edge cases than drown in noise.

### 2. Customize the Drafts
Clawdbot's proposals are starting points. Always add 1-2 sentences that prove you actually read their posting.

### 3. Track Your Wins
When you land a client, note which source and what made your proposal stand out. Feed this back into your templates.

### 4. Seasonal Adjustments
Update PROFILE.md when your availability or rates change. Lower your minimums during slow periods if needed.

### 5. Browser Automation for Gated Sites
For sites like Upwork that require login, use the browser skill with your authenticated session:
```
Open my Upwork best matches page using the browser skill. 
Scan for new jobs posted in the last 6 hours matching my profile.
```

---

## Quick Start Checklist

- [ ] Create `freelance/PROFILE.md` with your criteria
- [ ] Create `freelance/PIPELINE.md` for tracking
- [ ] Create `freelance/JOB_SOURCES.md` with your target boards
- [ ] Create `freelance/TEMPLATES.md` with proposal starters
- [ ] Add freelance section to `HEARTBEAT.md`
- [ ] Set up morning cron job for lead scanning
- [ ] Test with: "Scan my job sources and find 3 leads that match my profile"

**Total setup time: ~30 minutes**

---

*Last updated: 2024*
