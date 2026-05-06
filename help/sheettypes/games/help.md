## 🎮 Games

### Take a break with built-in arcade games right inside your workbook

The **Games** sheet type drops a four-game arcade into any workbook tab. Useful as a workbook-side micro-break, a presentation icebreaker, or a "first sheet" for someone who's never used xApps and needs a friendly entry point. Games are single-player and run entirely in the browser — no network round-trips during play, so even slow connections feel instant.

Per-game high scores persist as workbook state on the Games sheet itself, so they survive reloads, sync across collaborators, and travel with the workbook file.

> 🤖 Agent example: an agent can seed a fresh Games sheet, drive a Tetris session via the browser harness, then read the saved high score back through the CLI to verify game state is durably persisted.

![Games sheet launcher with cards for Tetris, Snake, Space Invaders, and Galaga](/help-assets/screenshots/games-launcher.png)

---

### Features at a Glance

- Four classic arcade games (Tetris, Snake, Space Invaders, Galaga) — all keyboard-driven
- Per-game high score tracking persisted as `gamesHighScores` on the sheet
- Active-game selection persisted as `gamesActiveGame` so reload returns to the same screen
- Game launcher with cards for each available game
- View menu shortcut: **Back to game launcher** returns from any game to the launcher
- Pause / resume on most games (P key)
- Ghost piece + next-piece preview in Tetris
- Difficulty ramps automatically as you progress
- Single CLI command (`games-scores`) and matching MCP tool (`games_scores`) for reading the high-score table programmatically
- Single-player gameplay; high scores replicate across collab clients

---

### The Games

| Game | Description | Controls |
|------|-------------|----------|
| **Tetris** | Stack falling tetrominoes to clear horizontal lines. Speed ramps with each level cleared. | ← / → move, ↑ rotate, ↓ soft drop, **Space** hard drop, **P** pause |
| **Snake** | Eat food to grow longer; avoid walls and your own tail. Speed increases with length. | Arrow keys or WASD; **P** pause |
| **Space Invaders** | Defend Earth from descending alien waves. Enemies shoot back and accelerate as their numbers shrink. | ← / → move, **Space** shoot, **P** pause |
| **Galaga** | Battle waves of diving alien fighters. Diving enemies score more but are harder to hit. | ← / → move, **Space** shoot, **P** pause |

Each game's high score is stored under its own key in `gamesHighScores`, so improving your Snake score doesn't affect your Tetris score.

---

### Getting Started

1. **Add a Games sheet.** Click the `+` button in the sheet tab bar and pick **Games**. The new sheet renders the launcher with four game cards.
2. **Pick a game.** Click any card. The sheet swaps to that game's screen and `gamesActiveGame` records your choice so reload returns to it.
3. **Play.** All controls are keyboard-only — click the game area first to capture focus.
4. **Pause if you need to.** Press **P** to pause; press again to resume.
5. **Back to the launcher.** Click the **← BACK** button at the top of the game, or open **View → Back to game launcher** from the menubar.
6. **Beat the high score.** When the round ends, your score is checked against `gamesHighScores[<game>]`; new bests are saved to the workbook automatically.

---

### Tips by game

- **Tetris** — Use the **ghost piece** (translucent outline at the bottom) to land tetrominoes precisely. Plan combos by leaving a tall column for the long bar (I-piece) for a Tetris (4-line clear). Hard-drop (Space) is committal; soft-drop (↓) gives last-second adjustments.
- **Snake** — The game speeds up as you eat. Carve out a winding corridor early so you have somewhere to go when the snake is long.
- **Space Invaders** — Take out the corner enemies first to keep the formation manageable. Watch for the bonus saucer that flies across the top.
- **Galaga** — Don't get greedy chasing divers; defend your bottom edge first, mop up survivors after.

---

### Persistent State

Two top-level fields on the Games sheet:

- `gamesActiveGame: 'tetris' | 'snake' | 'invaders' | 'galaga' | null` — the launched game (null = launcher).
- `gamesHighScores: Record<string, number>` — best score per game, keyed by game id.

Both go through the surface's `applyCreateDefaults` / `applySettings` so they're normalized on load (negative scores are clamped to 0; unknown game keys are dropped).

---

### Command Line Interface

The games surface ships **one** CLI command — every other game interaction is keyboard-driven inside the browser.

```bash
xapps games-scores <sheet>
```

Prints the per-game high-score table for a Games sheet. Empty table prints `No high scores yet.` Useful for verifying that a play session persisted, or for scripting a leaderboard digest. Pass `--json` for machine-readable output.

---

### MCP

`games_scores` mirrors the CLI command — pass `{ sheet: "<name>" }` and get back the same scores envelope. Useful inside agentic flows that want to react to a high-score event without scraping the browser.

---

### REST API

The Games surface routes through the standard sheet API. There's no per-game `/api` because gameplay happens locally; the only persisted state is the two sheet fields above:

- `GET /api/sheets/<games>` — read the sheet record (`gamesActiveGame`, `gamesHighScores`).
- `PUT /api/sheets/<games>` — patch the sheet record (used internally by the browser after each round).

---

### Collab

Games is a "single-player most of the time" surface, but it's still a sheet, and a sheet's two fields (`gamesActiveGame`, `gamesHighScores`) are part of the workbook collab graph. Two browsers viewing the same Games sheet:

- See **independent active games** — each client picks its own game from the launcher; one client's choice doesn't yank the other into the same screen.
- See **shared high scores** — when client A finishes a Tetris run with a new best, client B sees the updated `gamesHighScores.tetris` after the next collab tick.

The split is intentional — gameplay is per-screen, but the leaderboard is one shared state.

---

### Accessibility

- All controls are keyboard-only by design; no mouse-only mechanic.
- The launcher and game frames respect the workbook dark theme.
- Pause is supported in all four games for unscheduled interruptions.
- High-contrast mode in the browser carries through (no fixed background colors that fight the OS theme).

---

### Known Follow-Ups

- **Multiplayer mode** — a Snake or Tetris race where two clients compete on the same sheet would be a fun expansion. Each player would render their own board; scores would race in real time.
- **More games** — Pong, Breakout, Asteroids are all natural fits.
- **Achievements / streaks** — track "first 1000-score Tetris run", "10-game Snake streak", etc., as additional sheet fields with badges in the launcher.
- **Sound** — currently silent; muted-by-default audio with a tiny preference toggle would add a lot.
