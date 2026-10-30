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

Personal curiosity: the user wants to understand the quantum Zeno effect properly, and a
course is the way to learn it.

## Users and context

- A learner with no quantum background, in a desktop web browser (GitHub Pages). The
  course teaches every quantum idea it uses (state, probability, measurement, evolution).

## Success criteria *

- [ ] After the course, a learner with no quantum background correctly predicts that
      measuring more often keeps the state from changing, and can say why (at short
      times the change grows quadratically, so frequent resets keep it near zero).

## Scope *

### Must (MVP)

- A GitHub Pages site that teaches the quantum Zeno effect.
- Main interactive view: a two-level state rotating (Rabi oscillation), interrupted by
  measurements the learner sets, beside a plot of survival probability vs. measurement rate.
- A short side note that "measurement" can be any strong interaction with the
  environment (decoherence); no density matrices.
- Math beside the pictures (amplitudes, the cos² survival formula), teaching the trig it uses.
- One lesson walks through a real experiment, Itano et al. 1990 (trapped beryllium ions,
  laser pulses as measurements), and its data.
- 5–7 lessons, about an hour. Lesson 1 shows the effect in the simulation before explaining
  it (paradox first); later lessons build the basics that explain it.
- Ideal, instantaneous measurements only.

### Later

- The anti-Zeno effect (frequent measurement speeding up decay).
- Quantum computing uses (Zeno-based error suppression, dynamical decoupling).
- Imperfect (weak) measurements, e.g. a measurement-strength slider.

### Not doing

- Anything beyond a learning page ("That's it").
- Quantum interpretations (Copenhagen, many-worlds, what "collapse" really is).
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
- Repo name: `quantum-zeno-effect`.
- Success: the learner predicts the effect and can say why.
- Decoherence: a short side note only.
- Math: shown beside the pictures (org rule), not picture-only.
- Problem: personal curiosity.
- MVP is complete as listed; interpretations Not doing; QC applications Later.
- Length: 5–7 lessons, about an hour. Opening: paradox first.
- Experiment: Itano et al. 1990.
- Weak measurements: Later; MVP uses ideal measurements.

## Open questions *

- [x] Repo name? → `quantum-zeno-effect`.
- [x] Learner level? → No quantum background.
- [x] Interactive simulation of what? → Rotating two-level state interrupted by
      measurements, beside a survival probability vs. measurement rate plot.
- [x] Anti-Zeno effect in MVP? → Later.
- [x] Real experiments? → Yes, one lesson.
- [x] Measurement vs. decoherence? → A short side note, no density matrices.
- [x] Math or picture-only? → Math beside the pictures.
- [x] Success criteria? → Learner predicts the effect and can say why.
- [x] MVP complete as listed? → Yes.
- [x] Interpretations? → Not doing.
- [x] Quantum computing applications? → Later.
- [x] Course length? → 5–7 lessons, about an hour.
- [x] Opening? → Paradox first.
- [x] Which experiment? → Itano et al. 1990.
- [x] Weak measurements? → Later.

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
- 2026-10-30: round 2: repo name, success criterion, decoherence note, math shown.
- 2026-10-30: round 3: problem (curiosity), MVP confirmed, interpretations out, QC uses Later.
- 2026-10-30: round 4: length, paradox-first opening, Itano 1990, weak measurements Later.
