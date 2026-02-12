# 🎯 Lead Scoring System

> Focus on leads that convert. Stop wasting time on tire-kickers.

---

## The Problem

Not all leads are equal, but treating them equally wastes time. Your inbox mixes hot prospects with students, competitors, and people who'll never buy. Without scoring, you either respond to everyone (burnout) or miss the good ones.

---

## The Solution

Clawdbot automatically scores every lead based on signals you define: company size, title, engagement, tech stack, funding status. You see a prioritized list and act accordingly.

---

## Setup Guide

### Step 1: Install Sales Skills

```bash
clawdbot skill install hubspot  # or your CRM
clawdbot skill install apollo
clawdbot skill install gmail
clawdbot skill install linkedin
```

### Step 2: Define Scoring Criteria

Create `~/clawd/leads/scoring.json`:

```json
{
  "firmographics": {
    "employeeCount": {
      "1-10": 5,
      "11-50": 15,
      "51-200": 25,
      "201-1000": 20,
      "1000+": 10
    },
    "funding": {
      "seed": 10,
      "seriesA": 20,
      "seriesB+": 25,
      "public": 15
    }
  },
  "title": {
    "CEO/Founder": 30,
    "VP/Director": 25,
    "Manager": 15,
    "Individual": 5
  },
  "engagement": {
    "visitedPricing": 20,
    "downloadedContent": 15,
    "openedEmails": 10,
    "bookedDemo": 40
  },
  "thresholds": {
    "hot": 70,
    "warm": 40,
    "cold": 0
  }
}
```

### Step 3: Set Up Routing Rules

Create `~/clawd/leads/routing.md`:

```markdown
# Lead Routing

## Hot Leads (70+)
- Notify immediately
- Personal outreach within 1 hour
- Research company before call

## Warm Leads (40-69)
- Add to nurture sequence
- Respond within 24 hours
- Automated follow-up

## Cold Leads (<40)
- Automated acknowledgment
- Marketing nurture only
- Review weekly for reclassification
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `hubspot` | CRM integration |
| `apollo` | Lead enrichment |
| `gmail` | Email monitoring |
| `linkedin` | Profile enrichment |

---

## Example Prompts

**Score new lead:**
```
New lead: [name] from [company]. Score them and tell me what I should know before reaching out.
```

**Daily prioritization:**
```
Show me today's leads ranked by score. Who should I focus on first?
```

**Pattern analysis:**
```
What do my converted customers have in common? Update my scoring weights.
```

**Enrich missing data:**
```
This lead is missing company info. Research them and update the record.
```

---

## Cron Schedule

```
*/15 * * * *   # Every 15 min - score new leads
0 8 * * 1-5    # 8 AM weekdays - daily priority list
0 10 * * 1     # Monday 10 AM - weekly pipeline review
```

---

## Expected Results

**Week 1:**
- All leads auto-scored
- Clear prioritization

**Month 1:**
- 50% more time on high-value leads
- Faster response to hot prospects

**Month 3:**
- Higher conversion rate
- Data-driven scoring refinement
- Sales efficiency up 30%+
