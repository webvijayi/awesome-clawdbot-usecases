# 💳 Expense Tracker & Analyzer

> Know where your money goes. Without manual data entry.

---

## The Problem

Tracking expenses is tedious. You start with good intentions, manually log for a week, then stop. Bank statements show transactions but no insights. By month-end, you're wondering where the money went.

---

## The Solution

OpenClaw automatically categorizes transactions, identifies spending patterns, alerts on unusual charges, and gives you clear insights—no manual entry required.

---

## Setup Guide

### Step 1: Install Finance Skills

```bash
openclaw skill install copilot-money  # or plaid
openclaw skill install excel
```

### Step 2: Configure Categories

Create `~/openclaw/expenses/categories.json`:

```json
{
  "categories": {
    "essentials": ["rent", "utilities", "groceries", "insurance"],
    "transport": ["uber", "lyft", "gas", "transit"],
    "food": ["restaurants", "delivery", "coffee"],
    "subscriptions": ["netflix", "spotify", "gym"],
    "shopping": ["amazon", "clothing"],
    "health": ["pharmacy", "doctor"]
  },
  "budgets": {
    "food": 500,
    "subscriptions": 100,
    "shopping": 300
  }
}
```

### Step 3: Set Alert Rules

Create `~/openclaw/expenses/alerts.md`:

```markdown
# Expense Alerts

## Notify Immediately
- Transactions > $100
- New recurring charges
- International transactions
- Declined transactions

## Weekly Check
- Category over budget by >20%
- Unusual spending pattern
- Forgotten subscriptions

## Monthly Review
- Total vs budget
- Category breakdown
- Subscription audit
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `copilot-money` | Bank account integration |
| `plaid` | Financial data aggregation |
| `excel` | Export and analysis |

---

## Example Prompts

**Daily update:**
```
What did I spend today? Anything unusual?
```

**Weekly review:**
```
Give me my spending breakdown this week by category. How am I tracking against budgets?
```

**Find waste:**
```
Identify any subscriptions I haven't used in 30 days. Any duplicate services?
```

**Trend analysis:**
```
How does my food spending this month compare to the last 3 months? What's driving changes?
```

---

## Cron Schedule

```
0 8 * * *      # 8 AM - yesterday's transactions summary
0 10 * * 1     # Monday 10 AM - weekly spending report
0 9 1 * *      # 1st of month - monthly budget review
0 0 15 * *     # 15th of month - mid-month check-in
```

---

## Expected Results

**Week 1:**
- All transactions auto-categorized
- Spending visibility achieved

**Month 1:**
- Identify 10-20% wasteful spending
- Clear budget tracking

**Month 3:**
- Spending habits improved
- No surprise charges
- Financial goals on track
