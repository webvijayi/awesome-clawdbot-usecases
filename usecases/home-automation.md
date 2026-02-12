# 🏠 Smart Home Orchestrator

> Your home, intelligently automated. Not just "lights on" but "perfect ambiance."

---

## The Problem

Smart home devices are dumb in isolation. You have 10 apps for 10 devices. Creating complex automations requires programming skills. And when something changes (guest visiting, working from home), you manually adjust everything.

---

## The Solution

Clawdbot becomes your home's brain: understands context (time, weather, who's home, your calendar), orchestrates devices together, and adapts to your life. Tell it what you want in natural language.

---

## Setup Guide

### Step 1: Install Smart Home Skills

```bash
clawdbot skill install homeassistant
clawdbot skill install homey-cli
clawdbot skill install nest-devices
clawdbot skill install netatmo
```

### Step 2: Define Scenes

Create `~/clawd/home/scenes.md`:

```markdown
# Home Scenes

## Morning
- Lights: Gradual brighten 15 min before alarm
- Thermostat: 72°F
- Coffee maker: Start
- Blinds: Open

## Work Mode
- Office lights: Bright, cool white
- Other rooms: Off
- Thermostat: Comfortable
- Do Not Disturb: On

## Movie Night
- Living room: Dim to 20%
- TV backlighting: On, blue
- Thermostat: 70°F
- Blinds: Closed

## Goodnight
- All lights: Off
- Doors: Locked
- Thermostat: 68°F
- Security: Armed
```

### Step 3: Set Context Rules

Create `~/clawd/home/rules.md`:

```markdown
# Automation Rules

## When I leave home
- Lights off (except security)
- Thermostat: Eco mode
- Security: Armed

## When I arrive home
- Lights: Based on time of day
- Thermostat: Comfort mode
- Security: Disarmed

## Guest mode
- Guest room: Comfortable
- WiFi: Share guest password
- Morning routine: Delayed
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `homeassistant` | Central home automation hub |
| `homey-cli` | Homey device control |
| `nest-devices` | Nest thermostat/cameras |
| `netatmo` | Climate/weather sensors |

---

## Example Prompts

**Activate a scene:**
```
Movie night mode.
```

**Custom automation:**
```
When the temperature outside drops below 50°F, close the blinds and set heat to 72.
```

**Status check:**
```
What's the status of my home? Any doors unlocked? What's the temperature?
```

**Guest preparation:**
```
My parents are arriving tomorrow. Prepare the guest room - comfortable temperature, lights on timer, share WiFi password.
```

---

## Cron Schedule

```
0 6 * * *      # 6 AM - start morning routine
0 23 * * *     # 11 PM - goodnight routine
*/10 * * * *   # Every 10 min - check for anomalies
```

---

## Expected Results

**Week 1:**
- All devices controllable via voice/chat
- Basic scenes working

**Month 1:**
- Context-aware automations
- 50% reduction in manual adjustments

**Month 3:**
- Home anticipates your needs
- Energy savings from smart optimization
- Guests impressed by seamless experience
