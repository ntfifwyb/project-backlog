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

- [ ] Every factual claim on the site links to a source in the research dossier.
- [ ] A curious adult with no biology background who finishes the lessons can do the final
      quiz's tasks without help.

## Scope *

### Must (MVP)

- Multi-lesson course, in depth: everything known about the tiger.
- A research phase done by Claude before the site is built: a cited dossier in
  `docs/research/`, one file per topic, every claim tied to a source (IUCN, peer-reviewed
  papers), disagreements between sources noted. The user reviews it before the lesson outline.
- Topics: all the science (taxonomy, evolution, body, senses, hunting, behaviour, life cycle,
  subspecies, range, ecology, conservation) and the culture (tigers in history, myth, art,
  and the trade in tiger parts).
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
- Breadth: science and culture.
- Research: a cited dossier in `docs/research/`, reviewed by the user before the outline.

## Open questions *

- [x] Who is the learner? → A curious adult, no biology background assumed.
- [x] Where do quizzes go? → At the end of each lesson, plus a final quiz.
- [x] What kind of interactive quiz? → Hands-on tasks (map, stripe matching, ordering, estimate sliders).
- [x] Scores? → No, the org's no-score rule stands. Answers are revealed and explained.
- [x] Breadth? → Science and culture.
- [x] What does the research produce? → A cited dossier per topic in `docs/research/`, user-reviewed before the outline.
- [x] Success criteria? → All facts sourced; a finisher can do the final quiz unaided.
- [ ] Lesson order? User said "both" to (a) topical, body out to world, and (b) following one
      tiger's life. How to combine them is still open (see next round).
- [ ] Exact lesson list: settled in `docs/LESSONS.md` after the dossier (org rule: outline approved first).

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
- 2026-11-15: round 2: breadth, research dossier, success criteria; lesson order is "both".
