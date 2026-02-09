# Meeting ROI Maximizer

> Turn every meeting from a time sink into a strategic opportunity with automated research, preparation, and follow-through.

## The Problem

Most professionals spend 23+ hours per week in meetings, yet walk in unprepared—not knowing attendees' backgrounds, missing context from past interactions, or forgetting to follow up afterward. This leads to missed opportunities, repeated conversations, and meetings that could have been emails. The cognitive load of researching attendees, reviewing past threads, and tracking outcomes across dozens of weekly meetings is simply unsustainable manually.

## The Solution

Clawdbot transforms your meeting workflow into a high-ROI system:

- **Before meetings**: Automatically researches attendees (LinkedIn, company news, past email threads), generates contextual agendas, and briefs you with everything you need to know
- **After meetings**: Transcribes notes into action items, drafts personalized follow-up emails, and tracks which meetings actually led to outcomes
- **Ongoing**: Maintains a "meeting intelligence" database so you never lose context between interactions

Works with **Google Calendar** (via gcal skill) or **Apple Calendar** (via ical skill).

## Setup Guide

### Step 1: Enable Required Skills

```bash
# Check available skills
clawdbot skills list

# Enable calendar integration (choose one)
clawdbot skills enable gcal      # For Google Calendar
clawdbot skills enable ical      # For Apple Calendar

# Enable email for follow-ups
clawdbot skills enable gmail     # or your email provider

# Enable web search for research
clawdbot skills enable brave     # Web search for company news
```

### Step 2: Create Meeting Intelligence Directory

Ask Clawdbot:
```
Create a meeting intelligence system with this structure:
- meetings/briefs/ (pre-meeting research)
- meetings/notes/ (meeting notes and summaries)
- meetings/followups/ (draft emails)
- meetings/outcomes/ (track what meetings led to)
- meetings/people/ (attendee profiles we've researched)
```

### Step 3: Configure HEARTBEAT.md

Add the meeting checks to your `HEARTBEAT.md` (see config section below).

### Step 4: Set Up Cron Jobs

Create the automated schedules (see Cron Schedule section below).

### Step 5: Create Meeting Brief Template

Ask Clawdbot:
```
Create a meeting brief template at meetings/BRIEF_TEMPLATE.md with sections for:
- Meeting basics (title, time, attendees)
- Attendee profiles (role, company, LinkedIn summary)
- Past interactions (emails, previous meetings)
- Company news (recent press, funding, product launches)
- Suggested talking points
- Questions to ask
- Desired outcomes
```

## Skills Needed

| Skill | Purpose | Required? |
|-------|---------|-----------|
| `gcal` or `ical` | Calendar access for meeting details | ✅ Yes |
| `gmail` / `email` | Review past threads, send follow-ups | ✅ Yes |
| `brave` | Web search for company news, LinkedIn | ✅ Yes |
| `browser` | Deep research on attendees/companies | Optional |
| `notion` / `obsidian` | Store meeting notes long-term | Optional |

## Example Prompts

### 1. Morning Meeting Prep (Daily)
```
Check my calendar for today's meetings. For each meeting with external 
attendees, create a brief in meetings/briefs/YYYY-MM-DD-{meeting-slug}.md:

1. List all attendees with their titles/companies
2. Search for recent news about their companies (last 30 days)
3. Check my email for any past threads with these people
4. Suggest 3 talking points based on context
5. Note any action items from previous meetings with them

Skip internal 1:1s and recurring standups.
```

### 2. Post-Meeting Processing
```
I just finished my meeting "{meeting name}". Here are my raw notes:

{paste notes}

Please:
1. Extract clear action items with owners and due dates
2. Summarize key decisions made
3. Draft a follow-up email to attendees with:
   - Thank you for their time
   - Summary of what we discussed
   - Clear next steps and owners
4. Save the structured notes to meetings/notes/YYYY-MM-DD-{slug}.md
5. Save the draft email to meetings/followups/YYYY-MM-DD-{slug}.md
```

### 3. Attendee Deep Dive
```
I have a meeting tomorrow with {name} from {company}. Do comprehensive research:

1. Find their LinkedIn profile and summarize their career path
2. Search for any talks, podcasts, or articles they've published
3. Find recent news about {company} (funding, product launches, leadership changes)
4. Check my email history with them or anyone at {company}
5. Look for mutual connections or shared interests
6. Save profile to meetings/people/{name-slug}.md

Give me 5 personalized conversation starters based on your research.
```

### 4. Meeting ROI Analysis (Weekly)
```
Analyze my meeting effectiveness for this week:

1. List all meetings I had (from calendar)
2. Check meetings/outcomes/ for any logged results
3. Categorize meetings: led-to-action, informational, could-have-been-email
4. Calculate rough time spent in each category
5. Identify meetings that should be declined, shortened, or made async
6. Update meetings/outcomes/weekly-YYYY-WW.md with this analysis
```

### 5. Follow-Up Tracker
```
Check my meetings/followups/ for any draft emails older than 24 hours 
that I haven't sent yet. For each one:

1. Remind me what the meeting was about
2. Show me the draft
3. Ask if I want to send it, edit it, or discard it

Also check meetings/notes/ for any action items assigned to ME that 
are due soon and haven't been completed.
```

## Cron Schedule

Add these to your Clawdbot cron configuration:

```bash
# Morning meeting prep - runs at 7:00 AM on weekdays
# Researches all meetings for the day and creates briefs
0 7 * * 1-5  "Check today's calendar and prepare meeting briefs for any external meetings. Save to meetings/briefs/"

# Evening follow-up reminder - runs at 5:30 PM on weekdays  
# Reminds you to process any meetings that need follow-ups
30 17 * * 1-5  "Check if I had any meetings today that need follow-up emails drafted. List them and ask if I want to process any."

# Weekly meeting ROI review - runs Sunday at 7 PM
# Analyzes meeting effectiveness for the week
0 19 * * 0  "Generate my weekly meeting ROI analysis. How many meetings, how many had clear outcomes, time spent. Save to meetings/outcomes/weekly-report.md"

# Next-day VIP prep - runs at 8 PM on weekdays
# Deep research for important meetings tomorrow
0 20 * * 1-5  "Check tomorrow's calendar for high-stakes meetings (external, first-time, exec-level). Do deep research on attendees and companies. Alert me if anything important found."
```

### Cron Expression Reference

| Expression | Meaning |
|------------|---------|
| `0 7 * * 1-5` | 7:00 AM, Monday-Friday |
| `30 17 * * 1-5` | 5:30 PM, Monday-Friday |
| `0 19 * * 0` | 7:00 PM, Sunday |
| `0 20 * * 1-5` | 8:00 PM, Monday-Friday |

## HEARTBEAT.md Config

Add this to your `HEARTBEAT.md`:

```markdown
## Meeting Intelligence Checks

### Every Heartbeat (if between 7 AM - 6 PM on weekdays)
- [ ] Check calendar for meetings starting in next 2 hours
- [ ] If meeting soon and no brief exists in meetings/briefs/, create one
- [ ] Check for any meeting that ended 1+ hours ago without notes processed

### Proactive Alerts
Notify me if:
- Meeting in <30 min with external attendees and no prep done
- Found significant news about a company I'm meeting with today
- Action item from past meeting is overdue

### Skip
- Internal recurring meetings (standups, 1:1s with directs)
- Meetings I declined or marked tentative
- Weekends and outside work hours (unless calendar shows something)
```

## Expected Results

### Week 1
- ✅ Meeting briefs auto-generated for external meetings
- ✅ Never walk into a meeting not knowing who you're talking to
- ✅ Follow-up emails drafted within hours, not days

### Month 1
- 📊 **Time saved**: 3-5 hours/week on meeting prep and follow-ups
- 📊 **Response rate**: Follow-ups sent same-day → better response rates
- 📊 **Context retained**: Attendee profiles accumulate in meetings/people/
- 📊 **Patterns emerge**: Weekly ROI reports show which meetings matter

### Quarter 1
- 🎯 **Meeting quality**: Walk in prepared, walk out with clear actions
- 🎯 **Relationship building**: Reference past conversations accurately
- 🎯 **Time reclaimed**: Decline/shorten meetings that don't drive outcomes
- 🎯 **Outcome tracking**: Clear data on which meetings led to deals, projects, or decisions

### Sample Metrics to Track

```markdown
## Meeting ROI Dashboard (meetings/outcomes/dashboard.md)

### This Month
- Total meetings: 47
- With external parties: 18
- Briefs generated: 18 (100%)
- Follow-ups sent same-day: 15 (83%)
- Meetings → concrete outcomes: 12 (26%)
- Hours in meetings: 31
- Estimated hours saved on prep: 6

### Outcome Categories
- Led to deal/revenue: 3
- Led to partnership: 2
- Led to project kickoff: 4
- Informational (valuable): 8
- Could have been email: 12
- Unclear value: 18
```

---

## Pro Tips

1. **Tag VIP meetings**: Add `[VIP]` to meeting titles for priority research
2. **Use consistent slugs**: Name files by date and meeting for easy searching
3. **Build the people database**: Every new contact gets a profile in meetings/people/
4. **Review weekly**: The ROI analysis only works if you log outcomes
5. **Iterate your templates**: Adjust the brief template based on what you actually use

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Calendar not syncing | Check `clawdbot skills test gcal` or `ical` |
| LinkedIn blocked | Use browser skill with rate limiting, or manual lookup |
| Email search slow | Narrow date ranges, use specific search terms |
| Too many briefs | Add filters: skip <15 min meetings, internal-only, recurring |

---

*This use case turns meetings from a necessary evil into a competitive advantage. You'll know more about who you're meeting than they know about you.*
