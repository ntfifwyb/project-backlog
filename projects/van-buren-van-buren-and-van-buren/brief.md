---
title: Van Buren, Van Buren & Van Buren
status: ready
created: 2026-11-20
updated: 2026-11-20
owner: ntfifwyb
repo:
tags: [game, mod, garrys-mod, roleplay, multiplayer]
stack: [garrys-mod, lua]
effort:
priority:
---

# Van Buren, Van Buren & Van Buren

## Summary *

A Garry's Mod gamemode for office roleplay. Players work in a corporate firm and talk to
each other over voice chat in an *American Psycho*-style register: vain, status-obsessed,
over-polished business talk. The players make the dialogue up themselves; the mod doesn't
script it. The work is deliberately pointless, like the bullshit tasks of a consulting
agency. The mod is named after the firm: Van Buren, Van Buren & Van Buren, the same family name three times as a nepotism joke.

## Problem *

There's no gamemode built around corporate satire. Office roleplay in Garry's Mod today
means bending a general RP gamemode like DarkRP to fit, so there's no in-game work that
feeds the joke.

## Users and context

- Garry's Mod players on multiplayer servers, roleplaying through in-game voice chat.

## Success criteria *

- [ ] When one player starts the gamemode on a listen server, they can play every MVP minigame, get paid, and climb the promotions ladder by themselves. Multiplayer comes after.

## Scope *

### Must (MVP)

- Standalone gamemode derived from Garry's Mod's `base` gamemode (not DarkRP).
- Four bullshit-task minigames, each short and paying out: a pointless spreadsheet, aligning
  a slide deck, shredding, faxing.
- 1980s Wall Street look: beige computers, CRTs, power suits, pastel business cards.
- Promotions ladder, with rank-ups from 'billable hours' earned by tasks plus a review: a
  threshold, then a superior's sign-off in multiplayer (automatic in solo play). E.g. Intern → Analyst → Associate → VP → Partner, with perks such as
  better offices and business cards.
- A custom office map: cubicles, corner offices, a conference room, with offices that fit the ladder's perks.
- Status purchases: suits, watches, business cards, restaurant reservations. Pure flex.
- Custom 1980s assets: our own models and textures (CRTs, fax machines, shredders, etc.).

### Later

- Multiplayer polish beyond the solo-playable MVP.
- Steam Workshop release.
- Office politics, once solo play works: players compete for promotion (e.g. taking credit
  for others' tasks, sabotage, a limited Partner seat).
- More minigames.

### Not doing

- Scripted or AI-generated dialogue: the players speak over voice chat.
- DarkRP as the base.
- Steam Workshop for now: GitHub only until it's polished.

## Constraints

- Anthropic Usage Policy (checked 2026-11-20, effective 2026-11-12): **allowed with
  limits.** Keep it non-sexual. Aim the satire at corporate absurdity, not at real people,
  groups or real companies (no impersonating them). No copied copyrighted assets or code.
  If voice or player data is ever recorded or stored, the privacy rules apply. If AI NPCs
  are ever added, they must disclose that they're AI. If minors are expected to play, the
  policy for products serving minors applies.
- Third-party risk (the user's call): *American Psycho* is a copyrighted novel and film.
  Borrow its tone, not its names (Pierce & Pierce, Patrick Bateman), quotes or likenesses.
  Garry's Mod and Steam Workshop terms apply when the mod is published.
- Development costs $0.

## Decided

- Garry's Mod gamemode, standalone, derived from `base`.
- Tasks are small absurd minigames that pay out.
- Progression is a promotions ladder with perks.
- Dialogue comes from the players over voice chat.
- Solo playable first: the MVP is done when one player can play everything alone.
- Custom office map, not existing workshop maps.
- Money buys status items as well as counting toward promotion.
- Competitive office politics between players, built after the solo MVP.
- Custom 1980s models and textures, not stock GMod/HL2 props.
- Code licence: MIT.
- MVP minigames: spreadsheet, slide deck, shredder, fax.
- Look: 1980s Wall Street.
- Promotion: billable hours from tasks plus a review (a superior's sign-off in multiplayer, automatic solo).
- Published on GitHub only for now.
- Name: Van Buren, Van Buren & Van Buren; repo `van-buren-van-buren-and-van-buren`.

## Open questions *

- [x] Name? → Van Buren, Van Buren & Van Buren (the same family name three times as a nepotism joke). Rejected: Hargrove & Whitcombe, Vantage Synergy Partners, Sterling Ashford & Crane, Blackwood Meridian Group, Pemberton Hale LLP, Apex Strategic Solutions, and Whitfield (the user liked the triple-name style, just not that surname).
- [x] How do tasks work? → Small absurd minigames (spreadsheets, slide decks, shredding, faxing) that pay out.
- [x] Hierarchy? → Promotions ladder (Intern → … → Partner) with perks.
- [x] When is the MVP done? → Solo playable first: one player can play every minigame and climb the ladder.
- [x] Map? → Custom office map.
- [x] Economy? → Status purchases (suits, watches, cards, reservations).
- [x] Rivalry? → Yes: office politics, players compete for promotion.
- [x] MVP minigames? → Four: spreadsheet, slide deck, shredder, fax.
- [x] Look? → 1980s Wall Street.
- [x] Promotion? → Billable hours from tasks plus a review (sign-off in multiplayer, automatic solo).
- [x] Release? → GitHub only for now.
- [x] Assets? → Custom 1980s models and textures.
- [x] Licence? → MIT.
- [x] First session? → Map blockout first.
- [x] Office politics in the MVP? → No, after the solo MVP.
- [x] Base? → Standalone gamemode derived from `base`, not DarkRP.

## Risks and unknowns

- Custom models, textures and a custom map are the slowest part. Grey-box first and put the
  assets in once the loop works.
- Map and model tools (Hammer, a 3D modeller) and Garry's Mod run on Windows, but this
  machine works in WSL. Testing means opening windows on the user's desktop: ask first.

## First session

- A grey-box blockout of the office floor in Hammer: cubicles, corner offices, conference
  room, and spots for the four minigame stations. It loads in Garry's Mod. No gameplay code yet.

## References

- https://www.anthropic.com/legal/aup: the Usage Policy behind the verdict above.

## Log

- 2026-11-20: created. Policy check: allowed with limits. Round 1: tasks, hierarchy, base.
- 2026-11-20: named Van Buren, Van Buren & Van Buren (renamed from office-roleplay-gamemode).
- 2026-11-20: round 2: solo-first MVP, custom map, status shop, office politics.
- 2026-11-20: round 3: four minigames, 1980s look, billable-hours promotion, GitHub only.
- 2026-11-20: round 4: custom assets, MIT, map blockout first, politics after the MVP.
- 2026-11-20: idea → ready
