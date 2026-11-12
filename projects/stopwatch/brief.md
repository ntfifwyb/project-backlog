---
title: Stopwatch
status: idea
created: 2026-11-12
updated: 2026-11-12
owner: ntfifwyb
repo:
tags: [desktop, utility]
stack: []
effort:
priority:
---

# Stopwatch

## Summary *

An extremely minimalistic stopwatch app: a small, monochrome window with no window bar,
draggable from anywhere on its UI, showing elapsed time as `00:00:00` and only two buttons:
continue/pause and reset.

## Problem *

Existing stopwatches are cluttered: laps, decimals, window chrome and extras get in the way.
The user wants only the time and two buttons.

## Users and context

- The user, on Windows and Linux desktops.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Time shown as `00:00:00` (hours:minutes:seconds), no decimals or fractions of a second.
  Past 99:59:59 the hours keep growing (`100:00:00`).
- A first button that reads "Start" at 00:00:00, "Continue" after a pause, and "Pause" while running.
- One more button: reset.
- No window bar: no minimize, maximize or close buttons.
- Draggable from everywhere on its UI.
- Small and monochrome: white on true black (`#000`), terminal-like.
- Buttons are words ("Start" / "Continue" / "Pause", "Reset"): plain white text, no borders, no background color.
- Right-click opens a tiny menu with Quit (the only way to close it besides the OS).
- Always on top of other windows.
- Remembers elapsed time across restarts: reopening shows the time from when it was closed, paused, ready to continue.
- Remembers window position across restarts.
- Keys while focused: Space toggles start/continue/pause, R resets.
- One bundled monospace font, so it looks the same on Windows and Linux.

### Later

- 

### Not doing

- Laps.
- Decimals / fractions of a second in the display.
- Window bar or minimize/maximize/close buttons.

## Constraints

- Development costs $0.

## Decided

- It's an app, extremely minimalistic.
- Platforms: Windows and Linux.
- Quit via a right-click menu.
- Always on top.
- Elapsed time is saved on close and restored, paused, on launch.
- Window position is remembered.
- First button label: Start at zero, Continue after pause, Pause while running.
- Keyboard: Space and R.
- Font: one bundled monospace font.
- Hours keep growing past 99.
- Look: white on true black, terminal-like; buttons are plain white words with no border or background.
- Policy check (Anthropic Usage Policy, effective 2026-11-12, read 2026-11-12): **allowed**.
  A local timing app with no data collection touches nothing the policy restricts.

## Open questions *

- [x] Platform? → Windows and Linux.
- [x] How to quit with no close button? → Right-click menu with Quit.
- [x] Stay on top of other windows? → Always on top.
- [x] Time after closing and reopening? → Remembered, shown paused.
- [x] Why build it? → Existing stopwatches are cluttered.
- [x] Buttons as icons or words? → Words.
- [x] Colors? → White on black. True black; buttons have no borders or background color, just white text. Terminal-like.
- [x] Remember window position? → Yes.
- [x] First button label at 00:00:00? → "Start" at zero.
- [x] Keyboard keys? → Space and R.
- [x] Font? → Bundled monospace.
- [x] Past 99:59:59? → Hours keep growing.

## Risks and unknowns

- Borderless, always-on-top, drag-anywhere windows behave differently across Linux window
  managers and X11 vs Wayland (Wayland restricts always-on-top and app-driven moves); test on
  the user's Linux setup early.

## First session

- 

## References

- 

## Log

- 2026-11-12: created.
- 2026-11-12: round 1 answers (platform, quit, on top, persistence).
- 2026-11-12: round 2 answers (problem, buttons, colors, position).
- 2026-11-12: round 3 answers (first label, keys, font, overflow).
