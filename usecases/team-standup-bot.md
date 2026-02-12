# 🤖 Async Team Standup Bot

> Run standups without the meeting. Blockers surfaced, progress tracked, time saved.

---

## The Problem

Daily standups eat 15-30 minutes of everyone's time, often at the worst part of the morning. Half the team zones out during updates that don't affect them. Remote teams across timezones struggle to find a time that works. Real blockers get buried in routine updates, and nobody actually reads the notes afterward.

---

## The Solution

OpenClaw runs async standups: collects updates via DM at each person's preferred time, identifies blockers automatically, creates digestible summaries, and alerts the right people when action is needed. Your team gets focused time back while staying more informed than before.

---

## Setup Guide

### Step 1: Install Communication Skills

```bash
openclaw skill install slack          # Slack integration
openclaw skill install discord        # Discord support
openclaw skill install telegram       # Telegram bots
openclaw skill install linear         # Issue tracker integration
```

### Step 2: Define Team Structure

Create `~/openclaw/standups/team.json`:

```json
{
  "team": "Engineering",
  "members": [
    {"name": "Alice", "handle": "@alice", "timezone": "America/New_York", "promptTime": "09:00"},
    {"name": "Bob", "handle": "@bob", "timezone": "Europe/London", "promptTime": "09:30"},
    {"name": "Priya", "handle": "@priya", "timezone": "Asia/Kolkata", "promptTime": "10:00"}
  ],
  "summaryChannel": "#engineering-standups",
  "alertChannel": "#engineering-alerts",
  "manager": "@sarah"
}
```

### Step 3: Configure Standup Questions

Create `~/openclaw/standups/questions.md`:

```markdown
# Standup Questions

## Daily (Mon-Fri)
1. What did you accomplish yesterday?
2. What are you working on today?
3. Any blockers or need help with anything?

## Monday Addition
4. What's your main goal for this week?

## Friday Addition
4. What went well this week?
5. What could have gone better?

## Blocker Keywords
- stuck, blocked, waiting on, need help
- can't, unable to, delayed
- dependency, waiting for, blocked by
```

### Step 4: Set Up Blocker Detection

Create `~/openclaw/standups/alerts.md`:

```markdown
# Alert Rules

## Immediate Alert (DM manager)
- Blocker mentioned + "urgent" or "critical"
- Same blocker mentioned 2+ days in a row
- Team member hasn't responded in 48 hours

## Daily Summary Include
- All blockers with owner
- Cross-team dependencies
- Risks to sprint commitments

## Weekly Patterns to Flag
- Team member consistently blocked
- Recurring blocker themes
- Velocity drops
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `slack` | Slack DMs and channels |
| `discord` | Discord integration |
| `telegram` | Telegram bot support |
| `linear` | Link blockers to issues |

---

## Example Prompts

**Start standup collection:**
```
Send standup prompts to the engineering team. Use each person's preferred time.
```

**Generate summary:**
```
Create today's standup summary from all responses. Highlight blockers prominently.
```

**Blocker follow-up:**
```
Alice mentioned she's blocked on the API review. Check if this was resolved and 
remind the reviewer if not.
```

**Weekly report:**
```
Generate this week's standup report: themes, blockers resolved, velocity trends, 
and any concerns for next week.
```

**Patterns analysis:**
```
Analyze the last month of standups. What are recurring blockers? Who's consistently 
overloaded? Any process improvements we should make?
```

---

## Cron Schedule

```
0 9-11 * * 1-5  # 9-11 AM window - Send individual prompts (per timezone)
0 12 * * 1-5    # 12 PM - Compile and post daily summary
0 17 * * 1-5    # 5 PM - Check for unresolved blockers
0 10 * * 1      # Monday 10 AM - Post last week's summary
0 16 * * 5      # Friday 4 PM - Generate weekly insights
```

---

## HEARTBEAT.md Config

```markdown
## Standups
- [ ] All team members submitted today's update?
- [ ] Any blockers mentioned needing escalation?
- [ ] Same blocker appearing 2+ consecutive days?
```

---

## Expected Results

**Week 1:**
- Team adjusts to async format
- Blockers surfaced faster than in sync standups

**Month 1:**
- 2-3 hours/week saved per team member
- Zero dropped blockers
- Manager has better visibility without attending every standup

**Ongoing:**
- Data-driven insights into team patterns
- Faster blocker resolution (hours, not days)
- Team prefers async format for deep work time
