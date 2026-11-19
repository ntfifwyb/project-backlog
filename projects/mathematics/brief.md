---
title: Mathematics
status: ready
created: 2026-11-19
updated: 2026-11-19
owner: prsnlanki
repo: prsnlanki/mathematics
tags: [anki, education, mathematics]
stack: [python, genanki]
effort:
priority:
---

# Mathematics

## Summary *

A mathematics Anki deck, `Mathematics` in Anki, built like the user's other prsnlanki decks
(deutsch, english, espanol, esperanto): one repo, one subdeck folder per kind of card,
packaged into one `.apkg`. It starts with one subdeck, **Multiplication**
(`Mathematics::Multiplication`), so the user knows the multiplication tables instantly.

## Problem *

The user wants to recall multiplication facts instantly instead of working them out. There's
no deck for it among their Anki decks today.

## Users and context

Just the user, in Anki (desktop and phone). Public repo, so others can download it too.

## Success criteria *

- [ ] Importing `Mathematics.apkg` into Anki creates `Mathematics::Multiplication` with 865 notes: 361 products, 361 divisions, 143 factoring cards.
- [ ] Re-importing a newer build updates the existing cards instead of duplicating them (stable GUIDs).
- [ ] On a product or division card, typing a wrong answer shows it as wrong, and the card shows the seconds elapsed since it appeared.
- [ ] With new cards in deck order, the 2–10 table's product cards all come before any 13–19 product card.

## Scope *

### Must (MVP)

- Subdeck **Multiplication**, range 2–20 × 2–20, with three kinds of card:
  - **Product:** a × b = ? → typed answer. Both orders are separate cards (7×8 and 8×7): 361 cards.
  - **Division** (the missing-factor fact, written as division): ab ÷ a = ? → b, typed. One per ordered pair: 361 cards.
  - **Factoring:** product → all its factor pairs within 2–20 (36 → 2×18, 3×12, 4×9, 6×6), self-graded (answer in your head, flip). One per distinct product: 143 cards, 110 of them with only one pair.
- A timer on the product and division cards that just shows elapsed seconds (no limit, no colours).
- New cards come easiest first: the 2–10 table, then ×11/×12/×15/×20, then the hard 13–19 facts. Each fact's division card arrives a few days after its product card.
- Same repo structure as the other decks: `build.py` with `PARTS`, `CHANGELOG.md`, `scripts/publish.sh` + `check-release-links.sh`, `.local-ci`, GitHub Releases with the `.apkg`, a row in anki-setup's README Decks table.

### Later

- Other mathematics subdecks (the user will name them).

### Not doing

- Audio.
- A speed limit or colour on the timer.
- Prime factorisation cards.

## Constraints

- Follow anki-setup's `FLASHCARD_GUIDE.md` and the prsnlanki deck conventions (see deutsch's `CLAUDE.md`).
- $0 development: local-ci, no GitHub Actions.

## Decided

- Repo `prsnlanki/mathematics`, folder `~/organizations/prsnlanki/mathematics`, public, with releases.
- Deck named in English: `Mathematics::Multiplication`.
- Range 2–20 × 2–20; both orders as separate cards.
- Products and divisions typed; factoring self-graded.
- Timer shows elapsed time only.
- New cards easiest first; division a few days after the product.
- Anthropic Usage Policy (effective 2026-11-12), checked 2026-11-19: **allowed**. Educational content, no restricted use.

## Open questions *

- [x] Range? → 2–20 × 2–20.
- [x] 7×8 and 8×7 separate? → Yes, both orders.
- [x] Other directions? → Missing factor and factoring a product.
- [x] How to answer? → Type, with a timer.
- [x] New-card order? → Easiest first.
- [x] Factoring cards? → All pairs, self-graded.
- [x] Timer behaviour? → Just show the time.
- [x] Deck name? → `Mathematics::Multiplication`.
- [x] Missing-factor format? → Written as division (56 ÷ 7 = ?).
- [x] Public with releases? → Yes.

## Risks and unknowns

- "Easiest first" needs a difficulty ranking within each band and a way to space a division card a few days after its product (new-card position or sibling burying); settle in the first session.
- A JavaScript timer must work in Anki desktop and AnkiDroid/AnkiMobile.

## First session

- Repo scaffold plus the Multiplication subdeck built, checked and published as v1.0.0.

## References

- `~/organizations/prsnlanki/deutsch`: the deck structure to copy.
- `~/organizations/prsnlanki/anki-setup/FLASHCARD_GUIDE.md`: card rules.

## Log

- 2026-11-19: created; questions answered in the same session; marked ready.
- 2026-11-19: idea → ready
