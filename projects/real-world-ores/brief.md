---
title: Real World Ores
status: idea
created: 2026-11-19
updated: 2026-11-19
owner: ntfifwyb
repo:
tags: [minecraft, mod, game]
stack: []
effort:
priority:
---

# Real World Ores

## Summary *

A Minecraft mod whose goal is to add every ore from real life: every listed mineral
(the IMA list, roughly 6,000), each generating where it forms in reality, and smelting
into its product when it is smelted in real life.

## Problem *

Vanilla Minecraft has only a handful of ores (coal, iron, copper, gold, redstone, lapis,
diamond, emerald, quartz, ancient debris); real-world ores are far more numerous.

## Users and context

- Minecraft players.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Every listed mineral (IMA list, ~6,000) as an ore block in the game.
- Each ore drops an item when mined.
- Ores that are smelted in real life smelt into their product; others don't smelt.
- World generation follows realistic geology: ores appear where they form in reality
  (veins, host rock, depth, biome), roughly.

### Later

- 

### Not doing

- A tech tree (alloys, tools, armor, machines) in the first release.

## Constraints

- Development costs $0 (workspace rule).
- Anthropic policy verdict (2026-11-19): **allowed, with limits**. Mineral facts are not
  anyone's IP, but the mod must not copy Mojang's textures, code or other assets beyond
  what Mojang's terms allow (AUP: no infringing third-party IP). Mineral data written with
  Claude's help must be checked, since outputs can be wrong.

## Decided

- Name: Real World Ores (`real-world-ores`).
- Platform: Minecraft Java, on whichever edition/version/loader is the most future-proof;
  judge that when the project starts.
- Scope of "every ore": every listed mineral (IMA list).
- Gameplay: block, drop, and smelting only where the mineral is smelted in real life.
- Generation: realistic geology.

## Open questions *

- [x] What counts as "every ore from real life"? → Every listed mineral (IMA list, ~6,000).
- [x] Which Minecraft edition, version and mod loader? → Whichever is the most future-proof
  (options weighed: Java + NeoForge, Java + Fabric).
- [x] What does each ore do in the game? → Block and drop; smelts only if the mineral is
  smelted in real life.
- [x] Where do ores generate? → Realistic geology.

## Risks and unknowns

- Mojang's EULA and usage guidelines govern mods (no Mojang assets redistributed, rules
  on monetization): a third-party rule, for the user to decide on.
- ~6,000 minerals each need a texture, data and a generation rule: hand work is
  impossible at that size, so textures and data must be generated from a mineral database.

## First session

- 

## References

- [Anthropic Usage Policy](https://www.anthropic.com/legal/aup)
- [Minecraft EULA](https://www.minecraft.net/en-us/eula): what mods may distribute.

## Log

- 2026-11-19: created.
- 2026-11-19: round 1: platform, mineral list, gameplay, generation.
