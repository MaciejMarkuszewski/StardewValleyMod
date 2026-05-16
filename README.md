# MultiplayerTime

A [SMAPI](https://smapi.io/) mod for Stardew Valley that synchronizes time pausing in
multiplayer. When players would have their time paused in single player — opening menus,
talking to NPCs, fishing, cutscenes, and more — the clock stops for everyone on the server.

Originally created by **lolmaj**. This fork adds configurable pause behavior and the
same-location pause feature.

---

## Features

- **Multiplayer time sync** — the host collects pause state from all connected players.
  When the configured condition is met, the clock stops for the whole server.
- **Player status bar** — a visual bar near the clock shows how many players are free to
  act (blue) vs paused (green). Red indicates a player who has not yet sent a status update.
- **Skull Cavern time fix** — time slows proportionally based on how many players are inside
  the Skull Cavern, matching single-player behavior.
- **Monster and health locking** — while time is paused, monsters freeze and player
  invincibility timers are suspended.
- **Buff timer pause** — food and drink buff durations do not tick down while time is paused.
- **Hotkey toggle** — press `F3` (configurable) to enable or disable the mod mid-session.
- **UI themes** — choose between Default, Vintage V2, and Natural Dark Wood bar styles.
- **Clock format** — 12-hour or 24-hour display, with locale-aware defaults.
- **UI Info Suite compatibility** — optional offset mode to avoid overlapping with UI Info Suite.

---

## Fork Changes (v5.4)

The following changes are included in this fork on top of the v5.3 upstream release:

### PR #3 — Freeze time when any player is paused
In the original mod, time only pauses when **all** players signal a pause state. This option
inverts that: time pauses as soon as **any** player signals a pause. Useful for two-player
sessions where one player should never be left behind. Disabled by default.

### New — Pause when all players share the same indoor location
When all players are inside the same building at the same time, time pauses automatically.
Useful for cooperative moments — reorganizing chests, planning, or just not wanting the
clock to run while everyone is together indoors. Disabled by default.

---

## Requirements

- [SMAPI](https://smapi.io/) 4.1.10 or later
- [Generic Mod Config Menu](https://www.nexusmods.com/stardewvalley/mods/5098) (required)
- Stardew Valley 1.6 or later
- **All players on the server must have this mod installed.**

---

## Installation

1. Install SMAPI and Generic Mod Config Menu if you haven't already.
2. Download this mod and extract the `MultiplayerTime` folder into your
   `Stardew Valley/Mods` directory.
3. Launch the game through SMAPI.
4. Configure via the in-game Generic Mod Config Menu or by editing `config.json` directly.

---

## Configuration

All options are available through Generic Mod Config Menu in-game, or by editing
`config.json` in the mod folder.

| Option | Default | Description |
|---|---|---|
| `Active` | `true` | Enable or disable the mod entirely. |
| `ActivationKey` | `F3` | Hotkey to toggle the mod on and off mid-session. |
| `PauseWhenAnyPlayerPaused` | `false` | Pause time when **any** player signals pause, instead of requiring all players to be paused. |
| `PauseWhenTogetherIndoors` | `false` | Pause time when all players are inside the same building. |
| `UiInfoSuite` | `false` | Offset the status bar to avoid overlapping with UI Info Suite. |
| `InvisibleUI` | `false` | Hide the status bar UI entirely. |
| `HourFormat` | `"Default"` | Clock display format. Options: `"Default"` (locale-based), `"12"`, `"24"`. |
| `InterfaceTheme` | `"Default"` | Visual theme for the status bar. Options: `"Default"`, `"Vintage V2"`, `"Natural Dark Wood"`. |

---

## Known Issues

- **Duplicate clock/bar rendering** — on some sessions, the status bar and clock text
  appear duplicated and offset to the left of the main clock. Not consistently reproducible.
  Under investigation.

---

## Credits

- **lolmaj** — original mod author ([Nexus page](https://www.nexusmods.com/stardewvalley/mods/2543))
- **DiscipleOfEris** — Combined Rings save fix (PR #2)
- **sprtlw** — freeze-when-any-player-paused logic (PR #3)