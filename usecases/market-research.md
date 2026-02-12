# 📊 Market Research Intelligence

> Know your market before your competitors do. Data-driven decisions, not guesswork.

---

## The Problem

Market research is expensive and time-consuming. By the time you've gathered data, analyzed trends, and compiled reports, the market has moved. Consultants charge thousands for reports that are already outdated. You need real-time intelligence, not quarterly PDFs.

---

## The Solution

Clawdbot continuously monitors your market: tracks competitors, identifies emerging trends, analyzes customer sentiment, and generates actionable intelligence reports on demand.

---

## Setup Guide

### Step 1: Install Market Research Skills

```bash
clawdbot skill install brave-search
clawdbot skill install reddit
clawdbot skill install twitter-api
clawdbot skill install crunchbase
clawdbot skill install hn-digest
clawdbot skill install miniflux
```

### Step 2: Define Your Market

Create `~/clawd/market-research/market.md`:

```markdown
# Market Definition

## Our Space
**Industry:** Developer Tools / DevOps
**Segment:** CI/CD and deployment automation
**Geography:** Global (focus: US, EU)

## Our Product
**Name:** DeployBot Pro
**Category:** Continuous deployment platform
**Target:** Mid-market engineering teams (20-200 devs)

## Key Differentiators
- One-click rollbacks
- Built-in feature flags
- SOC2 compliant out of box
```

### Step 3: Track Competitors

Create `~/clawd/market-research/competitors.json`:

```json
{
  "direct": [
    {
      "name": "Vercel",
      "website": "vercel.com",
      "twitter": "@vercel",
      "pricing": "https://vercel.com/pricing"
    },
    {
      "name": "Railway",
      "website": "railway.app",
      "twitter": "@Railway",
      "subreddit": "r/railway"
    },
    {
      "name": "Render",
      "website": "render.com",
      "twitter": "@render"
    }
  ],
  "indirect": [
    "AWS Amplify",
    "Netlify",
    "Fly.io"
  ]
}
```

### Step 4: Set Up Trend Tracking

Create `~/clawd/market-research/trends.md`:

```markdown
# Trend Tracking

## Keywords to Monitor
- "deployment automation"
- "GitOps"
- "platform engineering"
- "developer experience" OR "DevEx"
- "internal developer platform"

## Sources
- Hacker News (comments mentioning competitors)
- r/devops, r/kubernetes, r/webdev
- Tech Twitter influencers
- ThoughtWorks Tech Radar
- Gartner reports
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `brave-search` | Web intelligence gathering |
| `reddit` | Community sentiment analysis |
| `twitter-api` | Social listening |
| `crunchbase` | Funding and company data |
| `hn-digest` | Developer sentiment |
| `miniflux` | RSS monitoring |

---

## Example Prompts

**Competitive analysis:**
```
What did [competitor] ship this month? Any pricing changes, new features, or messaging shifts?
```

**Trend detection:**
```
What are developers complaining about with current deployment tools? What pain points keep coming up?
```

**Market sizing:**
```
How big is the CI/CD market? What's the growth rate? Who are the leaders by market share?
```

**Sentiment analysis:**
```
Analyze Reddit and HN discussions about [competitor]. What do people love? What do they hate?
```

**Funding watch:**
```
Any funding rounds in our space this month? Who's raising and at what valuation?
```

**Report generation:**
```
Generate a competitive intelligence report for the executive team. Focus on threats and opportunities.
```

---

## Cron Schedule

```
0 8 * * 1-5    # 8 AM weekdays - competitor news scan
0 10 * * 1     # Monday 10 AM - weekly market summary
0 9 1 * *      # 1st of month - full market report
0 14 * * 3     # Wednesday 2 PM - trend analysis
```

---

## HEARTBEAT.md Config

```markdown
## Market Intelligence
- [ ] Competitor news in last 24h?
- [ ] Trending discussions about our space?
- [ ] New funding announcements?
- [ ] Pricing page changes (competitors)?
```

---

## Report Templates

### Weekly Brief (Monday)
```markdown
# Market Intelligence Brief - Week of [DATE]

## Competitor Moves
- [Summary of significant competitor activities]

## Market Signals
- [Trending topics, sentiment shifts]

## Opportunities
- [Gaps identified, potential positioning]

## Threats
- [New entrants, feature parity risks]
```

---

## Expected Results

**Week 1:**
- Complete competitor landscape mapped
- Monitoring infrastructure in place
- First intelligence brief delivered

**Month 1:**
- Pattern recognition kicks in
- Early warning on competitor moves
- Data-backed positioning insights

**Month 3:**
- Predictive insights emerging
- Feature roadmap informed by market gaps
- Competitive advantage from information edge
