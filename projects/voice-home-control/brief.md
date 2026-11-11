---
title: Voice Home Control
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [smart-home, voice]
stack: []
effort:
priority:
---

# Voice Home Control

## Summary *

A home control assistant with voice control, for the user's own home. First targets: their
Xiaomi light bulb and Xiaomi fan.

## Problem *

The user wants to control their Xiaomi bulb and fan by voice. (How they control them today,
e.g. the Mi Home app, isn't recorded yet.)

## Users and context

- The user, at home, controlling their own devices.

## Success criteria *

- [ ] (not chosen yet)

## Scope *

### Must (MVP)

- Voice control of the user's Xiaomi light bulb.
- Voice control of the user's Xiaomi fan.

### Later

- 

### Not doing

- 

## Constraints

- Development costs $0 (workspace rule).
- Anthropic policy check (2026-11-11): **allowed**. Controlling the user's own devices by
  voice falls under no prohibited use in the [Usage Policy](https://www.anthropic.com/legal/aup);
  if an agent (Claude) acts on the devices, the policy's agentic guidance applies (human
  oversight, minimal footprint). Recheck if it grows to other people's homes, cameras/audio
  of other people, or locks/security devices.

## Decided

- 

## Open questions *

- [ ] Exact device models (from the box or Mi Home app → device → About)? This decides the
      protocol (see Risks).
- [ ] Protocol: Matter (only if both devices support it) or Xiaomi's own protocol
      (miio/MIoT, via local token or the Xiaomi Home cloud)?

## Risks and unknowns

- **Matter may not fit the devices.** Checked 2026-11-11: Xiaomi's first Matter device is the
  Xiaomi Smart LED Bulb (White and Color), launched in 2025 (Matter 1.2, Wi-Fi). Older Mi
  bulbs and, as far as found, all Xiaomi fans (e.g. Mi Smart Standing Fan 2, `dmaker.fan.p18`)
  are not Matter; they speak Xiaomi's miio/MIoT protocol, which Home Assistant and
  python-miio control locally with a device token. So Matter is the right standard only if
  both exact models support it.
- Local miio control needs a token pulled from the Xiaomi cloud; community reports show
  some fan models appearing "unavailable" in Home Assistant.

## First session

- 

## References

- [Xiaomi Smart LED Bulb (Matter)](https://www.mi.com/global/product/xiaomi-smart-led-bulb/): Xiaomi's Matter-certified bulb.
- [Matter Alpha: Xiaomi devices](https://www.matteralpha.com/xiaomi): Matter-certified Xiaomi products.
- [Home Assistant Xiaomi Miio](https://www.home-assistant.io/integrations/xiaomi_miio/): local control of miio devices, incl. Standing Fan.
- [syssi/xiaomi_fan](https://github.com/syssi/xiaomi_fan): fan component, lists `dmaker.fan.p18`/`p30`.
- [python-miio](https://github.com/syssi/python-miio): Python library for miio/MIoT devices.

## Log

- 2026-11-11: created; Matter checked against Xiaomi devices (see Risks).
