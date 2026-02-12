# 🎤 Voice Note Organizer

> Capture thoughts anywhere. Find them organized later.

---

## The Problem

Voice notes are the fastest way to capture ideas, but they become a graveyard of untranscribed audio files. You know that brilliant idea is somewhere in your recordings, but finding it means listening to hours of audio.

---

## The Solution

Clawdbot automatically transcribes your voice notes, extracts key points, tags by topic, and makes everything searchable. Ideas captured on a walk become organized notes by the time you're home.

---

## Setup Guide

### Step 1: Install Transcription Skills

```bash
clawdbot skill install voicenotes
clawdbot skill install local-whisper
clawdbot skill install voice-transcribe
```

### Step 2: Set Up Voice Note Sync

Create `~/clawd/voice-notes/config.json`:

```json
{
  "inputSources": [
    "~/Library/Mobile Documents/com~apple~CloudDocs/VoiceNotes/",
    "~/Dropbox/VoiceMemos/"
  ],
  "outputDir": "~/clawd/voice-notes/transcripts/",
  "autoTags": ["idea", "todo", "meeting", "journal", "reminder"],
  "language": "en"
}
```

### Step 3: Configure Processing Rules

Create `~/clawd/voice-notes/rules.md`:

```markdown
# Voice Note Processing

## Auto-Tag Rules
- Contains "remind me" → todo
- Contains "meeting with" → meeting
- Contains "I think" / "what if" → idea
- Morning recordings → journal

## Extract
- Action items (make a list)
- People mentioned
- Dates/deadlines mentioned
- Questions to follow up on

## Archive
- Keep originals for 30 days
- Archive transcripts indefinitely
- Flag recordings with low confidence for review
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `voicenotes` | Voicenotes.com integration |
| `local-whisper` | Local transcription |
| `voice-transcribe` | Cloud transcription |

---

## Example Prompts

**Process new notes:**
```
Transcribe and organize all new voice notes from today.
```

**Search recordings:**
```
Find any voice notes where I talked about [topic] in the last month.
```

**Extract todos:**
```
Go through this week's voice notes and compile all action items I mentioned.
```

**Daily summary:**
```
Summarize what I recorded today. What were my main thoughts?
```

---

## Cron Schedule

```
*/30 * * * *   # Every 30 min - check for new recordings
0 21 * * *     # 9 PM - daily summary of recordings
0 10 * * 0     # Sunday 10 AM - weekly idea review
```

---

## Expected Results

**Week 1:**
- All voice notes searchable
- Ideas no longer lost

**Month 1:**
- Knowledge capture habit improved
- 10x more actionable notes
- Easy recall of past thoughts

**Ongoing:**
- Personal knowledge base grows
- "What was that idea?" → instant answer
- Voice becomes primary capture method
