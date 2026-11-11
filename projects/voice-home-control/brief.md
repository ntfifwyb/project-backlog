---
title: Voice Home Control
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [smart-home, voice]
stack: [miot, offline-stt]
effort:
priority:
---

# Voice Home Control

## Summary *

A home control assistant with voice control, for the user's own home: a standalone app
that listens for fixed spoken commands, recognised offline, and controls their Xiaomi Smart
LED Bulb and Xiaomi Smart Tower Fan 2 over Xiaomi's local MIoT protocol. It runs on their
PC first, starts on a wake word, and must be lightweight and fast: "nothing like the
bloatware from Windows".

## Problem *

The user wants to control their Xiaomi bulb and fan by voice. (How they control them today,
e.g. the Mi Home app, isn't recorded yet.)

## Users and context

- The user, at home, controlling their own devices.
- Devices: Xiaomi Smart LED Bulb (exact variant unknown) and Xiaomi Smart Tower Fan 2
  (a retailer lists it as model BPTS02DMU; Wi-Fi, Xiaomi Home app).
- Runs on the user's PC first; a dedicated device is wanted later.

## Success criteria *

- [ ] (not chosen yet)

## Scope *

### Must (MVP)

- Voice control of the user's Xiaomi light bulb.
- Voice control of the user's Xiaomi fan.
- Runs on the user's PC.
- Fixed command phrases, recognised by speech-to-text running locally (offline).
- Wake word starts a command (hands-free; the mic listens locally).
- Commands: bulb on/off, brightness, colour/warmth; fan on/off, speed, oscillation.

### Later

- Run on a dedicated device too (user said "both", PC first).

### Not doing

- 

## Constraints

- Development costs $0 (workspace rule).
- Lightweight app: "nothing like the bloatware from Windows" (small footprint, quick to
  start, low background CPU/memory).
- Under 1 second from the end of a spoken command to the device reacting.
- Anthropic policy check (2026-11-11): **allowed**. Controlling the user's own devices by
  voice falls under no prohibited use in the [Usage Policy](https://www.anthropic.com/legal/aup);
  if an agent (Claude) acts on the devices, the policy's agentic guidance applies (human
  oversight, minimal footprint). Recheck if it grows to other people's homes, cameras/audio
  of other people, or locks/security devices.

## Decided

- Standalone app, not Home Assistant. "Make it as fast as possible" (latency from speech to
  device is the priority).
- Speech: local, offline speech-to-text with fixed commands (no Claude/LLM in the loop).
- Platform: PC first, a dedicated device later.
- Protocol: MIoT for both devices. The user's rule: Matter only if it adds significant
  functionality; for an on/off/brightness/colour bulb and a fan it doesn't (its gains are
  cross-ecosystem pairing), so MIoT, one local code path.
- Trigger: wake word.
- MVP commands: on/off plus levels (brightness, colour/warmth, fan speed, oscillation).

## Open questions *

- [x] Exact device models? → Xiaomi Smart Tower Fan 2 and Xiaomi Smart LED Bulb; the user
      couldn't find the model numbers.
- [x] Where does it run? → Both PC and a dedicated device; PC first.
- [x] How are commands understood? → Local, fixed commands.
- [x] Home Assistant or standalone? → Standalone, as fast as possible.
- [x] Protocol? → MIoT for both, since Matter adds nothing significant for these devices.
- [x] Which bulb variant? → No longer matters: MIoT covers both the Matter and older bulbs.
      The exact MIoT model IDs get read from the devices in the first session.
- [x] What counts as "fast"? → Under 1 s from speech to device, and above all a lightweight,
      non-bloated app.
- [x] Trigger? → Wake word.
- [x] MVP commands? → On/off plus levels.

## Risks and unknowns

- **Matter doesn't fit the fan.** The Smart Tower Fan 2 lists Alexa and Google Home support,
  not Matter (2026-11-11).
- **Matter on older devices.** Checked 2026-11-11: Xiaomi's first Matter device is the
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
- [Xiaomi Smart Tower Fan 2](https://www.mi.com/global/product/xiaomi-smart-tower-fan-2/): the user's fan.
- [HA forum: Tower Fan `dmaker.fan.p39`](https://community.home-assistant.io/t/add-support-for-xiaomi-tower-fan-dmaker-fan-p39/454061): possible MIoT ID lead (unverified; may be the first-gen Tower Fan).

## Log

- 2026-11-11: created; Matter checked against Xiaomi devices (see Risks).
- 2026-11-11: round 1: devices, PC first, local fixed commands, standalone and fast.
- 2026-11-11: round 2: MIoT for both, lightweight app, under 1 s, wake word, on/off + levels.
