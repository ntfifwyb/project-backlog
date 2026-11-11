---
title: Ant Colony Simulation
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [simulation, web]
stack: []
effort:
priority:
---

# Ant Colony Simulation

## Summary *

An ant colony simulation that runs as a webpage, made to be watched. The goal is for it to
be as realistic as possible, based on what has been studied about ants: biologically
detailed behavior, not just simple rules. It must be fast and use little to no RAM.

## Problem *

To be filled in: what the simulation is for (watching, learning, playing) and what's
missing from existing ones.

## Users and context

- Runs in a web browser.
- The viewer watches; they don't play. Interaction is settings only (no drawing on the map).

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- An ant colony simulation in a webpage, made for watching.
- Biologically detailed behavior, as realistic as the ant research allows.
- Colony size: realistic for the species simulated (the user accepts ~10,000 as a fallback).
- Viewer controls are settings only.

### Later

- 

### Not doing

- A game: no goals, no win or lose conditions.
- Painting the world (placing food or walls with the mouse).

## Constraints

- Fast, with little to no RAM use.
- Development costs $0 (workspace rule).
- Policy check (Anthropic Usage Policy, read 2026-11-11): **allowed**. A client-side
  simulation with no personal data falls under no restricted use. If it ever calls the
  Claude API, the Usage Policy applies to those calls.

## Decided

- Platform: a webpage.
- Purpose: watching, as realistic as studied ant biology allows.
- Realism: biologically detailed, not just simple emergent rules.
- Interaction: settings only.

## Open questions *

- [x] What is it for? → Watching, as realistic as possible with what has been studied about ants.
- [x] How realistic? → Biologically detailed.
- [x] How many ants? → Whatever is realistic: the average colony size. If the user doesn't like that number, ~10,000.
- [x] What can the viewer do? → Settings only.

## Risks and unknowns

- 

## First session

- 

## References

- 

## Log

- 2026-11-11: created.
- 2026-11-11: round 1: purpose, realism, scale, interaction.
