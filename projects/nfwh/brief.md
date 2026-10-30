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

- 

### Later

- 

### Not doing

- 

## Constraints

- Development costs $0 (workspace rule); checks run locally with `local-ci`.

## Decided

- Name `nfwh`, under the `cmprssd` org (`cmprssd/nfwh`). The org uses abbreviated repo
  names, an exception to the full-name rule.
- Goals, in the owner's words: smaller file size, faster game, more reliable; "heavily
  optimized, extremely quick, using the fastest tech stack possible".
- Same nature as `cmprssd/swjkja` (a new, much faster engine for an existing game).

## Open questions *

- [ ] How does this differ from swjkja's starting point? swjkja ports released GPL source
      (OpenJK) and reads the owner's game data. Heat's Frostbite engine and code were
      never released, so there is nothing to port. Options: (a) clean-room engine that
      reads the owner's installed Heat data (like OpenMW for Morrowind), needing reverse
      engineering of Frostbite file formats; (b) optimize the original install itself
      (repack/compression, config, mods) without a new engine.
- [ ] What does the MVP run? (e.g. a map/free-roam viewer of Palm City, one drivable car,
      one race.)
- [ ] Single-player only? Heat's online/multiplayer depends on EA servers.
- [ ] How is "faster/smaller/more reliable" measured against the original (same scene,
      same hardware), and which numbers count?
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
