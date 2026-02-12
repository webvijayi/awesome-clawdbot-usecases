# Competitor Radar 🎯

> Automated competitive intelligence that keeps you one step ahead

## The Problem

You're building a product but have no idea what competitors are doing until customers tell you they switched. Manually checking competitor websites, blogs, and social media is a time sink that falls off your radar within a week. By the time you notice a competitor launched a killer feature or slashed prices, you've already lost deals.

## The Solution

OpenClaw becomes your always-on competitive intelligence analyst. It monitors competitor websites for pricing changes, scans their blogs for product announcements, tracks their social media activity, and delivers a weekly digest with strategic recommendations. When something big happens (major price drop, new feature launch), you get an instant alert.

---

## Setup Guide

### Step 1: Create Your Competitor Config File

Create `competitors.json` in your OpenClaw workspace:

```bash
mkdir -p ~/openclaw/competitor-radar
```

```json
// ~/openclaw/competitor-radar/competitors.json
{
  "competitors": [
    {
      "name": "Acme Corp",
      "website": "https://acme.com",
      "pricing_page": "https://acme.com/pricing",
      "blog": "https://acme.com/blog",
      "twitter": "acmecorp",
      "linkedin": "company/acme-corp"
    },
    {
      "name": "BigCo",
      "website": "https://bigco.io",
      "pricing_page": "https://bigco.io/pricing",
      "blog": "https://bigco.io/resources/blog",
      "twitter": "bigco_io"
    },
    {
      "name": "StartupX",
      "website": "https://startupx.com",
      "pricing_page": "https://startupx.com/plans",
      "changelog": "https://startupx.com/changelog",
      "twitter": "startupx"
    }
  ],
  "your_product": "MyAwesomeApp",
  "alert_keywords": ["enterprise", "price cut", "free tier", "AI", "integration"]
}
```

### Step 2: Create Tracking Files

```bash
# Initialize tracking files
touch ~/openclaw/competitor-radar/pricing-history.md
touch ~/openclaw/competitor-radar/feature-log.md
touch ~/openclaw/competitor-radar/weekly-digest.md
```

### Step 3: Set Up the Cron Jobs

Run these commands to schedule your competitor monitoring:

```bash
# Weekly comprehensive scan (Sunday 8 PM)
openclaw cron add "0 20 * * 0" "Run the weekly competitor radar scan. Check all competitors in ~/openclaw/competitor-radar/competitors.json. For each: fetch pricing page (compare to pricing-history.md), scan blog for new posts, search for recent news. Generate weekly-digest.md with findings and strategic recommendations. Alert me immediately if any competitor dropped prices >15% or announced a major feature."

# Daily quick scan for urgent changes (8 AM)
openclaw cron add "0 8 * * 1-5" "Quick competitor check: Fetch pricing pages for all competitors in competitors.json. Compare to last known prices in pricing-history.md. If ANY price changed, alert me immediately with details. Update pricing-history.md."

# Mid-week blog/news scan (Wednesday 2 PM)
openclaw cron add "0 14 * * 3" "Scan competitor blogs and search for recent news about competitors listed in competitors.json. Log any new posts to feature-log.md. If anything matches alert_keywords, notify me."
```

### Step 4: Verify Setup

```bash
openclaw cron list
```

---

## Skills Needed

| Skill | Purpose | Required? |
|-------|---------|-----------|
| **web_fetch** | Scrape pricing pages, blogs, changelogs | ✅ Yes |
| **web_search** | Find competitor news, press releases | ✅ Yes |
| **file read/write** | Track historical data, generate reports | ✅ Yes (built-in) |
| **message** | Send alerts to Telegram/Discord | ✅ Yes |
| **browser** | For JS-heavy pricing pages | Optional |

---

## Example Prompts

### 1️⃣ Initial Setup Scan
```
Read ~/openclaw/competitor-radar/competitors.json. For each competitor, fetch their pricing page and extract all plan names, prices, and key features. Save this as the baseline in pricing-history.md with today's date. Format as a comparison table.
```

### 2️⃣ Deep Dive on Specific Competitor
```
Do a deep competitive analysis on [Competitor Name]:
1. Fetch their pricing page and compare to our last snapshot
2. Check their blog for posts in the last 30 days
3. Search for "[Competitor Name] announcement" or "[Competitor Name] funding" news
4. Search Twitter for what people are saying about them
5. Summarize findings and suggest how we should respond
```

### 3️⃣ Pricing Intelligence Report
```
Generate a pricing comparison matrix:
1. Fetch current pricing from all competitors in competitors.json
2. Compare each tier to our pricing for MyAwesomeApp
3. Identify where we're cheaper, where we're more expensive
4. Flag any changes from pricing-history.md
5. Recommend pricing adjustments if we're significantly misaligned
```

### 4️⃣ Feature Gap Analysis
```
For each competitor in competitors.json:
1. Check their homepage and product pages for feature lists
2. Check their changelog or "what's new" page if available
3. Compare to our feature set
4. Create a feature matrix showing gaps
5. Prioritize which gaps we should close based on frequency across competitors
```

### 5️⃣ Weekly Strategic Digest
```
Generate the weekly competitor digest:
1. Summarize all changes logged this week in feature-log.md
2. Highlight pricing changes from pricing-history.md
3. Search for news about each competitor from the past 7 days
4. Rate overall competitive threat level (Low/Medium/High)
5. Give 3 specific action items for our product/marketing team
Save to weekly-digest.md and send me a summary.
```

---

## Cron Schedule

```bash
# ┌───────────── minute (0-59)
# │ ┌───────────── hour (0-23)  
# │ │ ┌───────────── day of month (1-31)
# │ │ │ ┌───────────── month (1-12)
# │ │ │ │ ┌───────────── day of week (0-6, Sun=0)
# │ │ │ │ │

# Daily pricing check - catches urgent changes
0 8 * * 1-5    "Quick pricing scan..."
# Runs: Mon-Fri at 8:00 AM

# Mid-week intel gathering  
0 14 * * 3     "Blog and news scan..."
# Runs: Wednesday at 2:00 PM

# Weekly comprehensive report
0 20 * * 0     "Full competitor radar..."
# Runs: Sunday at 8:00 PM (prep for Monday planning)

# Monthly deep dive (first Monday)
0 10 * * 1     "[ $(date +%d) -le 7 ] && deep analysis..."
# Runs: First Monday of each month at 10:00 AM
```

**Pro tip:** Stagger your scans to avoid rate limiting and spread the load.

---

## HEARTBEAT.md Config

Add this section to your `HEARTBEAT.md`:

```markdown
## 🎯 Competitor Radar

### Quick Check (if not done in last 6 hours)
- [ ] Any breaking news about competitors? Quick web search for "[competitor] announcement"
- [ ] Check if any competitor pricing page returns different content than cached

### On Significant Finding
Alert immediately if:
- Competitor price dropped >15%
- New "enterprise" tier announced
- Competitor raised funding
- Major feature matching our roadmap launched

### Files to Update
- `competitor-radar/pricing-history.md` - append any price changes
- `competitor-radar/feature-log.md` - log new features spotted
- `memory/YYYY-MM-DD.md` - note competitive intel gathered
```

---

## Expected Results

### Week 1
- ✅ Baseline pricing data for all competitors captured
- ✅ Initial feature comparison matrix created
- ✅ First weekly digest generated

### Month 1
- 📊 Pricing trend data showing competitor movements
- 🚨 2-3 alerts for competitor changes you'd have missed
- 📝 4 weekly digests with actionable insights
- 💡 Identified 1-2 feature gaps worth addressing

### Quarter 1
- 📈 Clear picture of competitor pricing strategies
- 🎯 Data-driven input for your own pricing decisions
- 📋 Feature roadmap informed by competitive gaps
- ⚡ Faster response time to competitor moves (hours vs weeks)

### Sample Weekly Digest Output

```markdown
# Competitor Radar - Week of Jan 15, 2025

## 🚨 Alerts
- **Acme Corp** dropped Pro tier from $49 → $39/mo (-20%)
- **StartupX** announced AI writing assistant feature

## 📊 Pricing Changes
| Competitor | Tier | Was | Now | Change |
|------------|------|-----|-----|--------|
| Acme Corp | Pro | $49 | $39 | -20% ⚠️ |
| BigCo | Team | $29 | $29 | — |

## 📰 News & Updates
- Acme Corp blog: "Introducing Acme 3.0" (Jan 12)
- StartupX featured in TechCrunch funding roundup
- BigCo quiet this week

## 🎯 Recommended Actions
1. **Respond to Acme price cut**: Consider limited-time matching offer or emphasize our value differentiators
2. **AI feature parity**: StartupX's AI writing is on our Q2 roadmap - consider accelerating
3. **Content gap**: BigCo published 3 SEO-optimized guides - assign content team to match

## Threat Level: MEDIUM 🟡
Acme's aggressive pricing needs monitoring. No existential threats.
```

---

## Pro Tips

1. **Start small**: Monitor 2-3 competitors max. Add more once the system is dialed in.

2. **Use alert_keywords wisely**: Add terms that matter to YOUR business. "Enterprise", "free", "API", etc.

3. **Archive your digests**: Move old `weekly-digest.md` to `digests/YYYY-MM-DD.md` monthly for trend analysis.

4. **Combine with customer intel**: Ask OpenClaw to correlate competitor moves with any customer feedback you've logged.

5. **Share with your team**: Have OpenClaw post the weekly digest to a #competitive-intel Slack/Discord channel.

---

## Quick Start Command

Copy-paste this to get started in under 5 minutes:

```
Create ~/openclaw/competitor-radar/ with competitors.json containing:
- Competitor 1: [NAME], pricing at [URL], blog at [URL]  
- Competitor 2: [NAME], pricing at [URL], blog at [URL]

Then fetch each pricing page, extract current prices, and save as pricing-history.md baseline. Tell me what you found.
```

Replace the bracketed items with your actual competitors and you're off to the races! 🏁
