# 🔍 PR Review Assistant

> Never merge buggy code again. Get thorough reviews in minutes, not days.

---

## The Problem

Code reviews are bottlenecks. PRs sit for days waiting for busy teammates. When reviews do happen, they're often rushed, missing bugs that slip into production. Junior devs don't get the learning feedback they need.

---

## The Solution

OpenClaw automatically reviews every PR: checks for bugs, security issues, style violations, and suggests improvements. Human reviewers can focus on architecture and business logic while OpenClaw handles the tedious stuff.

---

## Setup Guide

### Step 1: Install Skills

```bash
openclaw skill install github
openclaw skill install github-pr
openclaw skill install conventional-commits
```

### Step 2: Configure Review Rules

Create `~/openclaw/pr-review/rules.md`:

```markdown
# PR Review Checklist

## Always Check
- [ ] No hardcoded secrets/credentials
- [ ] No console.log/print statements left in
- [ ] Error handling present
- [ ] Input validation for user data
- [ ] SQL injection prevention
- [ ] XSS prevention

## Code Quality
- [ ] Functions under 50 lines
- [ ] No deep nesting (max 3 levels)
- [ ] Meaningful variable names
- [ ] DRY - no copy-pasted blocks

## Tests
- [ ] New code has tests
- [ ] Edge cases covered
- [ ] Tests actually test something meaningful

## Documentation
- [ ] Complex logic has comments
- [ ] Public APIs have docstrings
- [ ] README updated if needed
```

### Step 3: Set Up GitHub Webhook (Optional)

For automatic reviews on new PRs, set up a webhook or use GitHub Actions.

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `github` | GitHub API access |
| `github-pr` | PR-specific operations |
| `conventional-commits` | Commit message validation |

---

## Example Prompts

**Review a PR:**
```
Review PR #123 in repo [owner/repo]. Focus on security, performance, and code quality.
```

**Batch review:**
```
Show me all open PRs in [repo] that haven't been reviewed in 2+ days. Give me a summary of each.
```

**Learn from feedback:**
```
What are the most common issues you've found in our PRs this month? Create a team guidelines doc.
```

**Pre-submit check:**
```
I'm about to submit a PR with these changes: [paste diff]. Any issues I should fix first?
```

---

## Cron Schedule

```
*/15 * * * *   # Every 15 min - check for new PRs to review
0 9 * * 1-5    # 9 AM weekdays - PR aging report
0 17 * * 5     # 5 PM Friday - weekly PR metrics
```

---

## HEARTBEAT.md Config

```markdown
## PR Reviews
- [ ] Any PRs open > 48 hours without review?
- [ ] Any PRs with failing checks that need attention?
- [ ] New PRs in last hour needing initial review?
```

---

## Expected Results

**Week 1:**
- All PRs reviewed within 2 hours of submission
- Common issues caught automatically

**Month 1:**
- 40% fewer bugs reaching production
- Junior devs improving faster with consistent feedback
- Review bottleneck eliminated

**Month 3:**
- Team coding standards internalized
- Code quality metrics trending up
- Faster shipping with confidence
