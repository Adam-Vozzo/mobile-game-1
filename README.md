# Maverick

A neon, beat-synced, Flappy-Bird-style web game built to be played on a phone in landscape. The entire game ships as a single static `index.html` and is deployed to GitHub Pages.

## Goals

- **One-tap arcade feel.** Tap (or click) to flap. Easy to start, hard to master.
- **Audio-reactive world.** The grid, walls and effects pulse to detected beats in `song.mp3`. With no song available, a steady 120 BPM fallback keeps the world breathing.
- **Mobile-first, zero-install.** Works from any modern mobile browser — no app store, no build step, no dependencies.
- **Variety from a single mechanic.** Three game modes share the same flap physics but ask different things of the player.

## Contents

| File | Purpose |
| --- | --- |
| `index.html` | The whole game — markup, styles, canvas rendering, physics, audio analysis and beat detection. |
| `song.mp3` | Background track. Drives beat-synced visuals; the game still runs without it. |
| `.github/workflows/` | GitHub Actions workflow that publishes the repo to GitHub Pages on every push to `main`. |
| `.nojekyll` | Tells GitHub Pages to serve the files as-is (no Jekyll processing). |

## Game modes

- **Gates** — classic Flappy-style: thread the gap between scrolling wall pairs.
- **Rings** — fly through tilted Sonic-style rings; clean passes score.
- **Tunnel** — hold a winding corridor without clipping the walls. Score grows with distance.

Per-mode best scores are stored locally in `localStorage`.

## Controls

- **Tap / click / spacebar** — flap.
- The game is locked to landscape; portrait shows a "rotate your phone" prompt.

## Running locally

Because everything is static, just serve the directory:

```bash
python3 -m http.server 8000
# then open http://localhost:8000 on your phone or in a desktop browser
```

Opening `index.html` directly via `file://` mostly works, but some browsers block `song.mp3` autoplay/decoding from the file scheme — use a local server for the full beat-synced experience.

## Deployment

Pushes to `main` are auto-deployed to GitHub Pages by `.github/workflows/`. No build step is required.
