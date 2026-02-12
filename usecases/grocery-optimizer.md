# 🛒 Grocery Optimizer

> Meal plan, shop smart, waste less.

---

## The Problem

Grocery shopping without a plan leads to impulse buys, forgotten items, and food waste. Meal planning is tedious. You buy ingredients for recipes you never make.

---

## The Solution

OpenClaw helps plan meals based on what's on sale, generates optimized grocery lists, tracks what you have, and ensures nothing goes to waste.

---

## Setup Guide

### Step 1: Install Shopping Skills

```bash
openclaw skill install bring-shopping
openclaw skill install recipe-to-list
openclaw skill install gurkerl  # or picnic, instacart
```

### Step 2: Configure Preferences

Create `~/openclaw/grocery/preferences.json`:

```json
{
  "dietaryRestrictions": [],
  "householdSize": 2,
  "cookingDays": ["Monday", "Wednesday", "Friday", "Sunday"],
  "budgetWeekly": 150,
  "stores": ["preferred store"]
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `bring-shopping` | Shopping list management |
| `recipe-to-list` | Recipe ingredient extraction |
| `gurkerl`/`picnic` | Online grocery ordering |

---

## Example Prompts

**Weekly planning:**
```
Plan meals for this week. Keep it under $150, use what's in season, and minimize waste.
```

**Recipe to list:**
```
I want to make [recipe]. Add ingredients to my shopping list, minus what I already have.
```

**What's for dinner:**
```
What can I make with chicken, rice, and the vegetables expiring soon?
```

---

## Cron Schedule

```
0 9 * * 0      # Sunday 9 AM - weekly meal planning
0 10 * * 3     # Wednesday - mid-week list check
```

---

## Expected Results

- 20% reduction in grocery spending
- Less food waste
- No more "what's for dinner?" stress
