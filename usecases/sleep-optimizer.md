# 😴 Sleep Optimizer

> Wake up refreshed. Optimize your nights to own your days.

---

## The Problem

Poor sleep destroys everything—focus, mood, health. You track with Whoop or Oura but never act on the data. Bedtime routines are inconsistent. You know you should sleep better but don't know what's actually hurting your sleep.

---

## The Solution

Clawdbot connects to your sleep trackers, identifies what's tanking your sleep score, enforces your wind-down routine, and adapts recommendations based on what actually works for *you*.

---

## Setup Guide

### Step 1: Install Sleep & Recovery Skills

```bash
clawdbot skill install whoop
clawdbot skill install oura-ring  # alternative tracker
clawdbot skill install calendar
clawdbot skill install remind-me
```

### Step 2: Configure Sleep Profile

Create `~/clawd/sleep/profile.json`:

```json
{
  "targetBedtime": "22:30",
  "targetWakeTime": "06:30",
  "minSleepHours": 7.5,
  "idealSleepScore": 85,
  "tracker": "whoop",
  "windDownMinutes": 60,
  "factors": {
    "caffeineCutoff": "14:00",
    "alcoholEffect": true,
    "exerciseEffect": true,
    "screensCutoff": "21:30"
  }
}
```

### Step 3: Define Wind-Down Routine

Create `~/clawd/sleep/routine.md`:

```markdown
# Wind-Down Routine (60 min before bed)

## T-60 minutes
- [ ] Put away work
- [ ] Dim lights
- [ ] Start winding down

## T-30 minutes
- [ ] No more screens
- [ ] Prepare for tomorrow
- [ ] Light reading or journaling

## T-10 minutes
- [ ] Bedroom
- [ ] Breathing exercises
- [ ] Sleep mask on

## Disruptors to Track
- Late caffeine
- Alcohol
- Heavy meals after 8 PM
- Intense exercise after 7 PM
- Stressful conversations
- Blue light exposure
```

### Step 4: Create Sleep Log

Create `~/clawd/sleep/log.json`:

```json
{
  "entries": [],
  "weeklyAverage": null,
  "trends": {
    "improving": false,
    "disruptors": [],
    "helpers": []
  }
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `whoop` | Recovery/strain/sleep data |
| `oura-ring` | Sleep stage tracking |
| `calendar` | Schedule awareness |
| `remind-me` | Bedtime reminders |
| `timer` | Wind-down routine timing |

---

## Example Prompts

**Morning check-in:**
```
How did I sleep last night? What does Whoop say about my recovery?
```

**Analyze patterns:**
```
Look at my sleep data for the past 2 weeks. What's helping and what's hurting my sleep quality?
```

**Start wind-down:**
```
Start my wind-down routine. What's my target bedtime tonight?
```

**Track disruptor:**
```
Log that I had coffee at 4 PM today. Flag it for sleep correlation.
```

**Optimize schedule:**
```
I have an important meeting at 9 AM tomorrow. What time should I go to bed to be at peak recovery?
```

**Weekly review:**
```
Give me my sleep report for this week. Am I trending better or worse?
```

---

## Cron Schedule

```
0 21 * * *     # 9 PM - wind-down reminder
30 22 * * *    # 10:30 PM - final bedtime warning
0 7 * * *      # 7 AM - sleep quality report
0 9 * * 0      # Sunday 9 AM - weekly sleep analysis
0 14 * * *     # 2 PM - caffeine cutoff reminder
```

---

## HEARTBEAT.md Config

```markdown
## Sleep
- [ ] Check Whoop/Oura for last night's sleep score
- [ ] Alert if recovery is <50% (adjust today's intensity)
- [ ] Evening: Is wind-down routine starting on time?
- [ ] Track correlation with yesterday's activities
```

---

## Expected Results

**Week 1:**
- Connected to sleep tracker
- Wind-down reminders active
- Baseline data established

**Month 1:**
- Clear understanding of personal sleep disruptors
- Consistent bedtime ±30 minutes
- 10-15% improvement in sleep score

**Month 3:**
- Optimized sleep routine
- Average sleep score 80+
- Better energy, focus, and recovery
- Sleep is no longer a problem—it's an advantage
