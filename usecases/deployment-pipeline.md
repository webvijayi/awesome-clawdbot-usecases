# 🚀 Deployment Pipeline Manager

> Ship with confidence. Automated deployments done right.

---

## The Problem

Manual deployments are error-prone and stressful. You forget steps, environments drift, and rollbacks are chaotic. CI/CD tools help but still need babysitting.

---

## The Solution

OpenClaw orchestrates deployments: runs pipelines, monitors progress, handles rollbacks, and notifies the right people. You push code, it handles the rest.

---

## Setup Guide

### Step 1: Install DevOps Skills

```bash
openclaw skill install github
openclaw skill install vercel-deploy
openclaw skill install dokploy
openclaw skill install cloudflare
```

### Step 2: Configure Environments

Create `~/openclaw/deploy/config.json`:

```json
{
  "environments": {
    "staging": {
      "autoDeploy": true,
      "branch": "develop"
    },
    "production": {
      "autoDeploy": false,
      "branch": "main",
      "requireApproval": true
    }
  }
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `github` | CI/CD integration |
| `vercel-deploy` | Vercel deployments |
| `dokploy` | Self-hosted deploys |
| `cloudflare` | Edge deployments |

---

## Example Prompts

**Deploy:**
```
Deploy latest main to production. Show me the diff from current.
```

**Status check:**
```
What's the deployment status? Any failed builds today?
```

**Rollback:**
```
Production is broken. Rollback to the previous version immediately.
```

---

## Cron Schedule

```
*/5 * * * *    # Monitor deployment health
0 9 * * 1      # Monday - deployment report
```

---

## Expected Results

- Zero-stress deployments
- Instant rollback capability
- Full deployment visibility
