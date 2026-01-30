# Gym Tracker

A minimal, mobile-first workout tracker built for the DENSITY PROTOCOL training program.

![Dark theme](https://img.shields.io/badge/theme-dark-1a1a1a) ![PWA Ready](https://img.shields.io/badge/PWA-ready-22c55e) ![No Backend](https://img.shields.io/badge/backend-none-blue)

## Features

- **Planned Workouts** — Full LPPLPP (Legs/Push/Pull) 6-day split with exercises, sets, reps, RPE, and rest times pre-programmed
- **Weight Logging** — Track weight used per exercise with numeric input
- **Feeling Tracker** — Rate each exercise as Hard/Okay/Light to inform future sessions
- **Progress Memory** — Shows previous weight and feeling for each exercise on subsequent workouts
- **Body Weight** — Weekly Monday weigh-in tracking with trend indicator
- **Block Periodization** — Auto-detects current training block based on date (Primer → Intensify → Deload → Peak Push → Polish → Peak Display)
- **Offline First** — Works without internet, data stored in localStorage

## Schedule

| Block | Dates | RPE | Notes |
|-------|-------|-----|-------|
| Block 1 - Primer | Jan 30 - Feb 17 | 7-8 | 9-day opening push, then 6-on-1-off |
| Block 2 - Intensify | Feb 18 - Mar 12 | 9-10 | Higher intensity, fewer sets |
| Strategic Deload | Mar 13 - Mar 22 | — | Yosemite + Spring Break |
| Block 2 - Peak Push | Mar 23 - Mar 28 | 10 | Final intensity push |
| Polish Phase | Mar 30 - Apr 19 | 7-8 | 4 days/week (Mon/Tue/Thu/Sat) |
| Peak Display | Apr 20+ | — | Maintenance |

## Usage

### Option 1: Direct File
1. Download `gym_tracker.html`
2. Open in Safari on iPhone
3. Tap Share → Add to Home Screen
4. Launch from home screen for full-screen app experience

### Option 2: Self-Host
Host the HTML file on any static server (GitHub Pages, Netlify, Vercel, etc.) and access via mobile browser.

## Data Storage

All data is stored in browser `localStorage`:
- Persists between sessions
- Device-specific (no sync)
- Lost if browser data is cleared

### Data Schema
```javascript
{
  gymLog: {
    "2026-01-30": {
      "ex0_weight": "185",
      "ex0_feeling": "okay",
      "ex0_name": "Back Squat",
      // ...
    }
  },
  bodyWeight: {
    "2026-01-27": 175.5  // Monday of each week
  }
}
```

## Customization

### Modify Workouts
Edit the `BLOCK1_WORKOUTS` and `BLOCK2_WORKOUTS` objects in the `<script>` section:

```javascript
const BLOCK1_WORKOUTS = {
  legs1: {
    name: 'Legs #1',
    time: '75-85 min',
    exercises: [
      { name: 'Back Squat', sets: 3, reps: '4-6', rpe: '7-8', rest: '3-4m', notes: 'Full depth' },
      // Add/modify exercises
    ]
  },
  // ...
};
```

### Change Schedule
Modify the `GYM_PROGRAM` object and `REST_DAYS` array:

```javascript
const PROGRAM_START = '2026-01-30';

const GYM_PROGRAM = {
  blocks: {
    block1: { name: 'Block 1', start: '2026-01-30', end: '2026-02-17', rpe: '7-8' },
    // ...
  }
};

const REST_DAYS = ['2026-02-08', '2026-02-15', /* ... */];
```

### Switch to Metric
Find and replace `lbs` with `kg` throughout the file.

## Tech Stack

- Vanilla HTML/CSS/JavaScript
- No dependencies
- No build step
- ~1500 lines total

## License

MIT

---

*Built for the DENSITY PROTOCOL training program targeting peak physique by April 20, 2026.*
