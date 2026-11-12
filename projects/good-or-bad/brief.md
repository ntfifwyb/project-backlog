---
title: Good or Bad
status: idea
created: 2026-11-12
updated: 2026-11-12
owner: ntfifwyb
repo:
tags: [education, health, habits]
stack: []
effort:
priority:
---

# Good or Bad

## Summary *

A "classifier" app where the human is the classifier. The app shows one image at a time
(donuts, a salad, a hobby, an activity) and the person labels it **GOOD** or **BAD**.
Context does not matter: donuts are BAD, salad is GOOD, full stop. The point is for people
to learn what they're putting into their bodies, and the same idea applies beyond food, to
hobbies and other things.

## Problem *

People excuse choices with context ("donuts are good in context, for instance if you're
spending time with someone"). The app rejects that: each item is judged on its own, so
people learn what the thing itself does to them.

## Users and context

<!-- Not discussed yet. -->

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Show one image at a time; the person labels it GOOD or BAD.
- Items cover food first, but also hobbies and other things.
- Labels ignore context: each item has one answer, not "it depends".

### Later

- 

### Not doing

- Context-dependent answers ("good if you're with friends").

## Constraints

- Anthropic Usage Policy verdict (read 2026-11-12, AUP effective 2026-11-12): **allowed
  with limits**. Generic wellness/education content is excluded from the high-risk medical
  requirements, as long as labels aren't applied to the individual's own conditions,
  symptoms or medications. Limits: health claims must be accurate (no health
  misinformation); no body-weight or body-shape framing and nothing that encourages
  restriction, purging or compensatory exercise; if Claude talks to users, disclose it's
  AI; any stored per-user labels are health data (consent, clear data policy). Recheck if
  the app personalizes by health condition or is aimed at minors.

## Decided

- The human does the labelling; the app has a fixed GOOD/BAD answer per item, independent
  of context.

## Open questions *

- [ ] 

## Risks and unknowns

- Who decides the "right" answer for borderline items, and on what source, so labels stay
  accurate (see the policy limits above).

## First session

- 

## References

- [Anthropic Usage Policy](https://www.anthropic.com/legal/aup): basis for the verdict
  under Constraints.

## Log

- 2026-11-12: created.
