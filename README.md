# 🏓 Table Tennis

A single-file, browser-based table tennis game built with vanilla HTML, CSS, and JavaScript. No dependencies, no build step — just open the file and play.

## Features

- **Smooth 60fps gameplay** via `requestAnimationFrame`
- **Dual input support** — control your paddle with the mouse or arrow keys
- **Synthesised audio** — all sounds (paddle hits, wall bounces, scoring, win/lose fanfares) are generated in real time using the Web Audio API; no audio files required
- **Angle-based ball physics** — where the ball hits your paddle determines its return angle, rewarding deliberate placement
- **Rally acceleration** — ball speed increases by 3% on each paddle hit, keeping long rallies tense
- **Configurable computer opponent** — three difficulty levels with tunable reaction speed and aim jitter
- **Configurable ball speed** — independently set to Slow, Medium, or Fast
- **Custom win score** — set any target from 1 to 99 points
- **Pause / Resume** — pause at any time with the button or the `P` key
- **Score flash effect** — a fading `+1` appears on the scoring side after each point

## Getting Started

No installation needed. Open `table_tennis.html` in any modern browser.

```
open table_tennis.html
```

Or drag the file into a browser window.

## How to Play

| Action | Input |
|---|---|
| Move paddle up | Mouse (over canvas) or `↑` arrow key |
| Move paddle down | Mouse (over canvas) or `↓` arrow key |
| Pause / Resume | `P` key or the Pause button |

The player controls the **left paddle**. The computer controls the **right paddle**. First to reach the win score wins.

## Settings

Settings are locked while a game is in progress and unlock again after it ends.

| Setting | Options | Default |
|---|---|---|
| Difficulty | Easy, Medium, Hard | Easy |
| Ball speed | Slow, Medium, Fast | Medium |
| Win at | 1–99 pts | 11 |

**Difficulty** controls the computer opponent's maximum movement speed per frame and how accurately it tracks the ball (higher difficulty = faster reactions, less jitter).

**Ball speed** is independent of difficulty and sets the initial launch speed. Speed also ramps up slightly with each paddle hit regardless of this setting.

## Game States

- **Start screen** — shown on load; configure settings before starting
- **In game** — Pause and Cancel buttons are active below the canvas
- **Paused** — overlay shows Resume and Cancel options; `P` also resumes
- **Game over** — win/loss result shown with final score; Play Again resets everything
- **Cancelled** — score at time of cancellation is displayed; settings unlock

## Technical Notes

- **Canvas size:** 640 × 400 px
- **Physics:** Euler integration; paddle collision angle mapped to ±60° based on hit position relative to paddle centre
- **Audio:** Web Audio API, lazily initialised on first user gesture to comply with browser autoplay policy. Five synthesised sounds: paddle hit, wall bounce, point scored, win fanfare (ascending C–E–G arpeggio), lose fanfare (descending G–E–C arpeggio)
- **No dependencies:** pure HTML/CSS/JS, single file, works offline

## Browser Support

Any modern browser with Canvas and Web Audio API support (Chrome, Firefox, Safari, Edge).
