# 💪 Workout Accountability Partner

> Train smarter. Never skip leg day.

---

## The Problem

Workout motivation fades. You start strong, skip a few days, then stop entirely. Fitness apps track but don't motivate. Personal trainers are expensive.

---

## The Solution

Clawdbot is your accountability partner: tracks workouts, adjusts plans based on progress, celebrates wins, and calls you out (gently) when you're slacking.

---

## Setup Guide

### Step 1: Install Fitness Skills

```bash
clawdbot skill install whoop  # or strava, workout-logger
clawdbot skill install strava-cycling-coach
```

### Step 2: Set Goals

Create `~/clawd/fitness/goals.json`:

```json
{
  "weeklyWorkouts": 4,
  "types": ["strength", "cardio", "flexibility"],
  "currentProgram": "strength building",
  "restDays": ["Sunday"]
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `whoop` | Recovery/strain tracking |
| `strava-cycling-coach` | Cardio analytics |
| `workout-logger` | Manual logging |

---

## Example Prompts

**Log workout:**
```
Just finished: chest/triceps day. Bench pressed 185 for 5 reps (new PR!).
```

**Plan week:**
```
Plan my workouts for this week. I'm feeling a bit fatigued from last week.
```

**Check progress:**
```
How am I tracking this month? Am I improving on my main lifts?
```

---

## Cron Schedule

```
0 6 * * 1,3,5  # Workout day reminders
0 20 * * 0     # Sunday - weekly progress
```

---

## Expected Results

- Consistent workout routine
- Visible progress tracking
- Accountability that works
