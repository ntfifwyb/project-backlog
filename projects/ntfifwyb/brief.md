---
title: GitHub Profile README
status: idea
created: 2026-11-08
updated: 2026-11-08
owner: ntfifwyb
repo: ntfifwyb/ntfifwyb
tags: [portfolio, github-profile]
stack: []
effort:
priority:
---

# GitHub Profile README

## Summary *

A minimalist portfolio shown on the user's GitHub profile page (https://github.com/ntfifwyb),
built as a GitHub profile README. It is not the user's actual portfolio: a separate portfolio
website is planned as a later, separate idea.

## Problem *

The GitHub profile page at https://github.com/ntfifwyb shows no curated overview of the user's
work today.

## Users and context

- Visitors to https://github.com/ntfifwyb.

## Success criteria *

- [ ] When someone opens https://github.com/ntfifwyb, they can tell who the user is and see
      the projects with links within about 10 seconds, on roughly one screen.

## Scope *

### Must (MVP)

- A minimalist portfolio rendered on https://github.com/ntfifwyb.
- Projects organised by groups, "sort of like a spider's web", with AI in the middle (the
  user's main focus; every project was built with appropriate use of AI). Groups the user
  named while brainstorming: Anki (plugins, decks), Entrepreneurship (portico), Games
  (ituzaingostudio), pedagogy / autodidacticism tools (adaptive-instructional-method,
  instructional-pages), Cybersecurity ("definitely"), Math ("maybe, in the future"),
  "and so on".

### Later

- 

### Not doing

- The real portfolio website (a separate, future idea).
- Auto-generated widgets (stats cards, streaks, language charts, badges).
- Automated updates: the list is edited by hand.

## Constraints

- Development costs $0.

## Decided

- Plain Markdown, no third-party widgets.
- The project list is edited by hand.
- Repo is `ntfifwyb/ntfifwyb`: GitHub only shows a profile README from a public repo named
  exactly after the account. This is why the name isn't a kebab-case full name.

## Open questions *

- [x] Widgets? → None: plain Markdown only.
- [x] How does the list stay current? → Edited by hand.
- [x] Success criterion? → Readable in about 10 seconds, on about one screen.
- [ ] How to draw the "spider's web"? Claude's suggestion: a diagram (Mermaid, rendered
      natively by GitHub, or a committed SVG) with AI at the centre, plus a short section
      per group with the actual links, since links inside diagrams aren't reliably
      clickable on GitHub.
- [ ] Final list of groups and which repos go in each (only public repos can be linked).

## Risks and unknowns

- The profile repo must be public; audit its content before the first push.

## First session

- 

## References

- GitHub docs, "Managing your profile README": https://docs.github.com/en/account-and-profile/setting-up-and-managing-your-github-profile/customizing-your-profile/managing-your-profile-readme

## Log

- 2026-11-08: created.
- 2026-11-08: round 1 answers (groups around AI, no widgets, hand-edited, 10-second criterion).
