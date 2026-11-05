---
title: Diplomatic VAT Refund
status: idea
created: 2026-11-05
updated: 2026-11-05
owner: ntfifwyb
repo:
tags: [germany, diplomacy, vat, automation, research]
stack: [tauri, typescript, sqlite, python]
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

- [ ] Every rule in the rulebook cites a primary source or is marked unverified.
- [ ] When the model test runs on the 200 labelled synthetic receipts, the chosen model reads total, VAT, rate, date and supplier with at least 98% accuracy.

## Scope *

### Must (MVP)

- Research and data first; the build follows from them.
- Deliver a cited rulebook, a labelled synthetic receipt set, model test results and a statement-matching study, and an automation map of the refund process.

### Later

- The app, built on the research: a Tauri, TypeScript and SQLite app on the mission's PC, in English, German and Spanish, using each mission's own AI key. It pre-fills all form pages, keeps phone upload over local Wi-Fi and encrypts records with a password.
- Pricing, after a free start.
- Mac support, if a mission needs it.

### Not doing

- Separate logins for members in the first release.
- Connecting to anyone's bank. Proof-of-payment research covers only a statement file the person exports.
- Real receipts during the research phase.
- Sending bank statements to an AI.

## Constraints

- Reading someone's bank statements to find proofs of payment is, in the user's words, not possible "at least safe". The user expects that only the data-gathering part can be automated.
- The backlog is public: no real receipts, mission details or reciprocity terms in this brief or its refs.

## Decided

- Research and data come before the build.
- This is a rebuild from the research. DIVAR is reference material, not the starting code.
- The research focuses first on rules and process.
- The research starts with public sources and synthetic receipts only.
- The user wants the DeepSeek API, but only if its OCR reading and understanding are good enough; the model should stay fairly cheap.
- Exported bank statements are matched locally by plain code and never go to an AI.
- The repo starts private.
- The rulebook covers the general rules and the first mission's country terms, in English with German legal quotes.
- Test tools are written in Python; the app is built with Tauri, TypeScript and SQLite.
- The app runs on the mission's PC and uses the mission's own AI key.
- The app ships in English, German and Spanish.
- The app pre-fills all form pages, keeps phone upload over local Wi-Fi and encrypts its records with a password.
- The app is free at first.
- The first release is for Windows, with one operator on one PC.
- Clean receipts are approved in bulk by a person, with a log; flagged ones are opened individually.
- Updates come from a signed public feed and install only after approval.
- The model test may spend up to $10 of API credit.
- Only DIVAR's `docs/RULES.md` and rule tests carry over, as reference.
- Each mission approves the AI company before any of its real receipts are uploaded.
- A blind test chooses the model: the cheapest that reaches 98% on total, VAT, rate, date and supplier.

## Open questions *

- [x] Is this a continuation of the existing prototype, or a new build that only reuses its findings? → A rebuild from the research; DIVAR is reference material.
- [x] What does the research cover first? → Rules and process.
- [x] What data is gathered at the start? → Public sources and synthetic receipts, no real receipts.
- [x] How far does automation go on proof of payment? → Research matching invoices against a statement file the person exports, with no connection to the bank.
- [x] How is the receipt-reading model chosen? → A blind test of DeepSeek Flash, Claude Haiku 5.5, Gemini on a Vertex EU region and Claude Sonnet 5.5 as a reference; the cheapest that passes wins. Evidence: `refs/model-advice-2026-11.md`.
- [x] What is the model's pass mark? → 98% correct on total, VAT, rate, date and supplier.
- [x] Where may real receipts be sent? → Only to an AI company the mission has approved before any upload; the app names where receipts go. DeepSeek stays possible.
- [x] What does the research deliver? → A cited rulebook, a labelled synthetic receipt set, model test results and a statement-matching study, and an automation map of the refund process.

- [x] When is the rulebook research finished? → When every rule cites a primary source or is marked unverified.
- [x] How large is the model test set? → 200 labelled synthetic receipts, including faded, crumpled and long-receipt variants.
- [x] How is an exported bank statement handled? → Matched on the PC by plain code; no statement goes to an AI.
- [x] Is the repo private or public? → Private for now.

- [x] Does the rulebook cover country-specific reciprocity terms? → Yes: the general rules plus one country's terms, that of the first mission. The country and its terms stay out of this public brief; they go in the private repo.
- [x] What language is the rulebook in? → English, with legal wording quoted in the original German.
- [x] What are the test tools written in? → Python.
- [x] What carries over from DIVAR? → `docs/RULES.md` and the rule tests as reference only; no app code, executable or access token.

- [x] Which country's terms are researched? → The user has chosen; the name goes in the private repo's first handoff, not this public brief.
- [x] What is the model test budget? → Up to $10 of API credit; the user supplies a key for each provider.
- [x] Which EU-hosted candidate is tested? → Gemini on a Vertex EU region. Its price and EU hosting still need checking against official pages.
- [x] Does the research map the process? → Yes: each step of the refund process is marked automatic, assisted or manual.

- [x] Where does the app run? → On the mission's PC, with records stored locally.
- [x] What is the app built with? → Tauri, TypeScript and SQLite. The research tools stay in Python, so their logic is rewritten for the app.
- [x] Who pays for and connects to the AI model? → Each mission, with its own API key for its approved provider.
- [x] Which languages does the app ship with? → English, German and Spanish.

- [x] How much of the BZSt forms does the app fill in? → Pre-fills all pages from saved mission and member details; people still check, sign and certify on paper.
- [x] Does the app keep phone upload? → Yes: QR code and upload over local Wi-Fi, through a small protected server.
- [x] How are local records protected? → Encrypted with a password; a recovery key guards against a forgotten one.
- [x] How is the app offered? → Free at first; pricing can come later.

- [x] Which computers does the first release support? → Windows first; Mac later if a mission needs it.
- [x] How do several people use the app? → One operator on one PC handles the mission and all members.
- [x] How are clean receipts reviewed? → A person approves them in bulk with one logged action and opens only flagged ones.
- [x] How does the app receive updates? → It checks a signed public release feed and installs only after approval.

## Risks and unknowns

- The prototype's own list of unverified points: country-specific reciprocity terms; Auswärtiges Amt Rundnoten 14/2018, 39/2020, 01/2022 and 3/2024, which aren't public; whether BZSt applies the €100 minimum to the invoice total or to the refundable part.

## References

- `refs/model-advice-2026-11.md`: desk research on prices, image limits and privacy for the receipt-reading model; no model tested yet.
- Prototype, local only and not a git repo: `C:\Users\tb\Desktop\projects\PCATR` (app name DIVAR, internal name PCATR, v2.3.0). A local web app that reads receipts with Claude, checks them against rules R01–R30 and pre-fills page 3 of the forms; pages 1–2 stay manual. Its `docs/RULES.md` is the ruleset with sources. On 2026-11-05 `node tests/test_rules.js` passed 31 of 31; the app itself wasn't run.
- UStErstV: https://www.gesetze-im-internet.de/usterstvo/BJNR003160970.html
- BZSt procedure: https://www.bzst.de/DE/Behoerden/Botschaft_Konsulat/Botschaften/botschaften.html
- Auswärtiges Amt Protokoll-Richtlinien 2.4.1 and 2.4.2: https://protokoll.diplo.de/protokoll-richtlinien-de/protokollrichtlinien/02-rechtundsteuern/03-umsatzsteuer/2456534-2456534
- Forms: https://www.formulare-bfinv.de/ffw/action/invoke.do?id=010160 and https://www.formulare-bfinv.de/ffw/action/invoke.do?id=010161

## Log

- 2026-11-05: created.
- 2026-11-05: first round: rebuild from research, rules and process first, public and synthetic data, research statement matching, DeepSeek preferred if good enough.
- 2026-11-05: added desk research on the receipt-reading model.
- 2026-11-05: second round: blind test, 98% pass mark, research deliverables; real-receipt destination still open.
- 2026-11-05: each mission approves the AI company that receives its real receipts.
- 2026-11-05: third round: rulebook finish line, 200 test receipts, local statement matching, private repo.
- 2026-11-05: fourth round: one country's reciprocity terms, English with German quotes, Python tools, rules and tests carried over from DIVAR.
- 2026-11-05: fifth round: country chosen, $10 test budget, Gemini as the EU candidate, automation map added.
- 2026-11-05: sixth round: local app, Tauri with TypeScript and SQLite, each mission's own AI key, three languages.
- 2026-11-05: seventh round: pre-fill all pages, keep phone upload, password encryption, free at first.
- 2026-11-05: eighth round: Windows first, one operator, bulk approval of clean receipts, signed update feed.
