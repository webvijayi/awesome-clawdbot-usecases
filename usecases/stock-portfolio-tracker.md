# 📈 Stock Portfolio Tracker

> Stay informed on your investments. Without checking every hour.

---

## The Problem

Portfolio tracking apps show prices but miss context. What earnings are coming? What news affects your holdings? Most investors either check obsessively (stress) or ignore completely (risk).

---

## The Solution

OpenClaw monitors your portfolio with context: tracks prices, alerts on significant moves, summarizes relevant news, and reminds you of earnings dates. Informed without obsessed.

---

## Setup Guide

### Step 1: Install Finance Skills

```bash
openclaw skill install stock-analysis
openclaw skill install yahoo-finance
openclaw skill install portfolio-watcher
```

### Step 2: Enter Your Holdings

Create `~/openclaw/portfolio/holdings.json`:

```json
{
  "holdings": [
    {
      "symbol": "AAPL",
      "shares": 50,
      "costBasis": 145.00
    },
    {
      "symbol": "GOOGL",
      "shares": 20,
      "costBasis": 125.00
    },
    {
      "symbol": "VTI",
      "shares": 100,
      "costBasis": 220.00
    }
  ],
  "watchlist": ["MSFT", "AMZN", "NVDA"]
}
```

### Step 3: Set Alert Thresholds

Create `~/openclaw/portfolio/alerts.md`:

```markdown
# Portfolio Alerts

## Price Alerts
- Position up/down > 5% in a day
- Hit target price (set per stock)
- 52-week high/low

## News Alerts
- Earnings announcement
- Major news (M&A, leadership, product)
- Analyst rating changes

## Regular Updates
- Daily: Portfolio summary
- Weekly: Performance review
- Quarterly: Rebalancing check
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `stock-analysis` | Stock analysis and metrics |
| `yahoo-finance` | Price and fundamental data |
| `portfolio-watcher` | Portfolio tracking |

---

## Example Prompts

**Morning briefing:**
```
How's my portfolio doing? Any pre-market movers? What earnings are coming this week?
```

**Deep dive:**
```
Analyze AAPL. How's it valued vs peers? What are analysts saying? Any concerns?
```

**Rebalancing:**
```
My tech allocation is 60% of portfolio now. Suggest trades to get back to my 40% target.
```

**Tax planning:**
```
Which positions have losses I could harvest? What's my overall tax situation this year?
```

---

## Cron Schedule

```
0 6 * * 1-5    # 6 AM weekdays - pre-market briefing
0 16 * * 1-5   # 4 PM weekdays - market close summary
0 9 * * 0      # Sunday 9 AM - weekly performance review
0 0 1 */3 *    # Quarterly - rebalancing check
```

---

## Expected Results

**Week 1:**
- Portfolio tracked in one place
- Relevant alerts configured

**Month 1:**
- Never miss important news
- Better informed decisions

**Ongoing:**
- Reduced checking anxiety
- Systematic investment approach
- Clear tax-loss harvesting
