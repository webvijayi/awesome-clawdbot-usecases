# 🧠 Mental Health Check-In

> Know yourself better. Track moods, prep for therapy, spot patterns before they spiral.

---

## The Problem

Mental health is invisible until it's not. You feel "off" but can't explain why. Therapy sessions start with "how was your week?" and you draw a blank. Bad patterns sneak up because you're not tracking them.

---

## The Solution

Clawdbot provides gentle daily check-ins, logs moods without judgment, helps you prepare for therapy sessions with actual data, and identifies patterns before they become problems.

---

## Setup Guide

### Step 1: Install Mindfulness & Journaling Skills

```bash
clawdbot skill install obsidian-conversation-backup  # or notion
clawdbot skill install remind-me
clawdbot skill install calendar
```

### Step 2: Configure Check-In Profile

Create `~/clawd/mentalhealth/config.json`:

```json
{
  "checkInTimes": ["09:00", "21:00"],
  "therapyDay": "Thursday",
  "therapyTime": "14:00",
  "moodScale": "1-10",
  "trackingAreas": [
    "mood",
    "anxiety",
    "energy",
    "sleep_quality",
    "social_connection",
    "accomplishment"
  ],
  "triggerWarnings": {
    "lowMoodStreak": 3,
    "anxietyThreshold": 7,
    "isolationDays": 2
  },
  "storage": "~/clawd/mentalhealth/entries/"
}
```

### Step 3: Set Up Check-In Questions

Create `~/clawd/mentalhealth/questions.md`:

```markdown
# Morning Check-In (2 min)
- How are you feeling right now? (1-10)
- Any anxiety present? (1-10)
- How did you sleep?
- What's one thing you're looking forward to?

# Evening Check-In (3 min)
- Overall mood today (1-10)
- Energy level (1-10)
- Did you connect with anyone today?
- One thing that went well
- Anything weighing on you?

# Weekly Patterns to Watch
- Are mood scores trending down?
- More anxious days than calm?
- Social isolation increasing?
- Self-care being neglected?

# Therapy Prep Questions
- What's been on my mind this week?
- Any breakthrough moments?
- What am I avoiding?
- What do I want to work on next?
```

### Step 4: Create Entry Template

Create `~/clawd/mentalhealth/template.json`:

```json
{
  "date": "",
  "morning": {
    "mood": null,
    "anxiety": null,
    "sleepQuality": null,
    "lookingForward": ""
  },
  "evening": {
    "mood": null,
    "energy": null,
    "socialConnection": false,
    "win": "",
    "concern": ""
  },
  "notes": "",
  "tags": []
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `obsidian-conversation-backup` | Secure entry storage |
| `notion` | Alternative storage |
| `remind-me` | Check-in reminders |
| `calendar` | Therapy scheduling |
| `reflect` | Pattern analysis |

---

## Example Prompts

**Morning check-in:**
```
Morning check-in. Mood is 6, anxiety 4, slept okay. Looking forward to lunch with a friend.
```

**Quick mood log:**
```
Feeling anxious right now - about a 7. Work deadline stress.
```

**Pattern analysis:**
```
How has my mood been this month? Any patterns with days of the week, sleep, or social time?
```

**Therapy prep:**
```
I have therapy tomorrow. Summarize my week - moods, themes, and what I might want to discuss.
```

**Concern flag:**
```
I've been feeling low for a few days. Is this worse than my usual patterns?
```

**Gratitude capture:**
```
Good moment: Had a great conversation with [person]. Felt really connected. Log it.
```

---

## Cron Schedule

```
0 9 * * *      # 9 AM - morning check-in prompt
0 21 * * *     # 9 PM - evening reflection
0 9 * * 3      # Wednesday 9 AM - therapy prep (day before)
0 10 * * 0     # Sunday 10 AM - weekly pattern review
```

---

## HEARTBEAT.md Config

```markdown
## Mental Health
- [ ] Check if morning/evening entries logged
- [ ] Alert on 3+ days of low mood (<5)
- [ ] Alert on high anxiety streak (>7 for 2+ days)
- [ ] Therapy prep reminder day before session
- [ ] Celebrate improvement trends
```

---

## Privacy Note

All entries stay local. Nothing is shared unless you explicitly export for therapy sessions. This is your private mental health data.

---

## Expected Results

**Week 1:**
- Daily check-in habit started
- Baseline mood data established
- Low-friction logging system

**Month 1:**
- Clear visibility into mood patterns
- Better therapy sessions with real data
- Early warning for difficult periods
- Increased self-awareness

**Month 3:**
- Deep understanding of personal patterns
- Trigger identification and management
- Stronger therapeutic relationship
- Proactive mental health maintenance
