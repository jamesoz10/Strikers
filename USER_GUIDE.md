# Caloundra Strikers Sub Manager — User Guide

---

## Overview

A Progressive Web App (PWA) for managing football substitutions, goalkeeper rotation, player stats, and match recording. Works offline after first load. All data persists across sessions via local storage — even after app updates.

---

## Installation

Open `jamesoz10.github.io/Strikers` in Safari → Share → **Add to Home Screen**. Launch from the home screen icon for full-screen experience.

---

## Main Game Screen

### Header Buttons

| Button | Action |
|--------|--------|
| ⚙️ | Opens Settings |
| **0 – 0** | Tap to edit score manually |
| 🩺 | Injury pause — freezes all timers |
| 📹 | Opens/closes camera panel |
| ☰ | Toggles drag-to-reorder mode |

---

### Player List

Players are shown in two groups: **on field** (top) then **bench** (bottom).

**Dot colours**
- 🟡 Yellow — current goalkeeper
- 🟢 Green — on field
- 🔴 Red — coming off next sub
- 🔵 Blue — coming on next sub

**Row info**
- Name + status label (e.g. "On field · Next off 1")
- Timer showing total field time (or keeper time for goalkeeper)
- ⚽ goal button — tap to log a goal for that player (also increments team score)
- ≡ drag handle — drag to reorder (drag mode must be on)

**Tapping a keeper row** opens the Switch Keeper modal — select any player to immediately swap them into goal.

---

### Bottom Bar — Timers

**Sub timer** (left)
- Counts down to next substitution
- Tap to start/pause independently
- Turns red when ≤ 30 seconds
- Auto-triggers sub alert at zero

**Swap button** (centre)
- Pulses when a substitution is due
- Tap to confirm which players swap in/out

**Game timer** (right)
- Shows countdown + half (1st Half / 2nd Half / FT)
- Tap to start/pause
- Starting game timer also starts sub timer
- At half time → half time modal appears
- At full time → game auto-saves to Season Stats

---

### Keeper Timer Bar

Appears below the banners when keeper rotation is enabled.

- Shows countdown to next keeper change
- **Edit ›** — jumps to Keeper Rotation screen
- **↺ Reset** — resets keeper timer back to the full interval

---

### Injury Pause

Tap 🩺 to freeze all timers immediately. A modal confirms the pause. Tap **Resume Game** to continue.

---

### Half Time Modal

Appears automatically when the first half timer reaches zero.

- **▶ Start 2nd Half** — resets sub timer and keeper timer, starts second half
- **Stay at Half Time** — dismisses the modal; tap the game timer play button to start 2nd half manually

---

### Substitution Confirmation Modal

Shows which players swap out (red) and in (purple). Tap **OK** to confirm or **Cancel** to abort.

---

### Keeper Change Modal

Appears when the keeper rotation timer expires. Shows incoming and outgoing keeper. Tap **Swap** to confirm or **Skip** to skip this change.

---

## Camera Panel

Open with 📹 in the header. The panel sits at the bottom of the game screen.

### Controls (left to right in the bar)

| Control | Function |
|---------|----------|
| 🔍 slider | Zoom — 1× to 5× |
| 1.0× label | Current zoom level |
| 📱 portrait | Toggle portrait mode (restarts stream in 9:16) |
| 🔄 | Flip between front and rear camera |
| ⏺ / ⏹ | Start / stop recording |
| ✕ | Close camera panel |

### Recording

- Default mode captures **landscape 4K** (3840 × 2160, with 1080p fallback)
- Portrait mode captures **portrait 4K** (2160 × 3840)
- A red REC dot and MM:SS timer show while recording
- Tapping ⏹ **immediately opens the iOS share sheet** — save to Photos or Files
- If share fails or is cancelled, a **💾 Save Clip** button appears as fallback

### Notes

- Camera closes automatically when navigating away from the game screen
- iOS applies automatic optical stabilisation — no setting needed

---

## Settings Screen

### Team Names

Enter your team name and today's opponent. These appear in score modals and season stats.

### Quick Action Buttons

| Button | Action |
|--------|--------|
| 📊 Season Stats | View all recorded games and player stats |
| 💾 Save Game to Season | Manually save current game to season history |
| 🧤 Keeper Rotation | Configure keeper rotation queue and interval |
| 🎲 Generate Random Lineup | Shuffle player order (keeper stays first) |
| ↺ Reset & New Game | Clear score, all timers, and player times (confirmation required) |

### Configuration Sliders & Toggles

| Setting | Range | Default | Description |
|---------|-------|---------|-------------|
| Field players | 2–10 | 5 | Outfield players (goalkeeper is additional) |
| Disable goalkeeper | toggle | Off | Removes keeper slot entirely |
| Players per sub | 1–4 | 2 | How many players swap each substitution |
| Manual sub interval | toggle | Off | When ON, sub timer is disabled — you decide when to sub |
| Sub interval | 1–15 min | 4 min | Time between automatic substitutions |
| Game time | 10–90 min | 20 min | Length of each half |

### Footer

- **👥 Players** — opens Players screen
- **Done** — returns to game

---

## Players Screen

Manage the squad. Players toggled off are excluded from the game but kept in the list.

| Control | Action |
|---------|--------|
| ✓ circle | Toggle player in/out of the squad |
| ✏️ | Rename player |
| 🗑 | Delete player (confirmation required) |
| ➕ Add Player | Type name and press Add |

Changes take effect immediately — player list and timer tracking update live.

---

## Keeper Rotation Screen

### Setup

1. Enable the toggle at the top
2. Set the keeper change interval (2–30 min)
3. Drag players into the queue in the order you want them to keep
4. Tap players in "Available" section to add them to the queue

### During a Game

- A timer bar appears on the game screen counting down
- **Warnings** fire at 2 min, 1 min, and 30 sec remaining (beep + vibration)
- At zero, a confirmation modal appears to swap the keeper
- The ↺ Reset button on the timer bar resets to the full interval

---

## Season Stats Screen

### Summary

Shows overall record: wins / draws / losses.

### Player Statistics

| Column | Meaning |
|--------|---------|
| ⚽ | Total goals across all saved games |
| Field | Total time on field (MM:SS) |
| 🥅 | Total time as goalkeeper |
| GP | Games played |

### Game History

Each row shows date, opponent, and score (green = win, grey = draw, red = loss). Tap a row to edit the score or delete that game.

### Footer

| Button | Action |
|--------|--------|
| ➕ Add Game | Add a past game manually (date, opponent, score) |
| 🗑 Clear | Delete all season data (confirmation required) |
| Done | Return to Settings |

---

## Notifications & Sounds

All alerts appear briefly at the bottom of the screen and auto-dismiss after ~2.5 seconds.

| Event | Alert |
|-------|-------|
| Sub due | 🔄 Time to sub! + beep + vibration |
| 30s sub warning | ⚠️ Sub in 30 seconds! |
| Keeper change 2 min | 🧤 Keeper change in 2 min — [name] next |
| Keeper change 1 min | 🧤 Keeper change in 1 min — [name] next |
| Keeper change 30s | 🧤 Keeper change in 30s — [name] next |
| Goal logged | ⚽ Goal — [name]! |
| Keeper swapped | 🧤 [name] is now in goal |
| Game saved | 📊 Game saved to season! |
| Full time | ⏱ Full time! (auto-saves) |
| Clip recorded | 📹 Clip ready — tap Save |

---

## Data & Persistence

All data is stored locally on the device (localStorage). Nothing is sent to a server.

| Store | Contents |
|-------|---------|
| `strikers_app` | Players, settings, team names, keeper rotation config |
| `strikers_season` | All saved games, player stats |

Data survives app updates — pushing a new version to GitHub Pages never clears local data.

**To clear all data**: Use the 🗑 Clear button in Season Stats (clears games only), or clear website data in Safari Settings → [site] → Clear Data.

---

## Tips

- **First launch on iOS**: Open in Safari, tap Share → Add to Home Screen for full-screen PWA mode.
- **Audio on iOS**: Audio unlocks on first tap — if you don't hear alerts, tap anywhere on the screen at game start.
- **Camera orientation**: Landscape (default) records in 16:9. Tap 📱 to switch to 9:16 portrait recording.
- **Offline use**: After first load the app works without internet.
- **App update + cache**: If you don't see changes after an update, reload Safari (not the home screen icon) once to clear the cache.
