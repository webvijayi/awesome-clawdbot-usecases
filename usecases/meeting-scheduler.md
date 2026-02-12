# 🗓️ Smart Meeting Scheduler

> Schedule meetings in seconds. Timezone math done for you, conflicts detected, follow-ups automated.

---

## The Problem

Scheduling meetings across timezones is a nightmare. You're juggling Calendly links, checking five people's availability, doing timezone math in your head, and manually sending follow-up reminders. Half the meeting gets wasted because nobody sent an agenda, and action items disappear into the void after the call ends.

---

## The Solution

Clawdbot handles the entire meeting lifecycle: finds times that work across timezones, checks everyone's availability, sends calendar invites with context, reminds participants before the meeting, and automatically captures and distributes follow-up action items.

---

## Setup Guide

### Step 1: Install Calendar Skills

```bash
clawdbot skill install calendar       # Google Calendar integration
clawdbot skill install ical           # iCal/Apple Calendar support
clawdbot skill install remind-me      # Smart reminders
clawdbot skill install gmail          # Email invites
```

### Step 2: Configure Timezone Preferences

Create `~/clawd/meetings/config.json`:

```json
{
  "myTimezone": "America/New_York",
  "workingHours": {
    "start": "09:00",
    "end": "18:00",
    "days": ["monday", "tuesday", "wednesday", "thursday", "friday"]
  },
  "bufferMinutes": 15,
  "defaultDuration": 30,
  "preferredTimes": ["10:00", "14:00", "16:00"],
  "avoidTimes": ["12:00-13:00"]
}
```

### Step 3: Set Up Contact Timezones

Create `~/clawd/meetings/contacts.json`:

```json
{
  "contacts": [
    {"name": "Sarah", "email": "sarah@example.com", "timezone": "Europe/London"},
    {"name": "Raj", "email": "raj@example.com", "timezone": "Asia/Kolkata"},
    {"name": "Alex", "email": "alex@example.com", "timezone": "America/Los_Angeles"}
  ]
}
```

### Step 4: Create Meeting Templates

Create `~/clawd/meetings/templates.md`:

```markdown
# Meeting Templates

## Quick Sync (15 min)
- No agenda required
- Reminder: 5 min before

## 1:1 (30 min)
- Include talking points
- Reminder: 1 hour before
- Follow-up: Action items within 24h

## Team Meeting (60 min)
- Agenda required 24h before
- Reminder: 1 day + 1 hour before
- Follow-up: Notes + recording link
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `calendar` | Google Calendar read/write |
| `ical` | Apple Calendar support |
| `remind-me` | Pre-meeting reminders |
| `gmail` | Send invites and follow-ups |

---

## Example Prompts

**Schedule a meeting:**
```
Schedule a 30-min call with Sarah and Raj sometime next week. 
Find a time that works for all timezones.
```

**Check availability:**
```
What does my Thursday look like? When am I free for a 1-hour meeting?
```

**Timezone conversion:**
```
If I schedule a call at 3 PM my time, what time is that for Sarah in London and Raj in Mumbai?
```

**Meeting follow-up:**
```
We just finished the product sync. Send follow-up notes to all participants 
with these action items: [list items]
```

**Reschedule:**
```
Move my 2 PM with Alex to tomorrow, same time. Let him know and update the calendar.
```

---

## Cron Schedule

```
0 8 * * *      # 8 AM - Today's meeting briefing
*/30 * * * *   # Every 30 min - Check for upcoming meeting reminders
0 18 * * *     # 6 PM - Summarize today's meetings, pending follow-ups
0 9 * * 1      # Monday 9 AM - Week's meeting overview
```

---

## HEARTBEAT.md Config

```markdown
## Meetings
- [ ] Any meetings in the next 2 hours needing prep?
- [ ] Outstanding meeting follow-ups not sent?
- [ ] Calendar conflicts for tomorrow?
```

---

## Expected Results

**Week 1:**
- Zero timezone confusion
- All meetings have proper calendar events

**Month 1:**
- 80% reduction in scheduling back-and-forth
- Automatic follow-ups on all meetings
- No more missed meeting prep

**Ongoing:**
- Meetings start on time, end with clear actions
- Full calendar visibility across timezones
- Professional, consistent communication
