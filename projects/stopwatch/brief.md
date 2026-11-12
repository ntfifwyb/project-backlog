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

<!-- Not stated yet: what's wrong with the stopwatches the user has today. -->

## Users and context

- The user, on Windows and Linux desktops.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Time shown as `00:00:00` (hours:minutes:seconds), no decimals or fractions of a second.
- A continue button, which turns into a pause button while running.
- One more button: reset.
- No window bar: no minimize, maximize or close buttons.
- Draggable from everywhere on its UI.
- Small and monochrome.
- Right-click opens a tiny menu with Quit (the only way to close it besides the OS).
- Always on top of other windows.
- Remembers elapsed time across restarts: reopening shows the time from when it was closed, paused, ready to continue.

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
- Policy check (Anthropic Usage Policy, effective 2026-11-12, read 2026-11-12): **allowed**.
  A local timing app with no data collection touches nothing the policy restricts.

## Open questions *

- [x] Platform? → Windows and Linux.
- [x] How to quit with no close button? → Right-click menu with Quit.
- [x] Stay on top of other windows? → Always on top.
- [x] Time after closing and reopening? → Remembered, shown paused.

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
