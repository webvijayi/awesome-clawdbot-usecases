# 🛸 Personal Tech Radar

> Track what matters in tech. Skip the hype, catch the signal.

---

## The Problem

Technology moves fast. New frameworks weekly, security vulnerabilities daily, paradigm shifts quarterly. You can't read everything, but you can't afford to miss critical updates to tools you depend on. Most "tech news" is hype—you need signal, not noise.

---

## The Solution

Clawdbot maintains your personal tech radar: tracks technologies you use, monitors for security issues, evaluates new tools against your stack, and alerts you only when something genuinely matters.

---

## Setup Guide

### Step 1: Install Monitoring Skills

```bash
clawdbot skill install github
clawdbot skill install hn-digest
clawdbot skill install cve-search
clawdbot skill install brave-search
clawdbot skill install context7
clawdbot skill install miniflux
```

### Step 2: Define Your Stack

Create `~/clawd/tech-radar/stack.json`:

```json
{
  "languages": ["TypeScript", "Python", "Rust"],
  "frameworks": ["Next.js", "FastAPI", "Tokio"],
  "databases": ["PostgreSQL", "Redis", "Clickhouse"],
  "infrastructure": ["Kubernetes", "Docker", "Terraform"],
  "tools": ["VS Code", "GitHub Actions", "Datadog"],
  "criticalDependencies": [
    "openssl",
    "node",
    "python",
    "postgresql"
  ]
}
```

### Step 3: Configure Watch Lists

Create `~/clawd/tech-radar/watchlist.md`:

```markdown
# Tech Watch List

## Adopt (using in production)
- Next.js 14 - watch for breaking changes
- PostgreSQL 16 - monitor security advisories
- Kubernetes 1.29 - deprecation warnings

## Trial (evaluating)
- Bun - JavaScript runtime alternative
- Turso - SQLite at the edge
- Deno 2.0 - TypeScript runtime

## Assess (keeping eye on)
- WebAssembly components
- AI code assistants (beyond Copilot)
- Edge computing frameworks

## Hold (avoid for now)
- Bleeding-edge ORMs
- Unproven serverless databases
```

### Step 4: Set Security Priorities

Create `~/clawd/tech-radar/security.md`:

```markdown
# Security Monitoring

## Critical (alert immediately)
- CVEs in: openssl, node, python, postgresql
- Any CVSS 9.0+ in our stack
- Supply chain attacks on npm/PyPI packages we use

## High (daily digest)
- CVEs in frameworks we use
- Authentication/authorization vulnerabilities
- Data exposure risks

## Medium (weekly summary)
- Dependencies of dependencies
- Theoretical attacks
- Best practice updates
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `github` | Release monitoring, repo activity |
| `hn-digest` | Developer community sentiment |
| `cve-search` | Security vulnerability tracking |
| `brave-search` | Tech news and updates |
| `context7` | Framework documentation changes |
| `miniflux` | RSS feeds for blogs/changelogs |

---

## Example Prompts

**Security check:**
```
Any new CVEs affecting my stack in the last 7 days? Prioritize by severity and our exposure.
```

**Framework update:**
```
What's new in Next.js 15? Breaking changes? Should I upgrade or wait?
```

**Tool evaluation:**
```
Compare Bun vs Node.js for my use case. Maturity, performance, ecosystem, risks.
```

**Deprecation watch:**
```
What's being deprecated in my stack? What do I need to migrate before it breaks?
```

**Trend analysis:**
```
What are the emerging technologies in [area] worth watching? Filter out the hype.
```

**Dependency audit:**
```
Audit my package.json for outdated or vulnerable dependencies. Prioritize what to update.
```

---

## Cron Schedule

```
0 7 * * *      # 7 AM daily - security CVE check
0 9 * * 1      # Monday 9 AM - weekly tech digest
0 10 1 * *     # 1st of month - full radar update
*/15 * * * *   # Every 15 min - critical CVE monitor
```

---

## HEARTBEAT.md Config

```markdown
## Tech Radar
- [ ] Critical CVEs in last 6 hours?
- [ ] Major releases for my frameworks?
- [ ] Trending on HN relevant to my stack?
- [ ] GitHub releases for watched repos?
```

---

## Radar Format

### Monthly Tech Radar Report
```markdown
# Tech Radar - [MONTH YEAR]

## 🟢 Adopt
Technologies ready for production use:
- [Tool] - [Why it's ready]

## 🟡 Trial  
Worth investing time to evaluate:
- [Tool] - [What's promising]

## 🔵 Assess
Watch but don't invest yet:
- [Tool] - [Why it's interesting]

## 🔴 Hold
Avoid or phase out:
- [Tool] - [Why to avoid]

## ⚠️ Security Alerts
- [CVE-XXXX] - [Impact and action]

## 📦 Upgrade Recommendations
- [Package] v[X] → v[Y] - [Priority: Critical/High/Medium]
```

---

## Expected Results

**Week 1:**
- Complete stack inventory
- Security baseline established
- Alert thresholds configured

**Month 1:**
- Zero surprise vulnerabilities
- Informed upgrade decisions
- Early awareness of deprecations

**Month 3:**
- Technology choices backed by data
- Reduced tech debt from proactive updates
- Team trusts radar for technology decisions
