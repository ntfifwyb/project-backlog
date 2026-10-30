---
title: Quantum Zeno Effect
status: idea
created: 2026-10-28
updated: 2026-10-30
owner: instructional-pages
repo:
tags: [education, physics, quantum, web]
stack: []
effort:
priority:
---

# Quantum Zeno Effect

## Summary *

A GitHub Pages site where you learn about the quantum Zeno effect. Like
`higher-dimensions`, it is just a page for learning the topic, nothing more.
It goes under the user's instructional pages organization (`instructional-pages`).

## Problem *

Not yet described. The user will add detail in a later session.

## Users and context

- A learner with no quantum background, in a desktop web browser (GitHub Pages). The
  course teaches every quantum idea it uses (state, probability, measurement, evolution).

## Success criteria *

- [ ] Not yet decided (see Open questions).

## Scope *

### Must (MVP)

- A GitHub Pages site that teaches the quantum Zeno effect.
- Main interactive view: a two-level state rotating (Rabi oscillation), interrupted by
  measurements the learner sets, beside a plot of survival probability vs. measurement rate.
- One lesson walks through a real experiment (e.g. Itano et al. 1990, trapped ions) and its data.

### Later

- The anti-Zeno effect (frequent measurement speeding up decay).

### Not doing

- Anything beyond a learning page ("That's it").
- Everything in the org's Not doing list (`~/projects/instructional-pages/CLAUDE.md`).

## Constraints

- Development costs $0 (workspace rule). Free static hosting only.

## Decided

- Topic: the quantum Zeno effect.
- Form: a GitHub Pages site for learning about it, like `higher-dimensions`.
- GitHub owner: the `instructional-pages` organization. Its shared rules
  (`~/projects/instructional-pages/CLAUDE.md`) apply: guided lessons then a sandbox,
  predict-then-reveal, dark minimal look, TypeScript + Vite, MIT, no analytics, English.
- Learner: no quantum background; the course teaches the basics it needs.
- Simulation: rotating two-level state with learner-set measurements, plus a survival
  probability vs. measurement rate plot.
- Anti-Zeno effect: Later, not MVP.
- Experiments: one lesson on a real experiment.

## Open questions *

- [ ] Repo name? `quantum-zeno-effect` (suggested) or another full name.
- [x] Learner level? → No quantum background.
- [x] Interactive simulation of what? → Rotating two-level state interrupted by
      measurements, beside a survival probability vs. measurement rate plot.
- [x] Anti-Zeno effect in MVP? → Later.
- [x] Real experiments? → Yes, one lesson.
- [ ] Measurement vs. decoherence: covered, and how deeply?
- [ ] Success criteria?
- [ ] MVP / Later / Not doing in detail?

## Risks and unknowns

- 

## First session

- 

## References

- `instructional-pages/higher-dimensions`: the model this project follows (a learning page
  on GitHub Pages).

## Log

- 2026-10-28: created. Captured roughly; user will answer the open questions later.
- 2026-10-30: round 1: learner level, simulation, anti-Zeno (Later), one experiment lesson.
