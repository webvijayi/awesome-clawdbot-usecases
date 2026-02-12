# 💸 AI Cost Tracker

> Know exactly what you're spending on AI. No surprises, just optimization.

---

## The Problem

AI API costs add up fast and unpredictably. You're using Claude, GPT-4, Gemini across different tools and projects. The bill arrives and you have no idea what drove the spike or how to optimize.

---

## The Solution

OpenClaw tracks your AI usage across all providers, alerts on unusual spending, identifies cost optimization opportunities, and helps you choose the right model for each task.

---

## Setup Guide

### Step 1: Install Tracking Skills

```bash
openclaw skill install claude-code-usage
openclaw skill install codex-quota
openclaw skill install minimax-usage
```

### Step 2: Configure Providers

Create `~/openclaw/ai-costs/providers.json`:

```json
{
  "providers": [
    {
      "name": "Anthropic",
      "budgetMonthly": 100,
      "alertThreshold": 80
    },
    {
      "name": "OpenAI",
      "budgetMonthly": 50,
      "alertThreshold": 80
    },
    {
      "name": "Google",
      "budgetMonthly": 30,
      "alertThreshold": 80
    }
  ],
  "totalBudget": 200
}
```

### Step 3: Set Up Cost Rules

Create `~/openclaw/ai-costs/rules.md`:

```markdown
# AI Cost Optimization Rules

## Model Selection
- Simple tasks: Use cheapest model (GPT-3.5, Claude Instant)
- Complex reasoning: Use best model
- Bulk processing: Batch API when available

## Alerts
- Daily spend > $10: Warning
- Weekly spend > $40: Alert
- Approaching 80% of budget: Alert

## Review Weekly
- Highest cost tasks
- Potential model downgrades
- Unused subscriptions
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `claude-code-usage` | Claude/Anthropic usage |
| `codex-quota` | OpenAI Codex usage |
| `minimax-usage` | MiniMax usage |

---

## Example Prompts

**Daily check:**
```
What's my AI spend today across all providers? Any unusual spikes?
```

**Optimization analysis:**
```
Analyze my AI usage this week. Where am I overspending? Which tasks could use cheaper models?
```

**Budget planning:**
```
Based on my usage patterns, what should my monthly AI budget be? Am I using the right models for each task?
```

**Provider comparison:**
```
For [task type], compare costs between Claude, GPT-4, and Gemini. Which gives best value?
```

---

## Cron Schedule

```
0 20 * * *     # 8 PM - daily spend summary
0 9 * * 1      # Monday 9 AM - weekly cost report
0 0 1 * *      # 1st of month - monthly analysis
*/30 * * * *   # Every 30 min - budget alert check
```

---

## Expected Results

**Week 1:**
- Full visibility into AI spending
- Budget alerts configured

**Month 1:**
- 20-30% cost reduction through optimization
- No surprise bills
- Clear per-project cost attribution

**Ongoing:**
- Predictable AI costs
- Informed model selection
- Budget always under control
