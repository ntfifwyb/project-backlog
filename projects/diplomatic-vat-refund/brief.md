---
title: Diplomatic VAT Refund
status: idea
created: 2026-11-05
updated: 2026-11-05
owner: ntfifwyb
repo:
tags: [germany, diplomacy, vat, automation, research]
stack: []
effort:
priority:
---

# Diplomatic VAT Refund

## Summary *

Automate as much as possible of the VAT reimbursement process for diplomatic entities in Germany (missions and their members, who reclaim VAT from the Bundeszentralamt für Steuern, BZSt). The work starts with research and data; the project gets built on that research afterwards.

## Problem *

Refund applications are built by hand from a year of receipts, each of which has to be checked against the refund rules, listed on the BZSt form and backed by a proof of payment.

A working prototype already exists outside the backlog (see References), so part of this is already automated. Its ruleset has open points that couldn't be verified from public sources.

## Users and context

Diplomatic entities in Germany: the mission itself (form 010160) and its members (form 010161). Applications are prepared throughout the year and must reach BZSt by 31 December of the following year.

## Success criteria *

- [ ] (Not defined yet.)

## Scope *

### Must (MVP)

- Research and data first; the build follows from them.

### Later

- The project itself, built on the research.

### Not doing

- (Not settled yet; see the proof-of-payment question.)

## Constraints

- Reading someone's bank statements to find proofs of payment is, in the user's words, not possible "at least safe". The user expects that only the data-gathering part can be automated.
- The backlog is public: no real receipts, mission details or reciprocity terms in this brief or its refs.

## Decided

- Research and data come before the build.

## Open questions *

- [ ] Is this a continuation of the existing prototype, or a new build that only reuses its findings?
- [ ] What does the research cover, and what does it produce?
- [ ] What data is gathered, and may it include real receipts?
- [ ] How far does automation go on proof of payment?

## Risks and unknowns

- The prototype's own list of unverified points: country-specific reciprocity terms; Auswärtiges Amt Rundnoten 14/2018, 39/2020, 01/2022 and 3/2024, which aren't public; whether BZSt applies the €100 minimum to the invoice total or to the refundable part.

## References

- Prototype, local only and not a git repo: `C:\Users\tb\Desktop\projects\PCATR` (app name DIVAR, internal name PCATR, v2.3.0). A local web app that reads receipts with Claude, checks them against rules R01–R30 and pre-fills page 3 of the forms; pages 1–2 stay manual. Its `docs/RULES.md` is the ruleset with sources. On 2026-11-05 `node tests/test_rules.js` passed 31 of 31; the app itself wasn't run.
- UStErstV: https://www.gesetze-im-internet.de/usterstvo/BJNR003160970.html
- BZSt procedure: https://www.bzst.de/DE/Behoerden/Botschaft_Konsulat/Botschaften/botschaften.html
- Auswärtiges Amt Protokoll-Richtlinien 2.4.1 and 2.4.2: https://protokoll.diplo.de/protokoll-richtlinien-de/protokollrichtlinien/02-rechtundsteuern/03-umsatzsteuer/2456534-2456534
- Forms: https://www.formulare-bfinv.de/ffw/action/invoke.do?id=010160 and https://www.formulare-bfinv.de/ffw/action/invoke.do?id=010161

## Log

- 2026-11-05: created.
