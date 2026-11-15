---
title: Panthera tigris
status: idea
created: 2026-11-15
updated: 2026-11-15
owner: instructional-pages
repo: instructional-pages/panthera-tigris
tags: [course, biology, animals]
stack: []
effort:
priority:
---

# Panthera tigris

## Summary *

A multi-lesson, in-depth browser course about the tiger (*Panthera tigris*): "everything
possible known about a tiger". It joins the other `instructional-pages` courses and follows
their shared rules. Claude researches the subject thoroughly before any of the website is built,
and the course includes interactive quizzes, "not just questions and answers".

## Problem *

There's no single place that teaches everything known about tigers in depth, as a guided,
interactive course rather than an encyclopedia page.

## Users and context

- Desktop browser, English, static site (org rules).
- Learner: a curious adult with no biology background. Every term is taught, but the depth goes all the way down.

## Success criteria *

- [ ] (open: see Open questions)

## Scope *

### Must (MVP)

- Multi-lesson course, in depth: everything known about the tiger.
- A research phase done by Claude before the site is built, with its findings and sources
  kept in the repo.
- Interactive quizzes, more than plain question-and-answer: a short check closes every
  lesson and a bigger mixed quiz closes the course. They are hands-on tasks (drag ranges
  onto a map, match stripe patterns to individual tigers, order the steps of a hunt, set a
  slider to estimate a number), answered first and then revealed and explained. No score.

### Later

- 

### Not doing

- Everything in the `instructional-pages` org's Not doing list (no accounts, backend,
  saved progress, analytics, ads, gamification; English only; desktop first).

## Constraints

- **Anthropic policy: allowed, with limits** (Usage Policy effective 2026-11-12, checked
  2026-11-15). Educational content is explicitly outside the high-risk categories. Limits:
  (1) no false or misleading science, so every fact (populations, subspecies taxonomy,
  conservation status) is verified against cited sources; (2) no IP infringement, so only
  self-made or openly licensed images, with credits; (3) poaching and attacks are covered
  factually, without graphic or gratuitous content; (4) if an AI tutor/chatbot is ever
  added it must say it's AI (static lessons and scripted quizzes don't trigger this).
- Org rules (`~/organizations/instructional-pages/CLAUDE.md`): predict-then-reveal checks,
  no scores, points or badges, no third-party requests at runtime, MIT, $0.

## Decided

- Name: `panthera-tigris`, the tiger's Latin (scientific) name, as the user asked.
- Format: multi-lesson course, in depth.
- Claude does extensive research before building the website.
- Quizzes are interactive, not just questions and answers.
- Learner: curious adult, no biology background assumed.
- Quizzes: one at the end of each lesson plus a final one; hands-on tasks; no score (org rule kept).

## Open questions *

- [x] Who is the learner? → A curious adult, no biology background assumed.
- [x] Where do quizzes go? → At the end of each lesson, plus a final quiz.
- [x] What kind of interactive quiz? → Hands-on tasks (map, stripe matching, ordering, estimate sliders).
- [x] Scores? → No, the org's no-score rule stands. Answers are revealed and explained.
- [ ] Topic list and lesson order.
- [ ] Success criteria.

## Risks and unknowns

- Facts disagree between sources (subspecies count after the 2017 IUCN revision, wild
  population figures). The research has to record which source it follows and why.
- Openly licensed tiger images and video may be limited. Self-drawn illustrations or
  diagrams may have to replace photos.

## First session

- 

## References

- `~/organizations/instructional-pages/CLAUDE.md`: shared course rules.
- https://www.anthropic.com/legal/aup: the policy checked on 2026-11-15.

## Log

- 2026-11-15: created from the user's description.
- 2026-11-15: round 1: learner, quiz placement, quiz style, no scoring.
