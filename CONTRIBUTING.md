# Contributing

We want use cases that **actually get used**, not demos that collect dust.

## The Bar

Your use case must pass the **busy person test**:

1. ✅ Would a busy person (not an AI enthusiast) actually set this up?
2. ✅ Would they use it **daily** (not just try once)?
3. ✅ Does it directly **make money** OR **save 1+ hour/day**?

If you can't answer YES to all three, it's not ready.

## Format

Use this structure:

```markdown
# [Use Case Name]

> One-sentence description of the outcome

## The Problem

2-3 sentences on the pain point. Be specific about who has this problem.

## The Solution

How Clawdbot solves it. Focus on the workflow, not the tech.

## Setup Guide

Step-by-step instructions. A non-technical person should be able to follow.

1. First step
2. Second step
3. ...

## Skills Needed

List any Clawdbot skills required:
- `skill-name` - what it does

## Example Prompts

Copy-paste ready prompts:

\`\`\`
Prompt 1 here
\`\`\`

\`\`\`
Prompt 2 here
\`\`\`

## Cron Schedule

Exact cron expressions with explanations:

\`\`\`
0 8 * * 1-5  # 8 AM weekdays - morning digest
\`\`\`

## HEARTBEAT.md Config

What to add to HEARTBEAT.md:

\`\`\`markdown
- [ ] Check X every Y hours
\`\`\`

## Expected Results

Concrete outcomes:
- Save X hours/week
- Increase Y by Z%
- Never miss W again
```

## How to Submit

1. Fork this repo
2. Add your use case to `usecases/your-use-case.md`
3. Update README.md with your use case in the appropriate table
4. Open a PR with:
   - Clear title: `Add: [Use Case Name]`
   - Brief description of who benefits and how

## What We DON'T Want

- ❌ "Cool" demos that require 2 hours of setup
- ❌ Use cases that only AI enthusiasts would appreciate
- ❌ Workflows that require constant babysitting
- ❌ Theoretical benefits without concrete outcomes

## Questions?

Open an issue. We're happy to help refine your idea before you write it up.
