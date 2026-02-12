# 📔 Daily Journaling System

> Reflection made effortless. Capture today, understand tomorrow.

---

## The Problem

Journaling is valuable but hard to maintain. Staring at a blank page is intimidating. You forget by evening what happened in the morning. And past journals are rarely reviewed, making the practice feel pointless.

---

## The Solution

OpenClaw prompts you with specific questions, captures quick responses throughout the day, and synthesizes patterns over time. Low friction, high insight.

---

## Setup Guide

### Step 1: Install Journaling Skills

```bash
openclaw skill install obsidian-conversation-backup  # or notion, reflect
openclaw skill install todoist
```

### Step 2: Create Journal Templates

Create `~/openclaw/journal/templates.md`:

```markdown
# Morning Questions (5 min)
- What's my ONE priority today?
- What am I grateful for?
- What would make today great?

# Evening Questions (5 min)
- What went well today?
- What did I learn?
- What would I do differently?

# Weekly Review (Sunday)
- Wins this week
- Challenges faced
- Focus for next week
- Pattern I noticed

# Monthly Themes
- What defined this month?
- Progress on goals
- Relationships status
- Energy/health check
```

### Step 3: Configure Prompts

Create `~/openclaw/journal/config.json`:

```json
{
  "morningTime": "07:00",
  "eveningTime": "21:00",
  "weeklyDay": "Sunday",
  "monthlyDay": 1,
  "storage": "~/openclaw/journal/entries/",
  "format": "markdown"
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `obsidian-conversation-backup` | Note storage |
| `reflect` | Reflection notes |
| `notion` | Alternative storage |
| `todoist` | Task integration |

---

## Example Prompts

**Morning entry:**
```
Good morning journal time. Ready for my 3 questions.
```

**Quick capture:**
```
Journal: Had a breakthrough conversation with [person] about [topic]. Don't want to forget this.
```

**Evening reflection:**
```
End of day. Let's do my evening reflection.
```

**Pattern search:**
```
Looking at the past month of journals, what patterns do you see in my mood, productivity, and gratitude entries?
```

---

## Cron Schedule

```
0 7 * * *      # 7 AM - morning journal prompt
0 21 * * *     # 9 PM - evening reflection
0 10 * * 0     # Sunday 10 AM - weekly review
0 9 1 * *      # 1st of month - monthly review
```

---

## Expected Results

**Week 1:**
- Daily journaling habit started
- Low-friction entry system

**Month 1:**
- 30 days of entries
- First pattern insights emerge
- Improved self-awareness

**Month 3:**
- Sustainable habit
- Valuable personal data
- Better decisions through reflection
