# Client Memory Hub

> Never forget a client conversation again. Track every touchpoint, remember every preference, nail every follow-up.

## The Problem

You're juggling 30+ clients across email, calls, Slack, WhatsApp, and meetings—and your brain isn't designed to remember that Sarah mentioned her kid's soccer tournament, that Marcus prefers Tuesday calls, or that you promised to check in with Lisa after her product launch. Sticky notes get lost, CRM updates feel like homework, and you've definitely followed up asking "how did the launch go?" when you already asked last week. The mental load of relationship management is crushing your actual work.

## The Solution

OpenClaw becomes your relationship memory layer. After every client interaction, you dump the context in natural language—OpenClaw structures it, stores it, and surfaces it exactly when you need it. Before any call, get a 30-second briefing. After any meeting, capture notes hands-free. Get proactive nudges when follow-ups are due. Your clients feel remembered because they *are* remembered.

## Setup Guide

**Time needed: 15-20 minutes**

### Step 1: Create Client Memory Structure (2 min)

Tell OpenClaw:
```
Create a client memory system with this structure:
- /root/openclaw/clients/contacts.json (master contact list)
- /root/openclaw/clients/interactions/ (individual client folders)
- /root/openclaw/clients/templates/ (briefing templates)
- /root/openclaw/clients/followups.json (scheduled follow-ups)

Initialize contacts.json as an empty array and followups.json as an empty object.
```

### Step 2: Define Your Contact Schema (3 min)

Tell OpenClaw:
```
Add a template for client records. Each client should track:
- name, company, role, email, phone
- communication_preference (channel, time, frequency)
- personal_notes (family, hobbies, important dates)
- business_context (their goals, pain points, what they bought/might buy)
- last_contact (date + summary)
- relationship_health (hot/warm/cold + why)
- follow_up_cadence (days between ideal touchpoints)
```

### Step 3: Import Your First 5 Clients (5 min)

Start with your most important relationships:
```
Add client: Sarah Chen, VP Engineering at TechFlow
- Email: sarah@techflow.io, prefers Slack DMs for quick stuff
- Has 2 kids, big into hiking, husband is David
- Bought our Pro plan in January, considering Enterprise
- Pain point: team scaling too fast, onboarding is chaos
- Follow up every 2 weeks, she likes Tuesday/Thursday afternoons
- Last talked March 15 about the new API features
```

Repeat for 4 more clients. OpenClaw will structure and store.

### Step 4: Configure Your Briefing Workflow (3 min)

```
Create a pre-call briefing template that shows me:
1. Last 3 interactions (date + one-liner each)
2. Any open commitments I made
3. Their current pain points
4. Personal context worth mentioning
5. Suggested talking points

Save to /root/openclaw/clients/templates/briefing.md
```

### Step 5: Set Up Follow-Up Tracking (2 min)

```
Add to HEARTBEAT.md:
- Check /root/openclaw/clients/followups.json for any follow-ups due today or overdue
- Check contacts where last_contact is older than their follow_up_cadence
- Alert me to relationships going cold (no contact in 2x their normal cadence)
```

## Skills Needed

| Skill | Purpose | Required? |
|-------|---------|-----------|
| **gmail** | Scan emails for client context, send follow-ups | Recommended |
| **gcal** | Check for upcoming client meetings, pull context | Recommended |
| **slack** | Monitor client channels, capture conversations | Optional |
| **whatsapp** | Track client messages on WhatsApp | Optional |
| **notion** | Sync with existing CRM/notes | Optional |

**Minimum setup:** No skills needed—you can manually log interactions. But gmail + gcal unlock automatic context gathering.

## Example Prompts

### After a client call:
```
Log client interaction:
Just finished a 30-min call with Sarah Chen. She's excited about the Q2 roadmap, 
especially the Slack integration. Her team grew to 45 people—onboarding pain is 
real. She mentioned David got a promotion, they're celebrating this weekend. 
I promised to send her the beta access form by Friday. Schedule follow-up for 
2 weeks, she wants to loop in her CTO Marcus for a demo.
```

### Before a meeting:
```
Brief me on Sarah Chen - I have a call in 10 minutes
```

### Weekly relationship review:
```
Show me my client relationship health:
- Who's overdue for contact?
- What commitments have I not fulfilled?
- Which relationships are cooling off?
- Any important dates coming up (work anniversaries, birthdays I logged)?
```

### Quick capture on mobile:
```
Quick note: Marcus from TechFlow mentioned they're evaluating competitors. 
Seemed frustrated about our pricing. Flag this as urgent, set follow-up for 
tomorrow with a discount discussion.
```

### Context search:
```
What did I promise Lisa about the API documentation? When did I last mention it?
```

## Cron Schedule

```bash
# Morning briefing: Today's client meetings with full context
0 8 * * 1-5 openclaw cron "Check my calendar for today's client meetings. For each one, pull the client briefing and send me a consolidated prep doc."

# Follow-up scanner: Catch overdue check-ins at lunch
0 12 * * 1-5 openclaw cron "Scan followups.json and all client records. List anyone overdue for contact or approaching their follow-up date. Prioritize by relationship value."

# Weekly relationship report: Friday afternoon reflection
0 16 * * 5 openclaw cron "Generate my weekly client relationship report: interactions logged this week, relationships that warmed or cooled, commitments made, follow-ups scheduled for next week."

# Email context capture: Pull client email threads daily
0 9 * * 1-5 openclaw cron "Scan my inbox for emails from known clients in the last 24h. Log key points to their interaction history. Flag anything that needs my response."

# Monthly deep review: First Monday, relationship audit
0 9 1-7 * 1 openclaw cron "Monthly client audit: Who haven't I contacted in 30+ days? Any clients who went silent? Suggest re-engagement strategies for cold relationships."
```

## HEARTBEAT.md Config

Add this to your `HEARTBEAT.md`:

```markdown
## Client Memory Hub Checks

### Every heartbeat:
- [ ] Check `/root/openclaw/clients/followups.json` for items due today
- [ ] If any overdue follow-ups (due date < today), alert immediately

### 2-3x daily (spread out):
- [ ] Scan client records for `last_contact` older than `follow_up_cadence`
- [ ] Check for unfulfilled commitments older than 3 days
- [ ] If gmail skill available: quick scan for unread client emails

### Alert thresholds:
- 🔴 URGENT: Commitment overdue by 3+ days
- 🟡 WARNING: No contact in 2x normal cadence
- 🟢 INFO: Follow-up due within 24h

### Do NOT alert if:
- It's before 9am or after 6pm
- I'm clearly in a meeting (check calendar)
- I acknowledged the same alert today already
```

## Expected Results

### Week 1:
- All key clients documented with full context
- Pre-call briefings feel like having a personal assistant
- Zero "wait, what did we discuss?" moments

### Month 1:
- Follow-up consistency improves 80%+
- Clients comment on how "you always remember everything"
- No dropped balls on commitments
- Personal touches (birthdays, milestones) happen reliably

### Quarter 1:
- Relationship health trends visible over time
- Pattern recognition kicks in ("clients churn when I don't contact for 3+ weeks")
- New team members can get up to speed on any client in 2 minutes
- You've essentially built a lightweight, AI-powered CRM—for free

### Metrics to track:
- Average days between client contacts (should decrease)
- Commitment fulfillment rate (should hit 95%+)
- Client "save" rate—catching at-risk relationships before they churn
- Time spent on "what was the context again?" (should drop to zero)

---

## Pro Tips

1. **Voice capture**: Use OpenClaw's mobile interface to voice-log interactions right after calls while context is fresh.

2. **Tag important patterns**: When you notice something that works ("Sarah always buys after I mention ROI case studies"), log it as a `what_works` field.

3. **Integrate with calendar**: Name your calendar events with client names, and the morning briefing cron will auto-match.

4. **Graduation criteria**: Once a client is stable/low-touch, extend their cadence. Don't over-contact happy customers.

5. **Failure logging**: When you drop a ball, log *why*. OpenClaw can help you spot patterns in your own failures.

---

*Built for humans who care about relationships but have goldfish memory. Your clients deserve to be remembered.*
