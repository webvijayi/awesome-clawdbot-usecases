# 📱 Social Media Scheduler

> Post once, publish everywhere. Stop juggling 5 apps to share the same content.

---

## The Problem

Managing social media presence across Twitter/X, LinkedIn, Bluesky, and Instagram means logging into each platform, reformatting content for each, and posting at optimal times. Most people either spend 2+ hours daily on this or let their accounts go stale. Both hurt growth.

---

## The Solution

OpenClaw takes one piece of content and automatically adapts it for each platform's format, character limits, and best practices. Schedule once, post everywhere at optimal times, and track what's working.

---

## Setup Guide

### Step 1: Install Required Skills (5 minutes)

```bash
openclaw skill install bluesky
openclaw skill install linkedin
openclaw skill install upload-post
```

### Step 2: Create Content Templates

Create `~/openclaw/social-templates/`:

```markdown
# Social Media Templates

## Thread Format (Twitter/X, Bluesky)
- Hook in first post (curiosity gap)
- Max 280 chars per post
- Number posts: 1/, 2/, etc.
- End with CTA

## LinkedIn Format
- Professional tone
- 1300 char limit
- Use line breaks for readability
- 3-5 relevant hashtags

## Instagram Caption
- Conversational tone
- Emoji-friendly
- 2200 char max
- 20-30 hashtags in first comment
```

### Step 3: Set Up Content Queue

Create `~/openclaw/content-queue.json`:

```json
{
  "queue": [],
  "posted": [],
  "schedule": {
    "twitter": ["09:00", "13:00", "17:00"],
    "linkedin": ["08:00", "12:00"],
    "bluesky": ["10:00", "15:00"]
  }
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `bluesky` | Post to Bluesky |
| `linkedin` | Post to LinkedIn |
| `upload-post` | Multi-platform posting |
| `twitter-api` | Twitter/X posting (optional) |

---

## Example Prompts

**Add content to queue:**
```
I just wrote a blog post about [topic]. Here's the main insight: [insight]. 
Create versions for Twitter thread, LinkedIn post, and Bluesky. Add to my content queue for this week.
```

**Repurpose existing content:**
```
Take my latest YouTube video transcript and create a Twitter thread, LinkedIn post, and 3 standalone tweets highlighting key points.
```

**Schedule batch posting:**
```
Review my content queue. Schedule all pending posts for optimal times this week. Show me the calendar.
```

**Analyze performance:**
```
Which of my posts from last week got the most engagement? What topics/formats worked best?
```

---

## Cron Schedule

```
0 8 * * 1-5    # 8 AM weekdays - post LinkedIn content
0 9 * * *      # 9 AM daily - post Twitter/X content  
0 15 * * *     # 3 PM daily - post Bluesky content
0 20 * * 0     # 8 PM Sunday - plan next week's content
```

---

## HEARTBEAT.md Config

```markdown
## Social Media
- [ ] Check content queue - any posts due today?
- [ ] Review engagement on yesterday's posts
- [ ] Alert if any scheduled post failed
```

---

## Expected Results

**Week 1:**
- 3x more posts across platforms
- Consistent posting schedule established

**Month 1:**
- 50%+ increase in social engagement
- 5+ hours/week saved on social media management
- Clear data on what content works

**Month 3:**
- Optimized posting times based on your audience
- Content library of repurposable posts
- Measurable follower growth
