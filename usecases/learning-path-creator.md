# 📚 Learning Path Creator

> Learn anything systematically. No more random YouTube binges.

---

## The Problem

Self-directed learning is chaotic. You want to learn [skill] but don't know where to start, what order to learn things, or when you've "finished." Most people bounce between resources without a plan.

---

## The Solution

OpenClaw creates personalized curricula: assesses your starting point, finds the best resources, creates a structured path, tracks progress, and adjusts when you struggle or excel.

---

## Setup Guide

### Step 1: Install Learning Skills

```bash
openclaw skill install context7
openclaw skill install literature-review
openclaw skill install youtube-summarizer
```

### Step 2: Define Learning Goals

Create `~/openclaw/learning/goals.json`:

```json
{
  "currentGoal": {
    "topic": "Machine Learning",
    "level": "beginner",
    "timeCommitment": "5 hours/week",
    "deadline": "3 months",
    "learningStyle": "video + hands-on projects"
  },
  "preferences": {
    "freeResourcesPreferred": true,
    "languages": ["English"],
    "formats": ["video", "interactive", "book"]
  }
}
```

### Step 3: Create Progress Tracker

Create `~/openclaw/learning/progress.md`:

```markdown
# Learning Progress

## Current: Machine Learning Fundamentals

### Completed
- [x] Module 1: Linear algebra basics
- [x] Module 2: Statistics refresher

### In Progress
- [ ] Module 3: Python for ML (60%)

### Up Next
- [ ] Module 4: Supervised learning

### Notes
- Struggling with: gradient descent intuition
- Should review: matrix multiplication
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `context7` | Library documentation |
| `literature-review` | Academic resources |
| `youtube-summarizer` | Video content |
| `brave-search` | Resource discovery |

---

## Example Prompts

**Create curriculum:**
```
I want to learn [topic] from scratch. I can commit 5 hours per week for 3 months. Create a learning path with the best free resources.
```

**Daily practice:**
```
I have 45 minutes to study. What should I work on today based on my learning plan?
```

**Stuck on concept:**
```
I don't understand [concept]. Explain it differently and find additional resources that explain it well.
```

**Progress check:**
```
Review my learning progress. Am I on track? What should I adjust?
```

---

## Cron Schedule

```
0 7 * * *      # 7 AM - daily learning reminder
0 20 * * 0     # 8 PM Sunday - weekly progress review
0 10 1 * *     # 1st of month - curriculum adjustment
```

---

## Expected Results

**Week 1:**
- Clear learning path created
- Know exactly what to study

**Month 1:**
- Steady progress visible
- Concepts building on each other
- No more resource paralysis

**Month 3:**
- Measurable skill acquisition
- Portfolio of completed projects
- Ready for next learning goal
