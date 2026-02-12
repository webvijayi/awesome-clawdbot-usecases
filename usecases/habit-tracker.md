# 🎯 Habit Tracker & Accountability Partner

> Build habits that stick. Never break the chain.

---

## The Problem

Habit apps are easy to ignore. You set ambitious goals, track for a week, then forget. There's no real accountability, no adaptation when life gets busy, and no celebration when you succeed.

---

## The Solution

OpenClaw becomes your accountability partner: checks in daily, celebrates streaks, adjusts when you're struggling, and provides the gentle (or firm) nudge you need. It understands context—a missed day during illness is different from laziness.

---

## Setup Guide

### Step 1: Install Productivity Skills

```bash
openclaw skill install todoist  # or ticktick, omnifocus
openclaw skill install timer
openclaw skill install remind-me
```

### Step 2: Define Your Habits

Create `~/openclaw/habits/habits.json`:

```json
{
  "habits": [
    {
      "name": "Morning Exercise",
      "frequency": "daily",
      "trigger": "after waking",
      "duration": "30 min",
      "streak": 0,
      "bestStreak": 0
    },
    {
      "name": "Read",
      "frequency": "daily",
      "trigger": "before bed",
      "duration": "20 min",
      "streak": 0,
      "bestStreak": 0
    },
    {
      "name": "Weekly Review",
      "frequency": "weekly",
      "trigger": "Sunday evening",
      "duration": "1 hour",
      "streak": 0,
      "bestStreak": 0
    }
  ],
  "history": []
}
```

### Step 3: Set Accountability Level

Create `~/openclaw/habits/settings.md`:

```markdown
# Accountability Settings

## Reminder Style
- Gentle: Friendly nudge, no pressure
- Moderate: Clear reminder with streak info
- Intense: Don't let me make excuses

Current: Moderate

## Check-in Times
- Morning: 7:00 AM
- Evening: 9:00 PM

## Streak Rules
- Grace days allowed: 1 per week
- Sick days: Don't break streak
- Travel: Adjusted expectations
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `todoist` | Task management integration |
| `timer` | Timed habit sessions |
| `remind-me` | Smart reminders |
| `calendar` | Schedule awareness |

---

## Example Prompts

**Log a habit:**
```
Done with my morning exercise - 35 minute run.
```

**Check status:**
```
How are my habits going this week? Show me my streaks.
```

**Adjust expectations:**
```
I'm traveling this week. Adjust my habits to travel mode.
```

**Recover from a miss:**
```
I missed exercise yesterday. Help me not let it become two days.
```

**Weekly review:**
```
Give me my habit report for this week. What worked? What needs attention?
```

---

## Cron Schedule

```
0 7 * * *      # 7 AM - morning habit reminder
0 21 * * *     # 9 PM - evening check-in
0 10 * * 0     # 10 AM Sunday - weekly review
0 0 1 * *      # 1st of month - monthly progress report
```

---

## HEARTBEAT.md Config

```markdown
## Habits
- [ ] Any habits due that haven't been logged?
- [ ] Streaks at risk of breaking?
- [ ] Celebrate milestone streaks (7, 30, 100 days)
```

---

## Expected Results

**Week 1:**
- Clear habit tracking system
- Daily accountability check-ins

**Month 1:**
- 2-3 habits becoming automatic
- Longest streaks established
- Understanding of what breaks habits

**Month 3:**
- Multiple 30+ day streaks
- Habits integrated into identity
- Sustainable long-term behavior change
