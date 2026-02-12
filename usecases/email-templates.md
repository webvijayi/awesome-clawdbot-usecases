# ✉️ Context-Aware Email Templates

> Draft perfect emails in seconds. Right tone, right context, right every time.

---

## The Problem

You write the same types of emails over and over: follow-ups, introductions, status updates, apologies. Each takes 10-15 minutes as you stare at a blank screen. Your tone varies wildly based on mood, and you forget what you discussed in previous threads. Worse, you delay sending important emails because drafting feels like work.

---

## The Solution

OpenClaw maintains your email templates, adapts them to context, matches tone to recipient and situation, and suggests responses based on conversation history. Tell it what you need to say—it handles how to say it professionally.

---

## Setup Guide

### Step 1: Install Email Skills

```bash
openclaw skill install gmail          # Gmail integration
openclaw skill install imap           # Generic email support
openclaw skill install prompt-library # Template management
```

### Step 2: Define Your Voice

Create `~/openclaw/email/voice.md`:

```markdown
# My Email Voice

## Default Tone
- Professional but warm
- Direct, not verbose
- Use contractions (don't, won't, I'm)
- Sign off: "Best," or "Thanks,"

## Formal (clients, executives)
- More structured paragraphs
- No contractions
- Sign off: "Best regards," or "Sincerely,"

## Casual (teammates, friends)
- Shorter sentences
- Emoji okay sparingly
- Sign off: "Cheers," or just name
```

### Step 3: Create Template Library

Create `~/openclaw/email/templates/`:

```markdown
# follow-up.md
Subject: Following up on [topic]
Trigger: 3-5 days after no response
Include: Reference to original email, new value-add, clear ask

# introduction.md
Subject: Introduction: [Person A] <> [Person B]  
Include: Why connecting them, what each does, suggested next step

# status-update.md
Subject: Update: [Project] - [Week/Date]
Include: Progress, blockers, next steps, any asks

# apology.md
Subject: Apologies for [issue]
Include: Acknowledge mistake, explain (briefly), remediation, prevent future
```

### Step 4: Set Up Response Suggestions

Create `~/openclaw/email/rules.md`:

```markdown
# Response Rules

## Auto-suggest reply when:
- Email marked important/urgent
- From VIP contacts (defined in contacts.json)
- Contains question requiring response
- Follow-up overdue by 48+ hours

## Tone adjustments:
- Complaints: Extra empathetic, solution-focused
- Good news: Enthusiastic, celebratory
- Requests: Clear, structured, with timeline
- Bad news: Direct but kind, offer alternatives
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `gmail` | Read/send emails |
| `imap` | Generic email provider support |
| `prompt-library` | Store and retrieve templates |

---

## Example Prompts

**Draft from scratch:**
```
Write a follow-up email to John about the proposal I sent last Tuesday. 
Keep it friendly but create some urgency—we need a decision by Friday.
```

**Tone adjustment:**
```
Rewrite this email to be more formal. It's going to the CEO:
[paste draft]
```

**Suggest response:**
```
Here's an email I just received. Draft a response:
[paste email]
```

**Template usage:**
```
Use my introduction template to connect Sarah (marketing director at TechCorp) 
with Mike (our sales lead). Sarah is looking for marketing automation tools.
```

**Batch drafts:**
```
I need to send status updates to 5 clients. Here's what happened this week: [summary]
Draft personalized updates for each based on their specific projects.
```

---

## Cron Schedule

```
0 9 * * *      # 9 AM - Review inbox, suggest responses to priority emails
0 14 * * *     # 2 PM - Check for overdue follow-ups, draft reminders
0 17 * * 5     # 5 PM Friday - Draft any pending status updates
```

---

## HEARTBEAT.md Config

```markdown
## Email
- [ ] Any urgent emails needing response?
- [ ] Follow-ups overdue by 48+ hours?
- [ ] VIP contacts waiting for reply?
```

---

## Expected Results

**Week 1:**
- Template library established
- 50% faster email drafting

**Month 1:**
- Consistent professional tone across all emails
- Zero dropped follow-ups
- Inbox feels manageable

**Ongoing:**
- Email becomes effortless
- Relationships improve from timely, thoughtful responses
- 5+ hours/week saved on email drafting
