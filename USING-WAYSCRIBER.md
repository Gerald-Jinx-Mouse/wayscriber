# Using Wayscriber (my ZoomIt replacement)

*Set up 2026-08-09 on the Arch/GNOME machine. Full manual: `README.md` in this folder, or press **F1** while drawing.*

## The one thing to remember

**Press `Super+G`** (Windows key + G) → the screen becomes drawable.
**Press `Escape`** → back to normal.

That's the whole workflow. It runs in the background all the time (starts
automatically at login), so it's always one keypress away — same as ZoomIt
sitting in the Windows tray.

## ZoomIt translation table

| I did this in ZoomIt | Here I do |
|---|---|
| Ctrl+1 (start drawing) | `Super+G` |
| Ctrl+2 (whiteboard) | `Super+G`, then `Ctrl+W` |
| Ctrl+3 (blackboard/break) | `Super+G`, then `Ctrl+B` |
| Ctrl+4 (zoom) | `Super+G`, then `Ctrl+Alt` + scroll wheel |
| Type text | `T`, click where you want it, type, `Enter` |
| Right-click to erase | `Ctrl+Z` (undo) or `E` (clear everything) |
| Esc to leave | `Escape` (same!) |

## Drawing (while the overlay is up)

| What | How |
|---|---|
| Pen (freehand) | just drag with the mouse |
| Straight line | hold `Shift` + drag |
| Rectangle | hold `Ctrl` + drag |
| Ellipse/circle | hold `Tab` + drag |
| Arrow | hold `Ctrl+Shift` + drag |
| Text | `T`, click, type, `Enter` when done |
| Sticky note | `N`, click, type, `Enter` |
| Eraser | `D` (then drag over things) |
| Move something | hold `Alt` + drag it |
| Undo / Redo | `Ctrl+Z` / `Ctrl+Y` |
| Clear the whole screen | `E` |

**Colors:** press a letter — `R`ed, `G`reen, `B`lue, `Y`ellow, `O`range,
`P`ink, `W`hite, blac`K`.
**Pen thickness:** `+` / `-` or the scroll wheel.
**Tool menu at the cursor:** click the middle mouse button (scroll wheel click).

## Zoom (the ZoomIt party trick)

Step by step:

1. `Super+G` to bring up the overlay
2. Hold `Ctrl+Alt` and **scroll the mouse wheel up** → the screen zooms in
   toward the pointer (scroll down zooms back out)
3. While zoomed, move around by **dragging with the middle mouse button**
   (press the scroll wheel and drag), or tap the **arrow keys**
4. `Ctrl+Alt+0` (zero) → instantly back to 100%
5. `Escape` → leave the overlay entirely

Extras:

- `Ctrl+Alt` + `+` / `-` zooms with the keyboard instead of the wheel
- `Ctrl+Alt+L` locks the zoomed view in place (press again to unlock)
- You can draw while zoomed — handy for pointing at tiny things
- Right-click → **Zoom** menu has the same actions if you forget the keys

## Presenting

- **Freeze the screen** (pause what's showing while apps keep running): `Ctrl+Shift+F`
- **Presenter mode** (hides toolbars, highlights every click): `Ctrl+Shift+M`
- **Whiteboard / blackboard:** `Ctrl+W` / `Ctrl+B` — back to see-through: `Ctrl+Shift+T`
- **Spotlight** (dim everything except one area): in the Shape picker on the toolbar

## Help, when stuck inside the overlay

- `F1` — full cheat sheet of every key
- `Ctrl+K` — command palette: type what you want ("arrow", "blur"...) and pick it
- `Escape` — always gets you out

## Screenshots

All of these work while the overlay is up (`Super+G` first), and your drawings
are included in the picture:

| Keys | What you get |
|---|---|
| `Ctrl+C` | Whole screen → **clipboard** (paste anywhere with Ctrl+V) |
| `Ctrl+S` | Whole screen → **saved as a PNG file** |
| `Ctrl+Shift+C` | Drag a box around an area → clipboard |
| `Ctrl+Shift+S` | Drag a box around an area → saved as PNG |
| `Ctrl+Shift+O` | Just the active window |
| `Ctrl+Alt+O` | Opens the folder where saved screenshots went |

The usual flow: `Super+G` → draw arrows/circles on whatever you're explaining →
`Ctrl+Shift+C` → drag a box around it → paste into an email or chat with
`Ctrl+V`.

If a GNOME permission dialog appears the first time ("share your screen?"),
allow it — that's how screenshots work on Wayland.

## Notes for this machine (GNOME)

- Wayscriber's GNOME support is "partial": everything above works, but **light
  passthrough mode (F6)** — drawing while clicks go through to apps underneath —
  is not available on GNOME.
- The first time freeze or capture runs, GNOME may show a screen-share
  permission dialog — allow it.
- No tray icon appears by default on GNOME (GNOME hides tray icons unless the
  AppIndicator extension is installed). Not needed — the hotkey does everything.
- My drawings survive reboots (session persistence is on by default).

## Under the hood / fixing things

- The background service: `systemctl --user status wayscriber.service`
  (restart with `systemctl --user restart wayscriber.service`)
- The `Super+G` hotkey lives in GNOME Settings → Keyboard → Custom Shortcuts →
  "Wayscriber Toggle" (runs `wayscriber --daemon-toggle`)
- Installed as the AUR package `wayscriber-bin` — updates arrive with normal
  `yay` updates
- Config file (optional tweaking): `~/.config/wayscriber/config.toml` — see
  `config.example.toml` in this folder. There's also a GUI configurator:
  install `wayscriber-configurator` from the AUR, then press `F11` in the overlay.
