# 🎙️ Podcast Production Pipeline

> From idea to published episode, streamlined. Focus on talking, not logistics.

---

## The Problem

Podcast production is 20% recording and 80% everything else: research, outlines, show notes, transcription, editing, publishing, promotion. Most podcasters burn out on the admin, not the content.

---

## The Solution

OpenClaw handles the pipeline: researches topics, creates outlines, generates show notes, transcribes episodes, creates social clips, and drafts promotion. You focus on the conversation.

---

## Setup Guide

### Step 1: Install Production Skills

```bash
openclaw skill install local-whisper  # Transcription
openclaw skill install youtube-summarizer
openclaw skill install voice-transcribe
openclaw skill install video-subtitles
```

### Step 2: Set Up Episode Template

Create `~/openclaw/podcast/episode-template.md`:

```markdown
# Episode {number}: {title}

## Pre-Production
- [ ] Topic researched
- [ ] Outline created
- [ ] Guest prep (if applicable)

## Recording
- Date:
- Duration:
- File:

## Post-Production
- [ ] Transcription complete
- [ ] Show notes written
- [ ] Timestamps added
- [ ] Social clips identified

## Publishing
- [ ] Audio edited
- [ ] Uploaded to host
- [ ] Show notes published
- [ ] Social promotion scheduled
```

### Step 3: Configure Show Details

Create `~/openclaw/podcast/show.json`:

```json
{
  "name": "Your Podcast Name",
  "host": "Your Name",
  "format": "interview",
  "typicalLength": "45-60 min",
  "publishDay": "Tuesday",
  "platforms": ["Spotify", "Apple", "YouTube"]
}
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `local-whisper` | Transcription |
| `youtube-summarizer` | Video content analysis |
| `voice-transcribe` | Voice note processing |
| `video-subtitles` | Subtitle generation |
| `content-multiplication` | Social promotion |

---

## Example Prompts

**Episode research:**
```
I'm doing an episode about [topic]. Give me 10 interesting angles, 5 potential guests, and key questions to explore.
```

**Outline creation:**
```
Create an episode outline for a 45-minute conversation about [topic]. Include intro hook, 3 main segments, and call to action.
```

**Post-recording processing:**
```
Here's the audio from today's recording [file]. Transcribe it, create show notes with timestamps, and identify 3 best clips for social media.
```

**Guest prep:**
```
I'm interviewing [name] tomorrow. Research their background, recent work, and suggest 10 thoughtful questions.
```

---

## Cron Schedule

```
0 9 * * 1      # Monday 9 AM - week's episode planning
0 10 * * 3     # Wednesday 10 AM - post-production check
0 6 * * 2      # Tuesday 6 AM - publish day prep
```

---

## Expected Results

**Per Episode:**
- 3-4 hours saved on admin
- Better research and preparation
- Consistent show notes quality

**Monthly:**
- Sustainable production pace
- Growing content library
- More time for creative work
