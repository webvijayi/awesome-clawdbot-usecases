# ✈️ Smart Travel Planner

> Plan trips in minutes, not hours. Get personalized itineraries that actually work.

---

## The Problem

Planning a trip means juggling 10 browser tabs: flights, hotels, activities, restaurants, transport. You spend hours comparing options and still worry you missed the best deals or made suboptimal choices. Last-minute changes throw everything off.

---

## The Solution

Clawdbot handles the entire trip planning process: finds flights, suggests accommodations matching your preferences, builds day-by-day itineraries, and adapts when plans change. All in one conversation.

---

## Setup Guide

### Step 1: Install Travel Skills

```bash
clawdbot skill install flights
clawdbot skill install flight-tracker
clawdbot skill install weather
clawdbot skill install spots  # For local recommendations
```

### Step 2: Set Your Preferences

Create `~/clawd/travel/preferences.md`:

```markdown
# My Travel Preferences

## Flights
- Preferred airlines: [list]
- Seat preference: Window/Aisle
- Max layover: 3 hours
- Budget range: Economy, willing to upgrade for long hauls

## Accommodation
- Style: Boutique hotels > big chains
- Must have: WiFi, workspace, AC
- Nice to have: Gym, breakfast included
- Avoid: Hostels, shared bathrooms

## Activities
- Love: Local food, walking tours, museums, nature
- Avoid: Tourist traps, shopping malls
- Pace: Moderate (not exhausting)
- Morning person: Yes

## Food
- Dietary: None
- Adventurous: Yes, try local cuisine
- Must try: Local specialties
```

### Step 3: Create Trip Template

Create `~/clawd/travel/trip-template.md`:

```markdown
# Trip: {destination}
## Dates: {start} - {end}

### Flights
- Outbound: 
- Return:

### Accommodation
- Hotel:
- Address:
- Confirmation:

### Daily Itinerary
#### Day 1
- Morning:
- Afternoon:
- Evening:
- Dinner:

### Packing List
- [ ] Essentials
- [ ] Documents

### Emergency Info
- Embassy:
- Local emergency:
```

---

## Skills Needed

| Skill | Purpose |
|-------|---------|
| `flights` | Flight search and booking |
| `flight-tracker` | Real-time flight status |
| `weather` | Destination weather forecasts |
| `spots` | Local place recommendations |

---

## Example Prompts

**Plan a trip:**
```
Plan a 5-day trip to Tokyo in April. I like food, temples, and avoiding crowds. Budget: mid-range.
```

**Find flights:**
```
Find the best flights from SFO to London, departing March 15-17, returning March 25. Show me options with price/convenience tradeoffs.
```

**Day itinerary:**
```
Build a detailed itinerary for day 3 in Barcelona. I'm near the Gothic Quarter and want to see Sagrada Familia.
```

**Handle changes:**
```
My flight is delayed 4 hours. What does this mean for my hotel check-in and dinner reservation?
```

---

## Cron Schedule

```
0 6 * * *      # 6 AM - weather update for upcoming trips
0 8 * * *      # 8 AM - flight status check if traveling today
0 20 * * 0     # 8 PM Sunday - review upcoming travel plans
```

---

## HEARTBEAT.md Config

```markdown
## Travel
- [ ] Any flights to track today?
- [ ] Weather alerts for upcoming destinations?
- [ ] Passport/visa expiration reminders?
```

---

## Expected Results

**Per Trip:**
- 3-5 hours saved on planning
- Better itinerary than you'd create manually
- No missed reservations or bookings

**Over Time:**
- Preferences refined for better suggestions
- Travel history helps future planning
- Stress-free trip preparation
