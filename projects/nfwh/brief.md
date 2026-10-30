---
title: nfwh
status: idea
created: 2026-10-30
updated: 2026-10-30
owner: cmprssd
repo: cmprssd/nfwh
tags: [game, engine, performance]
stack: []
effort:
priority:
---

# nfwh

## Summary *

nfwh is a heavily optimized version of **Need for Speed: Heat** (Ghost Games / EA, 2019),
in the same spirit as `cmprssd/swjkja`: the same game, but a smaller footprint on disk,
much faster, and more reliable. Built on the fastest tech stack possible.

## Problem *

From the owner's experience playing it years ago, Need for Speed: Heat is heavily
bloated: large on disk, with nearly no optimization. There is no lighter or faster way to
play it today.

## Users and context

- The owner, on their own PC (Windows), playing their own copy of the game.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Palm City viewer: reads the map from the owner's Heat install and flies through it,
  showing frame rate and frame time.
- Benchmarks against the original on the same camera path and PC.

### Later

- Driving, races, campaign and free roam (single-player).
- Multiplayer of the project's own (not EA's servers).

### Not doing

- Shipping any EA code or game data: the owner's install supplies the assets.
- Connecting to EA's online services.

## Constraints

- Development costs $0 (workspace rule); checks run locally with `local-ci`.

## Decided

- Name `nfwh`, under the `cmprssd` org (`cmprssd/nfwh`). The org uses abbreviated repo
  names, an exception to the full-name rule.
- Goals, in the owner's words: smaller file size, faster game, more reliable; "heavily
  optimized, extremely quick, using the fastest tech stack possible".
- Same nature as `cmprssd/swjkja` (a new, much faster engine for an existing game).
- Clean-room engine reading the owner's installed Heat data (no source to port).
- Speed and size are measured against the original on the same scene and PC.

## Open questions *

- [x] Approach, given there is no Heat source to port? → Clean-room engine that reads
      the owner's installed Heat data (like OpenMW), reverse engineering Frostbite's
      formats.
- [x] What does the MVP run? → A Palm City viewer: load and fly through the open-world
      map from the install, frame time shown.
- [x] Online? → Single-player first; the project's own multiplayer later.
- [x] How is "faster" proven? → Same scene, same PC: frame time and load time on a
      recorded camera path vs. the original, plus install size on disk (as swjkja's
      BASELINE.md).
- [ ] Success thresholds: how much faster/smaller counts as done for the MVP?
- [ ] Target platform and minimum hardware.
- [ ] Stack: Rust like swjkja, or something else?
- [ ] License and repo visibility.

## Risks and unknowns

- No source code: everything (formats, physics, handling, AI, rendering) has to be
  reverse engineered or reimplemented. Far larger than swjkja, which had a source port.
- Frostbite's data formats (superbundles, casc catalogs, EBX/RES) are undocumented
  officially; community tools exist but may be incomplete for Heat.
- Legal: EA's EULA and anti-tamper (if the install uses it) constrain reverse
  engineering; the project must ship no EA code or data.
- Scale of the original: a large open world with modern Frostbite rendering, so "same
  look" may be out of reach; matching would need to be measured, as in swjkja.

## First session

- 

## References

- `cmprssd/swjkja` (`~/projects/cmprssd/swjkja`): the model this project follows
  (README, `docs/OVERVIEW.md`, `docs/DECISIONS.md` "Project direction").

## Log

- 2026-10-30: created.
- 2026-10-30: round 1: clean-room engine, Palm City viewer MVP, single-player first, measured benchmarks.
