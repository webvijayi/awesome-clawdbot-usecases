# 💰 Price Drop Alerter

> Never pay full price again. Get alerted the moment prices drop.

---

## The Problem

You want to buy something but it's too expensive. You check periodically, forget, then buy at full price right before a sale. Or you set alerts that spam you with 1% changes. Neither works.

---

## The Solution

Clawdbot monitors products across multiple retailers, tracks price history, predicts good buying times, and alerts you only when prices hit YOUR target or drop significantly.

---

## Setup Guide

### Step 1: Install Shopping Skills

```bash
clawdbot skill install camelcamelcamel-alerts  # Amazon price tracking
clawdbot skill install marktplaats  # Dutch marketplace
clawdbot skill install whcli  # Austrian Willhaben
```

### Step 2: Create Watchlist

Create `~/clawd/shopping/watchlist.json`:

```json
{
  "items": [
    {
      "name": "Sony WH-1000XM5",
      "url": "https://amazon.com/dp/...",
      "targetPrice": 280,
      "currentPrice": 350,
      "addedDate": "2026-01-15",
      "priority": "high"
    },
    {
      "name": "Standing Desk",
      "url": "https://...",
      "targetPrice": 400,
      "currentPrice": 599,
      "addedDate": "2026-01-20",
      "priority": "medium"
    }
  ],
  "priceHistory": {}
}
```

### Step 3: Set Alert Preferences

Create `~/clawd/shopping/preferences.md`:

```markdown
# Alert Preferences

## Notify me when:
- Price drops below my target
- Price drops 20%+ from recent high
- Lowest price in 30 days
- Lightning deals on watchlist items

## Don't notify for:
- Price changes < 5%
- Items I marked "not urgent"
- Out of stock alerts

## Check frequency:
- High priority: Every 2 hours
- Medium priority: Every 6 hours
- Low priority: Daily
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `camelcamelcamel-alerts` | Amazon price tracking |
| `marktplaats` | Dutch marketplace |
| `whcli` | Austrian Willhaben |
| `brave-search` | Find better prices elsewhere |

---

## Example Prompts

**Add to watchlist:**
```
Track this product: [URL]. Alert me if it drops below $200.
```

**Check status:**
```
Show me my watchlist with current prices. Any good deals right now?
```

**Price research:**
```
I want to buy [product]. Find the best current price across Amazon, Best Buy, and other retailers.
```

**Buying advice:**
```
Is now a good time to buy [product]? Check price history and upcoming sales.
```

---

## Cron Schedule

```
0 */2 * * *    # Every 2 hours - check high priority items
0 8,14,20 * * * # 3x daily - check medium priority
0 8 * * *      # 8 AM - daily watchlist summary
0 0 * * 5      # Midnight Friday - weekend deals preview
```

---

## Expected Results

**Per Purchase:**
- Average 15-30% savings
- Never miss a good sale
- No regret from buying too early

**Monthly:**
- Hundreds saved on planned purchases
- Better buying decisions
- Less time manually checking prices
