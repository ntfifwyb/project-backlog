---
title: Ant Colony Simulation
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: simultrs
repo:
tags: [simulation, web]
stack: []
effort:
priority:
---

# Ant Colony Simulation

## Summary *

An ant colony simulation that runs as a webpage, made to be watched. There is one shared,
live colony: everyone who opens the page sees the same colony, and it runs for as long as
it lasts. Only the admin (the user) changes its parameters. People can also install their
own individual version and run their own colony. The goal is for it to
be as realistic as possible, based on what has been studied about ants: biologically
detailed behavior, not just simple rules. It must be fast and use little to no RAM.

## Problem *

Existing web ant simulations are not realistic: they are toy pheromone-trail demos, not
grounded in what field research has found about how real colonies live and work.

## Users and context

- Runs in a web browser.
- The viewer watches; they don't play. No drawing on the map.
- Desktop first: the performance target is for laptops; phones are best effort.
- Interface in English.

## Success criteria *

- [ ] When 12,000 ants are running on a mid-range laptop, the page holds 60 fps and its JS
  heap stays under 50 MB.
- [ ] Every behavior and default parameter in the simulation cites a study (in the repo and
  in an About panel).

## Scope *

### Must (MVP)

- An ant colony simulation in a webpage, made for watching.
- Biologically detailed behavior, as realistic as the ant research allows.
- Colony size: realistic for the species simulated (the user accepts ~10,000 as a fallback).
- One shared live colony: every visitor sees the same colony at the same moment. It runs
  until it ends naturally (however long that is).
- Only the admin can change the shared colony's parameters. Every research parameter
  (pheromone decay, task thresholds, and so on) is exposed to them, plus time speed.
- Built first: local mode, the individual version. The page runs its own colony in WASM in
  the browser, with the parameters under the viewer's control, installable as a PWA and
  offline-capable. No server.
- Then the shared colony: the same Rust core runs natively on an always-on free-tier VM
  and streams compact snapshots over WebSocket; viewers' browsers only render.
- One species: the red harvester ant (*Pogonomyrmex barbatus*, mature colonies of about
  10,000–12,000 workers). Species data is kept separate from the engine so more can be added.
- Every behavior and default parameter cites a study; an About panel lists the sources.
- Realistic look.
- Two views: the foraging surface above and the nest chambers below (queen, brood, tasks).
- The full colony life: founding queen, growth, maturity, with births, deaths and aging.

### Later

- A species picker with more species (the user wants the viewer to be able to choose).

### Not doing

- A game: no goals, no win or lose conditions.
- Painting the world (placing food or walls with the mouse).
- Analytics, tracking or cookies for visitors.
- Other interface languages.

## Constraints

- Fast, with little to no RAM use.
- License: MIT.
- Development costs $0 (workspace rule).
- Policy check (Anthropic Usage Policy, read 2026-11-11): **allowed**. A client-side
  simulation with no personal data falls under no restricted use. If it ever calls the
  Claude API, the Usage Policy applies to those calls.

## Decided

- Platform: a webpage.
- Purpose: watching, as realistic as studied ant biology allows.
- Realism: biologically detailed, not just simple emergent rules.
- Interaction: viewers watch; the admin sets every parameter of the shared colony.
- One shared, persistent colony for everyone, plus an installable individual version.
- Desktop first; English only; no analytics.
- Views: surface and nest.
- Timeline: full colony life, founding to maturity.
- MVP species: red harvester ant; a species picker comes later.
- Realism is checked by citations: every behavior and default cites a study.
- Look: realistic.
- Owner: the `simultrs` GitHub org (repo `simultrs/antclny`).
- Name: `antclny` (the user's choice, an abbreviation like the `cmprssd` repos, an
  exception to the full-name rule).
- Stack: whichever is fastest overall: the simulation core in Rust compiled to WebAssembly
  (SIMD), rendered with WebGPU and a WebGL2 fallback.
- Hosting: GitHub Pages (`simultrs.github.io/antclny`), deployed from this machine, for
  the static page.
- Shared-colony server: a free-tier VM (e.g. Oracle Cloud Always Free ARM) running the Rust
  core natively, streaming state over WebSocket.
- Individual version: local mode in the browser (WASM, PWA, offline). Built before the
  shared colony.
- License: MIT.

## Open questions *

- [x] What is it for? → Watching, as realistic as possible with what has been studied about ants.
- [x] How realistic? → Biologically detailed.
- [x] How many ants? → Whatever is realistic: the average colony size. If the user doesn't like that number, ~10,000.
- [x] What can the viewer do? → Settings only.
- [x] Which species? → The viewer could choose. If that's too big, red harvester ant only.
- [x] What does the viewer see? → Surface + nest.
- [x] What timeline? → Full colony life.
- [x] How should settings work? → Every parameter exposed.
- [x] When does species picking arrive? → Harvester first; the picker comes later.
- [x] Performance target? → 60 fps and under 50 MB JS heap with 12,000 ants on a mid-range laptop.
- [x] How is realism checked? → Cited sources for every behavior and default.
- [x] What should it look like? → Realistic.
- [x] What's missing today? → Existing web ant sims aren't realistic.
- [x] Stack? → Whichever gives the fastest overall speed.
- [x] Owner? → The new `simultrs` org.
- [x] License? → MIT.
- [x] How is the fastest stack chosen? → Rust→WASM now, without a benchmark.
- [x] Renderer? → WebGPU with a WebGL2 fallback.
- [x] Hosting? → GitHub Pages.
- [x] First session? → Research + benchmark. Also: the project is called `antclny`.
- [x] Phones? → Desktop first.
- [x] Persistence? → One shared colony that everyone sees, lasting as long as it lasts;
  the admin (the user) sets the parameters; an installable individual version gives anyone
  their own colony.
- [x] Analytics? → None.
- [x] Language? → English.
- [x] Where does the shared colony run? → A free-tier VM.
- [x] How do viewers get its state? → The server streams state; browsers only render.
- [x] What is the individual version? → Local mode in the browser, installable as a PWA.
- [x] What comes first? → Local mode, then the shared colony.
- [ ] How does the admin change the shared colony's parameters? Options: (a) a config or CLI
  on the server over SSH, with no web login (recommended: no auth surface); (b) an admin
  page in the site, with login.

## Risks and unknowns

- Detailed biology, a full lifecycle, two views, and maybe several species all pull against
  "fast, little RAM". Per-ant state must stay small (typed arrays) for ~10k ants.
- The shared colony depends on a free-tier VM: the provider can reclaim idle free VMs or
  change its terms, and the VM is a machine to maintain. A paid VPS is the fallback (the
  user's decision at launch).
- Species-picking multiplies the research: each species needs sourced parameters.

## First session

- A cited parameter sheet for *P. barbatus* (behaviors, task allocation, colony growth,
  lifespans, foraging), the source for every default.
- A benchmark: the Rust/WASM core moving 12,000 ants, measured against the success
  criterion (60 fps, under 50 MB JS heap).

## References

- 

## Log

- 2026-11-11: created.
- 2026-11-11: round 1: purpose, realism, scale, interaction.
- 2026-11-11: round 2: species, views, lifecycle, settings.
- 2026-11-11: round 3: species MVP, performance, realism check, look.
- 2026-11-11: round 4: problem, stack, owner (simultrs), license.
- 2026-11-11: round 5: stack (Rust→WASM), renderer, hosting, first session; renamed to antclny.
- 2026-11-11: round 6: desktop first, no analytics, English; scope changed to one shared live colony plus an installable individual version.
- 2026-11-11: round 7: free-tier VM, server streams state, local mode as PWA, local mode first.
