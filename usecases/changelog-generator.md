# 📝 Changelog Generator

> Release notes in seconds. Never write them manually again.

---

## The Problem

Writing changelogs is boring but necessary. You forget what changed, PR descriptions are technical, and users need human-readable updates. Most changelogs are either skipped or rushed.

---

## The Solution

Clawdbot analyzes commits and PRs since last release, groups by type, writes user-friendly descriptions, and generates formatted changelogs automatically.

---

## Setup Guide

### Step 1: Install Git Skills

```bash
clawdbot skill install github
clawdbot skill install app-store-changelog
clawdbot skill install conventional-commits
```

### Step 2: Configure Format

Create `~/clawd/changelog/config.json`:

```json
{
  "format": "keepachangelog",
  "groupBy": ["feat", "fix", "perf", "docs"],
  "exclude": ["chore", "test", "ci"],
  "includeContributors": true
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `github` | Git history access |
| `app-store-changelog` | App Store format |
| `conventional-commits` | Commit parsing |

---

## Example Prompts

**Generate changelog:**
```
Generate changelog for release v2.0 from all commits since v1.9.
```

**App Store notes:**
```
Create App Store release notes for this version. Keep it user-friendly, highlight the top 3 improvements.
```

**Compare releases:**
```
What changed between v1.5 and v2.0? Summarize for the team.
```

---

## Cron Schedule

```
# Run on release tags automatically via GitHub Actions
```

---

## Expected Results

- Consistent, professional changelogs
- 30 minutes saved per release
- Users actually know what's new
