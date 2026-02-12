# 🎬 Video Content Pipeline

> From idea to upload-ready. Script, optimize, dominate the algorithm.

---

## The Problem

YouTube success requires more than good videos—it demands optimized titles, thumbnails that pop, SEO-rich descriptions, strategic tags, and engaging scripts. Creators spend hours on metadata that could go into content. Most never nail the algorithm because they're guessing, not analyzing.

---

## The Solution

Clawdbot handles the YouTube grind: researches trending topics, writes scroll-stopping scripts, generates thumbnail concepts, crafts SEO-optimized metadata, and analyzes what's working in your niche. You focus on filming; Clawdbot handles everything else.

---

## Setup Guide

### Step 1: Install Video Skills

```bash
clawdbot skill install youtube-summarizer  # Analyze competitor videos
clawdbot skill install brave-search        # Trend research
clawdbot skill install web-fetch           # Pull video data
clawdbot skill install local-whisper       # Transcription
```

### Step 2: Create Video Workspace

```bash
mkdir -p ~/clawd/youtube/{scripts,thumbnails,analytics,research}
```

Create `~/clawd/youtube/channel-profile.json`:

```json
{
  "channelName": "Your Channel",
  "niche": "Tech tutorials",
  "targetAudience": "Developers, 25-40",
  "videoStyle": "Educational with personality",
  "averageLength": "10-15 minutes",
  "uploadSchedule": "Tuesday, Friday",
  "competitors": [
    "@CompetitorChannel1",
    "@CompetitorChannel2"
  ]
}
```

### Step 3: Create Script Template

Create `~/clawd/youtube/script-template.md`:

```markdown
# Video Script: {title}

## Hook (0:00-0:30)
[Pattern interrupt - curiosity gap - preview value]

## Intro (0:30-1:00)
[Quick channel intro - why watch - what you'll learn]

## Main Content
### Section 1: [Topic]
- Key point
- Example/demo
- Transition

### Section 2: [Topic]
...

## Call to Action (Last 30 seconds)
[Engagement ask - subscribe - next video tease]

---
**Target Length:** X minutes
**Key Moments:** Timestamp markers for chapters
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `youtube-summarizer` | Analyze competitor content |
| `brave-search` | Research trending topics |
| `web-fetch` | Pull metadata from videos |
| `local-whisper` | Transcribe your recordings |
| `image` | Thumbnail concept analysis |

---

## Example Prompts

**Topic research:**
```
Research trending topics in [niche] on YouTube this week. Find gaps where demand is high but competition is low. Give me 5 video ideas with title options.
```

**Script writing:**
```
Write a script for a 12-minute YouTube video about [topic]. Hook viewers in the first 10 seconds, include 3 main sections, and end with engagement CTA. Match my energetic but educational style.
```

**Title optimization:**
```
I'm making a video about [topic]. Generate 10 title options optimized for CTR. Include curiosity gaps, numbers, and power words. Avoid clickbait that doesn't deliver.
```

**Thumbnail concepts:**
```
Suggest 5 thumbnail concepts for my video "[title]". Describe the visual elements, text overlay (max 3 words), facial expression, and color scheme that would maximize CTR.
```

**Description & tags:**
```
Write a YouTube description for my video "[title]". Include: hook paragraph, timestamps, links, 3 paragraphs with keywords, and generate 15-20 relevant tags.
```

**Competitor analysis:**
```
Analyze the top 5 performing videos about [topic] on YouTube. What hooks do they use? How long are they? What patterns can I learn from their titles and thumbnails?
```

---

## Video Metadata Template

```markdown
## Title Options (pick best CTR)
1. [Option with number]
2. [Option with curiosity gap]
3. [Option with "How to"]

## Description
[Hook paragraph with primary keyword]

📺 Timestamps:
0:00 - Intro
...

[2-3 paragraphs with secondary keywords]

🔗 Links mentioned:
...

## Tags
[tag1], [tag2], [tag3]...

## Thumbnail Notes
- Main visual: [description]
- Text overlay: "[2-3 words]"
- Expression: [surprised/excited/curious]
```

---

## Cron Schedule

```
0 9 * * 0      # Sunday - plan week's content
0 10 * * 1     # Monday - research & scripting
0 8 * * 2,5    # Upload days - final metadata prep
0 20 * * *     # Daily - check video performance
```

---

## Expected Results

**Week 1:**
- Scripts written in 30 min vs. 3 hours
- Better titles through A/B testing ideas

**Month 1:**
- 2x video output with same effort
- Higher CTR from optimized thumbnails/titles
- Consistent upload schedule

**Month 3:**
- Algorithm-friendly metadata on every video
- Clear content strategy based on data
- Growing channel with less burnout
