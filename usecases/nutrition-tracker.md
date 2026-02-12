# 🥗 Nutrition Tracker

> Eat smarter, not harder. Log meals, hit macros, get personalized suggestions.

---

## The Problem

Nutrition apps are tedious. Scanning barcodes, weighing portions, logging every ingredient—it's exhausting. You start motivated but quit within a week. Meanwhile, you have no idea if you're actually eating enough protein or too many carbs.

---

## The Solution

Clawdbot makes logging effortless: snap a photo or describe your meal in plain language. It estimates macros, tracks patterns, suggests meals that fit your goals, and adapts to your preferences over time.

---

## Setup Guide

### Step 1: Install Nutrition Skills

```bash
clawdbot skill install nutritionix  # food database
clawdbot skill install recipe-parser
clawdbot skill install remind-me
clawdbot skill install grocery-list  # optional
```

### Step 2: Configure Nutrition Goals

Create `~/clawd/nutrition/profile.json`:

```json
{
  "goal": "maintain",
  "calories": 2200,
  "macros": {
    "protein": 150,
    "carbs": 220,
    "fat": 73
  },
  "preferences": {
    "diet": "none",
    "allergies": [],
    "dislikes": ["cilantro"],
    "cuisines": ["mediterranean", "asian", "mexican"]
  },
  "mealTimes": {
    "breakfast": "08:00",
    "lunch": "12:30",
    "dinner": "19:00"
  },
  "trackingLevel": "moderate"
}
```

### Step 3: Define Meal Templates

Create `~/clawd/nutrition/favorites.json`:

```json
{
  "quickMeals": [
    {
      "name": "Greek Yogurt Bowl",
      "calories": 350,
      "protein": 25,
      "carbs": 35,
      "fat": 12
    },
    {
      "name": "Chicken Salad",
      "calories": 450,
      "protein": 40,
      "carbs": 20,
      "fat": 22
    },
    {
      "name": "Protein Shake",
      "calories": 250,
      "protein": 30,
      "carbs": 15,
      "fat": 5
    }
  ],
  "restaurants": {
    "Chipotle": {
      "usual": "Chicken Bowl",
      "macros": { "calories": 650, "protein": 50, "carbs": 45, "fat": 20 }
    }
  }
}
```

### Step 4: Create Daily Log Structure

Create `~/clawd/nutrition/log/template.json`:

```json
{
  "date": "",
  "meals": [],
  "totals": {
    "calories": 0,
    "protein": 0,
    "carbs": 0,
    "fat": 0
  },
  "water": 0,
  "notes": ""
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `nutritionix` | Food/macro database |
| `recipe-parser` | Parse meal ingredients |
| `remind-me` | Meal logging reminders |
| `grocery-list` | Shopping from meal plans |
| `whoop` | Calorie burn correlation |

---

## Example Prompts

**Quick log:**
```
Lunch: grilled chicken breast, cup of rice, steamed broccoli, olive oil drizzle.
```

**Photo log:**
```
[photo attached] Log this meal. Estimate macros.
```

**Check progress:**
```
How am I doing today? How much protein do I have left to hit my goal?
```

**Meal suggestion:**
```
I need 40g more protein for dinner but only 400 calories left. What should I eat?
```

**Weekly analysis:**
```
Analyze my nutrition this week. Am I consistently hitting protein? Where am I slipping?
```

**Restaurant help:**
```
Going to Chipotle for lunch. What should I order to stay on track?
```

**Meal prep planning:**
```
Plan my meals for the week. Focus on high protein, moderate carbs. Include a shopping list.
```

---

## Cron Schedule

```
0 8 * * *      # 8 AM - morning reminder to log breakfast
0 13 * * *     # 1 PM - lunch logging check
0 20 * * *     # 8 PM - daily summary and dinner reminder
0 9 * * 0      # Sunday 9 AM - weekly nutrition review
0 10 * * 0     # Sunday 10 AM - meal prep suggestions
```

---

## HEARTBEAT.md Config

```markdown
## Nutrition
- [ ] Any meals logged today? Gentle reminder if not
- [ ] Protein check - on track or falling behind?
- [ ] Water intake reminder (aim for 8 glasses)
- [ ] If consistently low on protein, suggest easy additions
```

---

## Smart Features

**Adaptive Learning:**
- Remembers your frequent meals
- Learns portion sizes at regular restaurants
- Suggests foods you actually like

**Macro Balancing:**
- End-of-day suggestions to hit targets
- "You're 30g short on protein - here are quick options"
- Adjusts for workout days automatically

**Trend Analysis:**
- Weekly averages vs goals
- Identifies problem meals/days
- Correlates with energy/sleep if tracking

---

## Expected Results

**Week 1:**
- Effortless meal logging established
- Baseline eating patterns visible
- Macro awareness increased

**Month 1:**
- Consistently hitting protein goals
- Better food choices through awareness
- Favorite meals catalogued for quick logging
- Clear understanding of calorie intake

**Month 3:**
- Intuitive eating aligned with goals
- Minimal logging needed (patterns learned)
- Sustainable nutrition habits
- Body composition changes visible
