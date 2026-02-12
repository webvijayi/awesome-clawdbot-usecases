# 🎨 Design Feedback Assistant

> Get instant UI/UX reviews without waiting for stakeholders. Ship better designs, faster.

---

## The Problem

Designers often work in isolation—you finish a design, share it, and wait days for feedback. When feedback comes, it's scattered across Slack, email, and Figma comments. Accessibility issues get caught in QA (too late). Design systems grow inconsistent because documentation is tedious.

---

## The Solution

OpenClaw provides instant, structured design feedback: reviews UI screenshots for usability issues, audits accessibility compliance, compares against your design system, and helps document components. Get a fresh perspective anytime, not just during review meetings.

---

## Setup Guide

### Step 1: Install Design Skills

```bash
openclaw skill install browser     # Screenshot and visual analysis
openclaw skill install web-fetch   # Reference design patterns
openclaw skill install image       # Image analysis capabilities
```

### Step 2: Create Design Workspace

```bash
mkdir -p ~/openclaw/design/{reviews,components,accessibility}
```

Create `~/openclaw/design/design-system.md`:

```markdown
# Design System Reference

## Colors
- Primary: #2563EB (Blue 600)
- Secondary: #7C3AED (Violet 600)
- Success: #059669 (Green 600)
- Warning: #D97706 (Amber 600)
- Error: #DC2626 (Red 600)

## Typography
- Headings: Inter, semi-bold
- Body: Inter, regular, 16px base
- Line height: 1.5 for body text

## Spacing
- Base unit: 4px
- Common: 8, 16, 24, 32, 48px

## Components
- Buttons: rounded-lg, min-height 44px
- Cards: rounded-xl, shadow-sm
- Inputs: border-gray-300, focus:ring-2
```

### Step 3: Set Up Review Checklist

Create `~/openclaw/design/review-checklist.md`:

```markdown
# UI/UX Review Checklist

## Usability
- [ ] Clear visual hierarchy
- [ ] Obvious primary action
- [ ] Consistent alignment
- [ ] Adequate white space
- [ ] Readable text contrast

## Accessibility
- [ ] Color contrast ≥ 4.5:1 (text)
- [ ] Touch targets ≥ 44x44px
- [ ] Focus states visible
- [ ] Alt text for images
- [ ] Screen reader friendly

## Consistency
- [ ] Matches design system colors
- [ ] Correct typography scale
- [ ] Standard component patterns
- [ ] Consistent iconography
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `browser` | Capture screenshots, inspect live sites |
| `image` | Analyze design screenshots |
| `web-fetch` | Pull design pattern references |
| `figma-api` | Connect to Figma files (optional) |

---

## Example Prompts

**UI review:**
```
Review this screenshot of my dashboard design. Check for visual hierarchy, alignment issues, and usability problems. Be specific about what to fix.
[attach screenshot]
```

**Accessibility audit:**
```
Audit this design for WCAG 2.1 AA compliance. Check color contrast, touch targets, and focus states. List all issues with severity ratings.
[attach screenshot]
```

**Design system check:**
```
Compare this component against my design system in ~/openclaw/design/design-system.md. Note any deviations from our standards.
```

**Component documentation:**
```
Document this button component for our design system. Include: variants, states, spacing specs, usage guidelines, and code examples.
```

**Competitor analysis:**
```
Visit [competitor URL] and analyze their checkout flow. What UX patterns are they using that we should consider? What do they do poorly?
```

**Live site audit:**
```
Go to [URL] and take screenshots of the homepage. Review for mobile responsiveness, load performance indicators, and UX issues.
```

---

## Review Output Format

```markdown
## Design Review: [Screen Name]

### ✅ What's Working
- Clear primary CTA
- Good use of whitespace
- Consistent typography

### ⚠️ Issues Found

**High Priority:**
1. [Issue] - [Impact] - [Recommendation]

**Medium Priority:**
1. [Issue] - [Recommendation]

### 📊 Accessibility Score: 7/10
- Contrast: Pass
- Touch targets: 2 failures
- Focus states: Missing
```

---

## Cron Schedule

```
0 10 * * 1     # Monday - weekly design review batch
0 14 * * 3     # Wednesday - accessibility spot check
0 9 * * 5      # Friday - design system audit
```

---

## Expected Results

**Week 1:**
- Catch 5-10 issues before stakeholder review
- Faster feedback loop on iterations

**Month 1:**
- Consistent accessibility compliance
- Design system documentation up to date
- 50% fewer revision rounds

**Month 3:**
- Higher quality designs shipping
- Reduced QA accessibility bugs
- Living design system documentation
