---
title: nfwh
status: idea
created: 2026-10-30
updated: 2026-10-30
owner: cmprssd
repo: cmprssd/nfwh
tags: [game, engine, performance]
stack: [rust, vulkan, ash]
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

- [ ] When nfwh's Palm City viewer and the original Heat play the same recorded camera
      path on the same PC, nfwh's average and 1%-low frame times are lower.
- [ ] On that path, nfwh's frames match the original's look by automated screenshot
      comparison (as in swjkja).
- [ ] Load time to the first frame of Palm City is lower than the original's, and the
      numbers are recorded in `docs/BASELINE.md`.
- [ ] nfwh's converted copy of the data the viewer needs is smaller on disk than the
      same data in the original install.

## Scope *

### Must (MVP)

- Palm City viewer: reads the map from the owner's Heat install and flies through it,
  showing frame rate and frame time.
- Benchmarks against the original on the same camera path and PC.
- Progress GitHub page and `docs/OVERVIEW.md`, as in swjkja.

### Later

- Driving, races, campaign and free roam (single-player).
- Multiplayer of the project's own (not EA's servers).

### Not doing

- Shipping any EA code or game data: the owner's install supplies the assets.
- Connecting to EA's online services.

## Constraints

- Development costs $0 (workspace rule); checks run locally with `local-ci`.
- Testing happens only on the owner's PC; integrated-GPU performance is a goal, not
  something tested on real low-end hardware.
- It must not crash: robustness is a coding priority even without a dedicated check.

## Decided

- Name `nfwh`, under the `cmprssd` org (`cmprssd/nfwh`). The org uses abbreviated repo
  names, an exception to the full-name rule.
- Goals, in the owner's words: smaller file size, faster game, more reliable; "heavily
  optimized, extremely quick, using the fastest tech stack possible".
- Same nature as `cmprssd/swjkja` (a new, much faster engine for an existing game).
- Clean-room engine reading the owner's installed Heat data (no source to port).
- Speed and size are measured against the original on the same scene and PC.
- Stack: Rust, Vulkan 1.3 via `ash` (as swjkja). Platforms: Windows and Linux.
- Public repo from day one, GPLv3.
- Minimum hardware target: integrated GPUs (Intel HD 630 / Steam Deck class), if possible.
- "Smaller": an import step converts the install into nfwh's own compact format.
- Reverse engineering covers data files and the game executable.
- A progress page on GitHub Pages and a `docs/OVERVIEW.md` explaining how the project
  works, both just like swjkja's.

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
- [x] Success thresholds? → Beat the original on the same path and PC, with the same
      look (screenshot comparison); no fixed multiplier.
- [x] Platforms? → Windows and Linux.
- [x] Stack? → Rust + Vulkan 1.3 via `ash`, as swjkja.
- [x] License and visibility? → Public from day one, GPLv3. Plus a progress GitHub page
      and a `docs/OVERVIEW.md`, both like swjkja's.
- [x] Minimum hardware? → Integrated GPUs (Intel HD 630 / Steam Deck class), if
      possible; testing is limited to the owner's PC.
- [x] How is "smaller" achieved? → An import step converts Heat's data into nfwh's own
      compact format; the original install can then be removed. Size is measured against
      the original install.
- [x] How is "more reliable" checked? → No dedicated check, but it must not crash: keep
      that in mind when coding.
- [x] How far may reverse engineering go? → Data files and the game executable
      (disassembly allowed, to match physics and logic).

## Risks and unknowns

- No source code: everything (formats, physics, handling, AI, rendering) has to be
  reverse engineered or reimplemented. Far larger than swjkja, which had a source port.
- Frostbite's data formats (superbundles, casc catalogs, EBX/RES) are undocumented
  officially; community tools exist but may be incomplete for Heat.
- Legal: the repo is public and the executable is disassembled. EA's EULA and the
  anti-tamper on the executable constrain this; decompiled EA code, game data and
  anything that bypasses protection must never be committed. Only the project's own
  descriptions of formats and behaviour go in the repo.
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
- 2026-10-30: round 2: Rust + ash, Windows and Linux, beat original with same look, public GPLv3, progress page and OVERVIEW.md.
- 2026-10-30: round 3: integrated-GPU target, compact converted data, no-crash priority, executable RE allowed.
