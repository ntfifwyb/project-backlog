---
title: Development Statistics
status: idea
created: 2026-11-18
updated: 2026-11-18
owner: ntfifwyb
repo:
tags: [cli, claude, github, stats]
stack: []
effort:
priority:
---

# Development Statistics

## Summary *

A terminal command, in the style of `autopilot` and `nightq` in claude-toolkit, that shows
a comprehensive list of the user's stats on Claude, GitHub, or development in general:
cost usage (even on a subscription, where there is no bill), tokens, and so on.

## Problem *

The numbers are scattered: Claude Code shows cost and context only for the current session
(the `statusline`), plan limits only while a session runs, and GitHub activity only on the
website. There's no single place to see totals and trends across all projects.

## Users and context

The user alone, on this machine (WSL), from any folder in a terminal.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- One terminal command with a live screen, like `nightq`'s (redrawn, keys switch views).
- Claude Code stats first: tokens and cost.
- Cost is shown only as the API-equivalent $ (what the tokens would cost at API prices).
  The subscription is implied; don't show its price or a comparison.

### Later

- GitHub stats, right after Claude Code.
- More sources beyond these two: the user doesn't want it limited to Claude and GitHub
  (candidates under Open questions).

### Not doing

- 

## Constraints

- Development costs $0 (workspace rule).
- Claude data comes from what's on disk (`~/.claude/projects/*/*.jsonl` transcripts,
  `~/.claude/stats-cache.json`) or what Claude Code hands its own hooks and status line;
  no automated scraping of claude.ai (see Policy).

## Decided

- It's a terminal command, like `autopilot` and `nightq`.
- Its own repo, `ntfifwyb/development-statistics`, installed onto PATH (not a tool in
  claude-toolkit/bin).
- Display: a live screen like `nightq`, not a one-shot printed report.

## Policy

**Allowed with limits** (checked 2026-11-18 against the Usage Policy, effective
2026-11-12, and the Consumer Terms). Reading the user's own local transcripts and their
own GitHub account is fine. Limit: Consumer Terms §3 forbids scraping the Services and
accessing them "through automated or non-human means" except via an API key, so the tool
must not log in to or scrape claude.ai for usage numbers. GitHub's API terms are a
separate question (not read).

## Open questions *

- [x] Own repo or claude-toolkit/bin? → Own repo under ntfifwyb.
- [x] MVP sources? → Claude Code first, then GitHub; not limited to those two.
- [x] Printed report or live screen? → Live screen like `nightq`.
- [x] Headline cost? → API-equivalent $ only; subscription implied, not shown.
- [ ] Which other sources? Candidates: local git across `~/organizations` (commits, lines
  changed), `local-ci` runs (pass/fail, duration), `nightq` and `autopilot` jobs,
  backlog briefs by status, time spent in Claude sessions.

## Risks and unknowns

- Subscription "cost" is an estimate at API prices; the price table must be kept current.

## First session

- 

## References

- `~/organizations/claude-toolkit/bin/statusline`: already computes session cost, cache
  hit and plan limits from Claude Code's status-line JSON.
- `~/.claude/stats-cache.json`: Claude Code's own daily message, session and tool-call counts.

## Log

- 2026-11-18: created.
- 2026-11-18: round 1: own repo, live screen, Claude Code first, API-equivalent cost.
