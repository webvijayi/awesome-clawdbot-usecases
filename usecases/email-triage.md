# 📧 Email Triage Autopilot

> Transform inbox chaos into organized action. Stop drowning in emails—let OpenClaw surface what matters.

---

## The Problem

The average professional receives 120+ emails daily, spending 2-3 hours just reading and sorting them. Most are noise (newsletters, notifications, CC chains), but buried in there are urgent requests, deadlines, and opportunities that get missed. You either live in your inbox anxiously or miss important things while trying to batch-check. Neither works.

---

## The Solution

OpenClaw continuously monitors your inbox, categorizes every email by urgency and importance, drafts responses to routine queries, extracts action items into your todo system, and delivers a concise morning briefing of what actually needs your attention. You check email once or twice a day, fully informed, and respond only to what matters.

**The magic:** OpenClaw learns YOUR priorities—who's important, what topics are urgent, which newsletters you actually read vs. ignore.

---

## Setup Guide

### Step 1: Install the Gmail Skill (5 minutes)

```bash
# Install the gmail skill
openclaw skill install gmail

# Authenticate (opens browser for OAuth)
openclaw skill gmail auth
```

For other providers:
- **Outlook:** `openclaw skill install outlook`
- **IMAP:** `openclaw skill install imap` (works with any provider)

### Step 2: Create Your Priority Rules File

Create `~/openclaw/email-rules.md`:

```markdown
# Email Priority Rules

## 🔴 URGENT (notify immediately)
- From: [boss@company.com, ceo@company.com, wife@family.com]
- Subject contains: "urgent", "asap", "emergency", "deadline today"
- Clients: *@bigclient.com, *@importantcustomer.io

## 🟠 IMPORTANT (morning digest, needs response today)
- Direct emails (not CC'd)
- From teammates: [team-list]
- Subject: "review needed", "your input", "decision required"
- Calendar invites requiring response

## 🟡 FYI (scan in digest, no action needed)
- CC'd on threads
- Automated reports I requested
- News from: [industry-newsletter@, techcrunch@]

## ⚪ NOISE (auto-archive, never show me)
- Marketing: "unsubscribe" in footer + not in approved list
- Social notifications: LinkedIn, Twitter, Facebook
- Automated: "do not reply", "noreply@"
- Promotions: "% off", "limited time", "deal"

## 📋 Auto-Response Templates
- PTO inquiries → "I'm out until [date], contact [backup] for urgent matters"
- Meeting requests → Draft acceptance with calendar link
- "Quick question" from strangers → Polite redirect to documentation/support
```

### Step 3: Set Up Your Todo Integration

Choose your system and create `~/openclaw/todo-config.md`:

```markdown
# Todo Integration

## System: Todoist (or: Things, Notion, Obsidian, plain markdown)

## Action Item Triggers
- "Can you..." / "Could you..." / "Please..." directed at me
- Explicit deadlines mentioned
- Commitments I made ("I'll send", "I'll review", "I'll follow up")

## Todo Format
- Task: [extracted action]
- Due: [deadline if mentioned, otherwise +2 days]
- Context: [email subject + sender]
- Link: [email URL for reference]
```

### Step 4: Configure HEARTBEAT.md

Add to your `~/openclaw/HEARTBEAT.md`:

```markdown
## 📧 Email Triage (check every 2-4 hours)
- [ ] Check unread emails against email-rules.md
- [ ] For URGENT: notify me immediately via Telegram
- [ ] For IMPORTANT: add to today's digest queue
- [ ] For NOISE: auto-archive (no notification)
- [ ] Extract action items → todo system
- [ ] Flag threads awaiting my response >48h for follow-up reminder
- [ ] Log summary to memory/email-triage.md
```

### Step 5: Set Up Cron Jobs

```bash
# Morning digest at 7:30 AM
openclaw cron add "30 7 * * *" "Deliver my email morning briefing. Read email-rules.md for priorities. Summarize: (1) urgent items, (2) important requiring response, (3) key FYIs. Be concise."

# Midday check at 1 PM (urgent only)
openclaw cron add "0 13 * * *" "Quick email scan: only alert me if there's something URGENT per email-rules.md. Otherwise stay quiet."

# End of day wrap-up at 5:30 PM
openclaw cron add "30 17 * * 1-5" "Email EOD: (1) threads I haven't responded to in 24h, (2) action items extracted today, (3) anything that arrived after morning digest that needs attention tomorrow."

# Weekly unsubscribe sweep (Sunday 10 AM)
openclaw cron add "0 10 * * 0" "Review emails marked NOISE this week. For senders appearing 3+ times: draft unsubscribe actions or add to permanent archive rules."
```

---

## Skills Needed

| Skill | Purpose | Install |
|-------|---------|---------|
| `gmail` or `outlook` or `imap` | Email access | `openclaw skill install gmail` |
| `todoist` / `notion` / `obsidian` | Action item sync | `openclaw skill install todoist` |
| Core OpenClaw | Cron, heartbeats, memory | Built-in |

**Optional enhancements:**
- `calendar` - Cross-reference meeting-related emails
- `slack` - Route work notifications appropriately

---

## Example Prompts

### 1. Morning Briefing (copy-paste ready)
```
Check my email from the last 12 hours. Categorize by: URGENT (need immediate action), IMPORTANT (respond today), FYI (interesting but no action). 

For each URGENT/IMPORTANT email give me:
- Sender + subject (one line)
- What they need from me (one line)  
- Suggested response or action

Skip the noise entirely. Be brutally concise.
```

### 2. Draft Responses for Common Queries
```
Review my unread emails. For any that are routine questions I've answered before (check my sent folder for patterns), draft responses. 

Show me: [Original ask] → [Draft response]

I'll approve/edit before you send anything.
```

### 3. Extract Action Items
```
Scan today's emails for anything that requires action from me. Create todos in this format:

- [ ] [Action] — from [Sender] re: [Subject] — due [date if mentioned, else "this week"]

Add these to my Todoist inbox. Don't duplicate if similar task exists.
```

### 4. Follow-Up Reminder
```
Find email threads where:
1. I'm the last sender AND no reply in 48+ hours
2. Someone asked me something AND I haven't responded in 24+ hours

For category 1: Draft polite follow-up bumps.
For category 2: Flag as "needs response" with quick summary of what they asked.
```

### 5. Unsubscribe Cleanup
```
Look at emails I've archived without reading in the past 2 weeks. Group by sender.

For senders with 5+ unread archived emails:
- Show me the sender and typical subject
- Find unsubscribe link if exists
- Recommend: unsubscribe, filter to trash, or keep

Don't auto-unsubscribe—just give me the list and I'll confirm.
```

---

## Cron Schedule

| Time | Cron Expression | What It Does |
|------|-----------------|--------------|
| 7:30 AM daily | `30 7 * * *` | Morning digest—full briefing of overnight emails |
| 1:00 PM daily | `0 13 * * *` | Midday scan—urgent items only |
| 5:30 PM weekdays | `30 17 * * 1-5` | EOD wrap—pending responses, tomorrow's priorities |
| 10:00 AM Sunday | `0 10 * * 0` | Weekly cleanup—unsubscribe recommendations |
| Every 2 hours | `0 */2 * * *` | Heartbeat check—urgent detection between scheduled runs |

**Customize for your schedule:**
- Night owl? Shift everything +3 hours
- Multiple time zones? Add a midday digest
- Weekend warrior? Remove the `1-5` restriction on EOD

---

## HEARTBEAT.md Config

Add this section to your `HEARTBEAT.md`:

```markdown
## 📧 Email Triage Autopilot

### Quick Check (every heartbeat)
- Scan for URGENT emails per ~/openclaw/email-rules.md
- If urgent found: notify immediately, don't wait for digest
- Log check timestamp to memory/heartbeat-state.json

### Periodic Tasks (track last-run, don't repeat within window)
- **Digest prep** (every 6h): Queue important emails for next scheduled digest
- **Action extraction** (every 4h): Scan new emails for todos
- **Follow-up check** (every 12h): Flag stale threads needing response

### State Tracking
```json
{
  "email": {
    "lastUrgentScan": 1703275200,
    "lastDigestPrep": 1703260800,
    "lastActionExtract": 1703250000,
    "lastFollowUpCheck": 1703200000,
    "pendingDigestItems": []
  }
}
```

### Quiet Hours
- 23:00-07:00: Only notify for URGENT from VIP senders
- Weekends: Batch everything into Monday morning digest unless truly urgent
```

---

## Expected Results

### Week 1
- ✅ Morning starts with clear briefing instead of inbox anxiety
- ✅ Urgent emails reach you in <30 minutes (vs. discovered hours later)
- ✅ 50% reduction in time spent in email client
- ✅ Zero "sorry for the late reply" situations

### Week 2-4
- ✅ Action items automatically flow to todo system
- ✅ Draft responses for 30-40% of routine emails
- ✅ Unsubscribed from 20+ noise sources
- ✅ Follow-up reminders prevent dropped balls

### Month 2+
- ✅ Email processing: 30 minutes/day (down from 2-3 hours)
- ✅ Inbox zero maintained automatically
- ✅ Priority rules refined to 95%+ accuracy
- ✅ You actually enjoy checking email (it's just the good stuff)

---

## Pro Tips

### 1. Train Your Triage
After each digest, tell OpenClaw about miscategorizations:
> "That email from [sender] should be IMPORTANT, not FYI. Update my rules."

### 2. VIP Sender List
Maintain an explicit list in `email-rules.md`. Anyone not on it gets lower priority by default.

### 3. Response Templates
Build a library of your common responses:
```markdown
## ~/openclaw/email-templates.md
### meeting-request
Happy to meet! Here's my calendar link: [link]. Pick any open slot.

### not-my-area  
Thanks for reaching out! This is actually handled by [team/person]. 
Looping them in / Try contacting them at [email].

### need-more-info
Thanks for the note. To help you better, could you clarify:
1. [Specific question]
2. [Timeline/urgency]
```

### 4. The Nuclear Option
For true inbox bankruptcy:
> "Archive everything older than 7 days that I haven't responded to. If it was important, they'll follow up."

---

## Troubleshooting

**"OpenClaw isn't catching urgent emails fast enough"**
- Reduce heartbeat interval for urgent scanning
- Add more specific triggers to URGENT rules
- Consider dedicated urgent-only cron every 30 minutes

**"Too many false positives in URGENT"**
- Tighten your VIP list
- Add negative patterns ("unsubscribe" → never urgent)
- Use sender reputation from past interactions

**"Action items are duplicating"**
- Add deduplication logic to todo prompt
- Use unique identifiers (email message ID)
- Check existing todos before adding

---

## Time Investment vs. Return

| Setup Task | Time | Ongoing Maintenance |
|------------|------|---------------------|
| Skill installation | 5 min | None |
| Priority rules | 10 min | 5 min/week refinement |
| Cron setup | 5 min | Occasional adjustment |
| HEARTBEAT config | 5 min | None |
| **Total** | **25 min** | **5 min/week** |

**ROI:** Save 1-2 hours daily = 7-14 hours/week = 30-60 hours/month

That's an entire work week back, every month. From 25 minutes of setup.

---

*Your inbox is a stream, not a bucket. Let OpenClaw fish out what matters.*
