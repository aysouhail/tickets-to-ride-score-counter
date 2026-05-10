# 🚂 Ticket to Ride — Score Counter

A simple, beautiful, **single-file** web app to track scores while playing the board game *Ticket to Ride*. No server, no build step, no dependencies — just one `index.html`.

![Single file](https://img.shields.io/badge/single--file-HTML-orange) ![Vanilla JS](https://img.shields.io/badge/vanilla-JS-yellow) ![Offline ready](https://img.shields.io/badge/offline-ready-brightgreen)

## Features

- **2 to 10 players** — adjustable on the setup screen with a stepper
- **Per-player customization** — name and color (10 colors available)
- **One-tap turn entry** — click a player card, choose how many carriages (1–8), confirm
- **Stations** — toggle up to **3 stations per player**, each worth **+4 points**
- **Longest Road bonus** — dropdown to assign **+10 points** to one player (clearable)
- **Destination Tickets** — at the end of the game, add each player's tickets with custom point values; completed tickets **add** points, uncompleted ones **subtract**
- **Live ranking** — the leader is automatically highlighted with a 🏆 badge
- **Turn history** — full chronological log; delete individual turns or undo the last one
- **Auto-save** — game state persists in `localStorage`, survives refresh / closing the tab
- **Keyboard shortcuts** — in the turn modal, press `1`–`8` then `Enter` (or `Esc` to cancel)
- **Mobile-friendly** — responsive layout, touch-optimized
- **Dark theme** by default

## Scoring

### Carriages (per turn)

| Carriages | Points |
| --------- | ------ |
| 1         | 1      |
| 2         | 2      |
| 3         | 4      |
| 4         | 7      |
| 5         | 10     |
| 6         | 15     |
| 7         | 18     |
| 8         | 21     |

### Bonuses

- **Station**: +4 points each, max 3 per player (so up to +12)
- **Longest Road**: +10 points, awarded to one player at game end
- **Destination Tickets**: each ticket has a custom point value (you enter it from the card). Completed tickets add the points to your score; uncompleted tickets subtract them.

A player's total = sum of all turn points + (stations × 4) + (longest-road bonus if held) + ticket points (signed).

> **Note**: the carriage table above matches the standard *Ticket to Ride: Europe* edition. If you play with different rules, you can change the values directly in `index.html` — see [Customizing](#customizing) below.

## Run it locally

Just open `index.html` in any modern browser:

```bash
open index.html        # macOS
xdg-open index.html    # Linux
start index.html       # Windows
```

That's it. No `npm install`, no compilation, nothing to set up.

## Host it for free

Since the app is fully static, you can host it on any of these for free:

### Option 1 — Netlify Drop (zero setup)

1. Go to [app.netlify.com/drop](https://app.netlify.com/drop)
2. Drag this folder (or just `index.html`) into the page
3. Done — you get a public URL instantly

### Option 2 — GitHub Pages

```bash
git init
git add .
git commit -m "Initial commit"
git remote add origin https://github.com/<your-username>/ticket-to-ride-counter.git
git push -u origin main
```

Then in the GitHub repo: **Settings → Pages → Source: `main` branch, `/root` folder → Save**.
Your site will be live at `https://<your-username>.github.io/ticket-to-ride-counter/` within a minute.

### Option 3 — Cloudflare Pages / Vercel

Connect a GitHub repo, leave the build command empty, and set the output directory to `/`. Both are free for personal use and have generous limits.

## Customizing

All scoring constants live near the top of the `<script>` block in `index.html`:

```javascript
const SCORE_TABLE = {
  1: 1,  2: 2,  3: 4,  4: 7,
  5: 10, 6: 15, 7: 18, 8: 21,
};

const MAX_STATIONS = 3;
const STATION_POINTS = 4;
const LONGEST_ROAD_BONUS = 10;
```

Change those values to match your house rules or a different edition. The UI (modal buttons, scoring reference panel, station dots) automatically adapts.

You can also change the **player color palette** by editing `PLAYER_COLORS`.

## Tech

- One HTML file, ~1300 lines (HTML + CSS + vanilla JS)
- No frameworks, no dependencies, no build tooling
- Works offline once loaded
- Tested in modern Chrome, Firefox, Safari

## License

MIT — do whatever you want with it.
