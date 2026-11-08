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
- A Mermaid diagram of the web (AI at the centre), followed by a short section per group
  with the actual links.
- Private projects are named in their group with no repo link.
- Groups with no project yet (e.g. Cybersecurity, Math) appear marked "coming soon".
- Above the web: a one-line intro plus contact links.

### Later

- Each private project gets a dedicated public GitHub page explaining what it is; the
  README then links to that page instead of a repo.

### Not doing

- The real portfolio website (a separate, future idea).
- Auto-generated widgets (stats cards, streaks, language charts, badges).
- Automated updates: the list is edited by hand.

## Constraints

- Development costs $0.

## Decided

- Plain Markdown, no third-party widgets.
- The project list is edited by hand.
- The web is a Mermaid diagram, with linked group sections below it.
- Private projects are listed by name, unlinked until their dedicated page exists.
- Empty groups are shown as "coming soon".
- Intro: one line plus contact links.
- Repo is `ntfifwyb/ntfifwyb`: GitHub only shows a profile README from a public repo named
  exactly after the account. This is why the name isn't a kebab-case full name.

## Open questions *

- [x] Widgets? → None: plain Markdown only.
- [x] How does the list stay current? → Edited by hand.
- [x] Success criterion? → Readable in about 10 seconds, on about one screen.
- [x] How to draw the "spider's web"? → Mermaid diagram with AI at the centre, plus a
      linked section per group below it.
- [x] Private projects? → Named, unlinked; later linked to a dedicated public page each.
- [x] Empty groups? → Shown as "coming soon".
- [x] What's above the web? → One-line intro plus contact links.
- [ ] Which contact links, and the wording of the intro line?
- [ ] What form does a private project's "dedicated GitHub page" take (a GitHub Pages
      site, or a small public showcase repo)?
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
- 2026-11-08: round 2 answers (Mermaid web, private projects unlinked, "coming soon" groups, intro + contacts).
