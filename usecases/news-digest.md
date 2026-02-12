# 📰 Personalized News Digest

> Stay informed without drowning in feeds. Get only what matters to you.

---

## The Problem

Information overload is real. Between Twitter, Hacker News, Reddit, newsletters, and news sites, you either spend hours scrolling or miss important developments in your field. Most news aggregators don't understand YOUR priorities.

---

## The Solution

Clawdbot monitors your chosen sources, filters by your interests, removes duplicates, and delivers a personalized digest at your preferred time. It learns what you engage with and improves over time.

---

## Setup Guide

### Step 1: Install News Skills (5 minutes)

```bash
clawdbot skill install miniflux  # RSS aggregator
clawdbot skill install hn-digest  # Hacker News
clawdbot skill install reddit  # Reddit
clawdbot skill install bbc-news  # BBC News
```

### Step 2: Define Your Interests

Create `~/clawd/news/interests.md`:

```markdown
# My News Interests

## High Priority (always include)
- AI/ML developments
- Startup funding news
- Programming languages (Rust, Swift, TypeScript)
- My company mentions: [YourCompany]
- Competitors: [Competitor1, Competitor2]

## Medium Priority (include if space)
- Tech industry news
- Product launches
- Developer tools

## Low Priority (only if highly upvoted/shared)
- General tech
- Science breakthroughs

## Exclude
- Crypto/blockchain (unless major)
- Political drama
- Clickbait ("You won't believe...")
```

### Step 3: Configure Sources

Create `~/clawd/news/sources.json`:

```json
{
  "rss": {
    "minifluxUrl": "https://rss.yourdomain.com",
    "feeds": ["tech", "programming", "business"]
  },
  "hackerNews": {
    "minScore": 100,
    "categories": ["show", "ask", "top"]
  },
  "reddit": {
    "subreddits": ["programming", "MachineLearning", "startups"],
    "minUpvotes": 500
  }
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `miniflux` | RSS feed aggregation |
| `hn-digest` | Hacker News filtering |
| `reddit` | Reddit monitoring |
| `bbc-news` | BBC News feeds |
| `brave-search` | Fill gaps with web search |

---

## Example Prompts

**Morning digest:**
```
What happened overnight that I should know about? Focus on AI, startups, and anything mentioning [my interests].
```

**Deep dive:**
```
I saw a headline about [topic]. Give me the full story with multiple sources and different perspectives.
```

**Weekly synthesis:**
```
What were the biggest stories this week in tech? What trends are emerging?
```

**Custom alert:**
```
Alert me immediately if any news mentions [company name] or [topic] in the next 24 hours.
```

---

## Cron Schedule

```
0 7 * * 1-5    # 7 AM weekdays - morning digest
0 12 * * *     # Noon daily - midday update (brief)
0 18 * * 5     # 6 PM Friday - weekly synthesis
*/30 * * * *   # Every 30 min - check for breaking news on priority topics
```

---

## HEARTBEAT.md Config

```markdown
## News Monitoring
- [ ] Any breaking news on priority topics?
- [ ] Competitor mentions in last 6 hours?
- [ ] Trending topics relevant to my interests?
```

---

## Expected Results

**Week 1:**
- 80% reduction in time spent on news
- No more FOMO (Fear Of Missing Out)

**Month 1:**
- Personalized digest accuracy improves
- Discover sources you wouldn't have found
- Always know about important developments

**Month 3:**
- Industry knowledge compounds
- Better conversation/meeting prep
- Early awareness of trends affecting your work
