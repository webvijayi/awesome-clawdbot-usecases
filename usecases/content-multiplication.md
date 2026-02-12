# Content Multiplication Engine

> Turn one piece of content into 10+ platform-specific posts automatically.

## The Problem

Creating content for one platform is hard enough—repurposing it for Twitter, LinkedIn, Instagram, newsletters, and Reddit is a time sink that kills consistency. Most creators either post the same thing everywhere (which performs poorly) or spend hours manually reformatting, losing momentum and burning out. The result? Great content stuck on one platform while your audience waits elsewhere.

## The Solution

OpenClaw acts as your always-on content repurposing assistant. Drop a blog post URL, paste a video transcript, or share podcast notes—OpenClaw transforms it into platform-native content for every channel you care about. It understands each platform's style: Twitter threads with hooks, LinkedIn thought-leadership angles, Instagram carousel concepts, punchy newsletter snippets, and Reddit-appropriate discussion starters. Set it up once, and your content multiplies while you sleep.

## Setup Guide

### Step 1: Create Your Content Workspace (2 minutes)

```bash
mkdir -p ~/content-engine/{input,output,templates}
```

Create a simple input structure in `~/content-engine/input/`:
- Drop source files here (`.md`, `.txt`, or just URLs)

### Step 2: Create Platform Templates (5 minutes)

Create `~/content-engine/templates/platforms.md`:

```markdown
# Platform Guidelines

## Twitter/X Thread
- Hook in first tweet (curiosity gap or bold statement)
- 5-10 tweets max, each standalone valuable
- End with CTA or callback to first tweet
- Use line breaks for readability
- No hashtags in thread, maybe 1-2 at end

## LinkedIn Post
- First line is the hook (before "see more")
- Personal angle or story lead-in
- Insights with white space between points
- End with question to drive comments
- 1300-1500 chars ideal
- 3-5 relevant hashtags at bottom

## Instagram Caption
- Hook in first line (emoji optional)
- Story or value in 2-3 short paragraphs  
- CTA: save, share, comment prompt
- Hashtags: 20-30 relevant ones in first comment (provide separately)
- Carousel slide concepts if applicable

## Newsletter Snippet
- TL;DR in 2-3 sentences
- Key insight or quote pullout
- "Read more" hook with link placeholder
- Keep under 150 words

## Reddit Post
- Title: Question or discussion-starter format
- No self-promotion tone
- Add genuine value first
- Mention source naturally at end
- Adapt to subreddit culture (specify which sub)
```

### Step 3: Add to TOOLS.md (1 minute)

Add this to your `~/openclaw/TOOLS.md`:

```markdown
### Content Engine
- Input folder: ~/content-engine/input/
- Output folder: ~/content-engine/output/
- Templates: ~/content-engine/templates/platforms.md
- Default platforms: Twitter, LinkedIn, Newsletter
```

### Step 4: Configure HEARTBEAT.md (2 minutes)

Add this section to your `~/openclaw/HEARTBEAT.md`:

```markdown
### Content Multiplication Check
- [ ] Check ~/content-engine/input/ for new files
- [ ] If found: Process through content engine, save outputs to ~/content-engine/output/[date]-[title]/
- [ ] Notify me with summary of what was generated
```

### Step 5: Test It (2 minutes)

Drop a test file in `~/content-engine/input/test-post.md`:

```markdown
# Source: Blog Post
URL: https://yourblog.com/my-latest-post
Title: 5 Lessons from Building in Public

## Key Points
- Lesson 1: Share failures, not just wins
- Lesson 2: Consistency beats perfection
- Lesson 3: Engage with every comment early
- Lesson 4: Your audience knows what they want—ask them
- Lesson 5: Building in public is marketing that doesn't feel like marketing
```

Then tell OpenClaw: "Process my new content in the input folder"

## Skills Needed

| Skill | Purpose | Required? |
|-------|---------|-----------|
| **File System** | Read inputs, write outputs | ✅ Yes (built-in) |
| **Web Fetch** | Pull content from blog URLs | ✅ Yes (built-in) |
| **Twitter/X** | Post threads directly | ⚡ Optional |
| **LinkedIn** | Post directly | ⚡ Optional |
| **Telegram/Discord** | Receive notifications | ✅ Yes (one channel) |

**Minimum setup:** Just file system + one messaging channel. You can copy-paste outputs manually.

**Power setup:** Add social media skills to post directly from OpenClaw.

## Example Prompts

### 1. Quick Single-Source Multiplication

```
Take this blog post and create platform versions:
https://myblog.com/latest-article

Generate:
- Twitter thread (8-10 tweets)
- LinkedIn post
- Newsletter teaser (100 words)

Save all outputs to ~/content-engine/output/
```

### 2. Video/Podcast Transcript Processing

```
Here's my latest podcast transcript:

[paste transcript or provide file path]

Extract the 3 most quotable moments and turn each into:
1. A standalone tweet
2. A LinkedIn insight post
3. An Instagram carousel concept (5-7 slides)

Focus on actionable advice, not fluff.
```

### 3. Batch Processing with Priorities

```
Process all files in ~/content-engine/input/

For each source, prioritize:
1. Twitter thread (always)
2. LinkedIn post (if professional/business topic)
3. Reddit post (if technical or niche interest)

Skip Instagram unless the content is visual or lifestyle.
Name outputs: [platform]-[source-title].md
```

### 4. Thread-First Deep Dive

```
Turn this into a Twitter thread that could go viral:

[paste key insight or link]

Requirements:
- Strong hook that creates curiosity
- Each tweet delivers standalone value
- Include 1 contrarian take
- End with a question or CTA to follow
- Suggest 3 quote-tweet variations I can use to resurface it later
```

### 5. Full Content Suite with Calendar

```
I just published: [URL]

Create my full content suite:
1. Twitter thread (post today)
2. LinkedIn post (schedule for tomorrow morning)
3. Newsletter snippet (for Sunday send)
4. Reddit discussion post for r/[subreddit] (wait 2 days)
5. Instagram carousel concept (weekend content)

Give me a posting calendar with optimal times.
```

## Cron Schedule

### Option A: Daily Morning Check (Recommended)

```bash
# Check for new content every morning at 8 AM
0 8 * * * cron:content-check Read ~/content-engine/input/ for any new files added in the last 24 hours. Process each through the content multiplication workflow and save outputs. Send me a summary.
```

### Option B: Twice Daily (Active Creators)

```bash
# Morning content processing
0 8 * * * cron:content-morning Process any new files in ~/content-engine/input/ and notify me what's ready to post.

# Evening review of what performed well
0 18 * * * cron:content-review Check my recent posts (if social skills installed). Suggest which content to repurpose further based on engagement.
```

### Option C: Publish Day Automation

```bash
# If you publish blogs on specific days (e.g., Tuesday/Thursday)
0 9 * * 2,4 cron:blog-multiply Check for new blog posts. Run full content multiplication suite. Queue outputs for the week.
```

### Explanation of Cron Expressions

| Expression | Meaning |
|------------|---------|
| `0 8 * * *` | 8:00 AM every day |
| `0 8 * * 1-5` | 8:00 AM weekdays only |
| `0 9 * * 2,4` | 9:00 AM on Tuesday and Thursday |
| `0 */4 * * *` | Every 4 hours |

## HEARTBEAT.md Config

Add this block to your `HEARTBEAT.md`:

```markdown
## 📝 Content Multiplication Engine

### Every Heartbeat
- [ ] Quick check: Any new files in `~/content-engine/input/`?
  - If YES: Process immediately and notify
  - If NO: Continue to other checks

### Daily (once per day, morning preferred)
- [ ] Review `~/content-engine/output/` for unpublished content
- [ ] If content is 3+ days old and unused, remind me
- [ ] Suggest "resurrection" ideas for older performing content

### Weekly (Sundays)
- [ ] Summarize: Content created this week vs published
- [ ] Identify gaps: Which platforms did I neglect?
- [ ] Suggest: One piece of old content worth repurposing

### Content Quality Rules
- Always read the full source before generating
- Match platform voice (casual Twitter, professional LinkedIn)
- Never duplicate exact text across platforms
- Flag if source material is too thin for multiplication
```

## Expected Results

### Immediate (Week 1)
- ⏱️ **Time saved:** 3-5 hours/week on content repurposing
- 📊 **Output volume:** 5-8 platform-ready pieces per source content
- 🎯 **Consistency:** Every platform gets fresh content

### Short-term (Month 1)
- 📈 **Posting frequency:** 3-5x increase in cross-platform presence
- 🔄 **Content velocity:** Same effort, 5x the output
- 💡 **Better hooks:** AI-generated alternatives surface winning angles

### Long-term (3+ Months)
- 🌐 **Audience growth:** Consistent presence = compound growth
- 📚 **Content library:** Organized archive of all variations
- 🧠 **Pattern recognition:** OpenClaw learns your voice and what performs

### Sample Output Structure

After processing, your output folder looks like:

```
~/content-engine/output/
└── 2024-01-15-building-in-public/
    ├── twitter-thread.md
    ├── linkedin-post.md
    ├── newsletter-snippet.md
    ├── reddit-r-startups.md
    ├── instagram-carousel-concepts.md
    └── quotes-for-graphics.md
```

Each file is copy-paste ready for its platform.

---

## Quick Start Checklist

- [ ] Create folder structure (`~/content-engine/{input,output,templates}`)
- [ ] Add platform guidelines to templates
- [ ] Update TOOLS.md with paths
- [ ] Add content check to HEARTBEAT.md
- [ ] Test with one piece of content
- [ ] Set up daily cron for automation

**Time to setup: ~15 minutes**
**Time saved weekly: 3-5 hours**
**ROI: Infinite** 🚀
