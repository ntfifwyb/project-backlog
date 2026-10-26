---
title: Shared shopping list
status: ready
created: 2026-10-26
updated: 2026-10-26
owner: ntfifwyb
repo:
tags: [household, mobile, offline]
stack: [pwa, typescript]
effort: M
priority: 2
---

# Shared shopping list

An example of a finished brief at status `ready`. It's not a real project: copy the
level of detail, not the content.

## Summary

A shopping list that two people in one household edit from their phones, works with no
signal in the supermarket, and merges cleanly afterwards. For people who now use a chat
thread and lose items in it.

## Problem

Lists live in a chat thread. Items get buried, nobody knows what's already bought, and
two people buy the same thing. Existing apps want an account per person and show ads.

## Users and context

Two adults, Android and iPhone, mostly in supermarkets with poor reception. Used several
times a week, for a few minutes at a time.

## Success criteria

- [ ] When both phones are offline and each adds items, both lists show every item within 5 s of reconnecting, with no duplicates.
- [ ] When an item is ticked on one phone, it shows as ticked on the other within 5 s (both online).
- [ ] Installs from the browser as an app (PWA) on Android Chrome and iOS Safari, with no app store.
- [ ] Joining a list takes one link or QR code, with no account or password.
- [ ] Hosting costs $0 at two users.

## Scope

### Must (MVP)

- One shared list per household, joined by link.
- Add, tick, untick, delete items; ticked items sink to the bottom.
- Offline edits that sync on reconnect (CRDT, so there are no merge conflicts).

### Later

- Several lists (supermarket, pharmacy).
- Item suggestions from past lists.

### Not doing

- Prices, budgets, recipes or store maps.
- Accounts, social features, ads.

## Constraints

- Development and hosting cost $0 at this scale (free tiers only).
- No personal data beyond item names; nothing is sold or shared.

## Decided

- PWA, not native apps: one codebase and no store review.
- Repo: `ntfifwyb/shared-shopping-list`, private.

## Open questions

- [x] Sync backend or peer-to-peer? → A tiny relay on a free tier: peer-to-peer fails when one phone is asleep.
- [x] Which CRDT library? → Yjs: mature, small, works offline with IndexedDB.

## Risks and unknowns

- iOS Safari evicts PWA storage after weeks without use. Find out in the first session whether that loses unsynced items.

## First session

- A deployed PWA where two browser tabs share one list through the relay, offline edits included, with the sync test automated.

## References

- refs/screenshot-chat-thread.png: what the current workaround looks like.

## Log

- 2026-10-26: created.
- 2026-10-26: open questions answered; status ready.
