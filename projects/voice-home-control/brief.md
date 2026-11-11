---
title: Voice Home Control
status: ready
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [smart-home, voice]
stack: [rust, miot, vosk, rustpotter]
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

The user wants to control their Xiaomi bulb and fan by voice. Today they use both the
Xiaomi Home app on their phone and Google/Alexa voice control, and depend heavily on the
phone, which they dislike.

## Users and context

- The user, at home, controlling their own devices.
- Devices: Xiaomi Smart LED Bulb (exact variant unknown) and Xiaomi Smart Tower Fan 2
  (a retailer lists it as model BPTS02DMU; Wi-Fi, Xiaomi Home app).
- Runs on the user's PC first (Windows now; the user will switch to Linux later); a
  dedicated device is wanted later.
- Commands spoken in English, Spanish and German (English first).

## Success criteria *

- [ ] When I say the wake word and "lights on", the bulb turns on within 1 s.
- [ ] Idle, the app uses under 100 MB RAM and under 2% CPU (Task Manager).
- [ ] With the internet unplugged, every MVP command still works on the LAN.

## Scope *

### Must (MVP)

- Voice control of the user's Xiaomi light bulb.
- Voice control of the user's Xiaomi fan.
- Runs on the user's PC.
- Fixed command phrases, recognised by speech-to-text running locally (offline).
- Wake word "Jarvis" starts a command (hands-free; the mic listens locally).
- Commands: bulb on/off, brightness, colour/warmth; fan on/off, speed, oscillation.
- English commands.
- No UI, except a small animation that pops up on screen while it's listening: a thin
  waveform bar along the top edge of the primary monitor that moves with the voice, then shows success or failure.
- Starts with Windows (at login) and stays in the background; always listening (no mute), also during calls.
- Devices are named in the config (name, room), so more bulbs and fans can be added later
  without a rewrite; today one of each.
- One command per wake word.
- Levels as numbers plus up/down ("brightness 50", "fan speed 3", "brighter", "fan faster").
- Bulb colour: warm/cool plus about 10 named colours ("red", "blue", "purple"...).
- If a device doesn't answer: retry once, then the bar shows failure.
- Command phrases live in the config file (add synonyms or languages without rebuilding).
- One-time setup command that signs in to the user's Xiaomi account, saves the device
  tokens locally, and is never needed again (then fully offline).

### Later

- Run on a dedicated device too (user said "both", PC first): a Raspberry Pi running the
  whole app standalone (no PC needed).
- Linux (the user's next OS).
- Spanish and German command sets, right after the MVP.

### Not doing

- A mute control (always listening; quit the app to stop).
- Several commands per wake word.
- Non-Xiaomi devices.
- Cloud services or an LLM in the command path.
- A phone app.
- Schedules or automations.

## Constraints

- Development costs $0 (workspace rule).
- Lightweight app: "nothing like the bloatware from Windows" (small footprint, quick to
  start, low background CPU/memory).
- Under 1 second from the end of a spoken command to the device reacting.
- Windows now, Linux later: the code must not lock itself to Windows.
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
- Written in Rust (small single binary, Windows and Linux).
- No UI; only a small listening animation pops up on screen.
- English first; Spanish and German next.
- Speech: Vosk with a fixed grammar of the command phrases.
- Wake word: Rustpotter (open-source, Rust), word "Jarvis".
- Releases: .exe built locally, attached to a tagged GitHub release.
- Repo: public, MIT licence. Device tokens and IPs live in a local config that is never
  committed.

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
- [x] OS? → Windows for now, Linux eventually.
- [x] Command language? → English, Spanish, German.
- [x] Success criteria? → fast command, light idle footprint, works offline (see above).
- [x] Not doing? → other brands, cloud, phone app, schedules/automations.
- [x] All three languages in the MVP? → English first, ES/DE next.
- [x] Implementation language? → Rust.
- [x] UI? → None, but a small animation pops up while it's listening.
- [x] First session? → Fan + bulb via CLI.
- [x] Speech recogniser? → Vosk with a fixed grammar.
- [x] Wake word engine? → Rustpotter.
- [x] Wake word? → "Jarvis".
- [x] Repo? → Public, MIT.
- [x] Command feedback? → Animation only (shows success/failure), no sound.
- [x] Animation look? → Waveform bar at the screen edge.
- [x] Startup? → Starts with Windows.
- [x] Tokens? → Built-in one-time login.
- [x] More devices later? → Named devices in the config from the start.
- [x] Chained commands? → One command per wake word.
- [x] Releases? → .exe built locally, attached to a tagged GitHub release.
- [x] Mute? → No mute.
- [x] How are they controlled today? → Xiaomi Home app and Google/Alexa; heavy phone
      dependence, which the user dislikes.
- [x] Level phrasing? → Numbers plus up/down.
- [x] Colour? → Warm/cool plus ~10 named colours.
- [x] Device not answering? → Retry once, then show failure.
- [x] When do ES/DE come? → Right after the MVP.
- [x] Grammar editable? → Phrases in the config file.
- [x] Proving speed? → By feel; no timing logs.
- [x] Bar position? → Top edge of the primary monitor.
- [x] During calls? → Keep listening.
- [x] Later (doesn't block the MVP): which dedicated device? → Raspberry Pi standalone.
      Considered: Raspberry Pi (runs the same
      Rust binary and Vosk) or ESP32, which the user would prefer if it's small enough. An
      ESP32-S3 can't run Vosk. Options: (a) ESP32-S3 as a mic satellite that detects the wake
      word and streams audio to the PC/Pi; (b) fully on-chip with Espressif ESP-SR, whose
      command models are believed to cover English and Chinese only (no ES/DE); to verify.

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

- Get both devices' MIoT tokens and model IDs (from the user's Xiaomi account), then switch
  the fan and bulb on/off and set levels from a Rust command-line tool on the LAN. No voice
  yet.

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
- 2026-11-11: round 3: Windows then Linux, EN/ES/DE, success criteria, exclusions.
- 2026-11-11: round 4: English first, Rust, listening animation only, CLI first session.
- 2026-11-11: round 5: Vosk grammar, Rustpotter, wake word "Jarvis", public MIT repo.
- 2026-11-11: round 6: animation-only feedback, waveform bar, start with Windows, built-in token login.
- 2026-11-11: round 7: named devices, one command per wake word, GitHub release .exe, no mute.
- 2026-11-11: round 8: today's workaround, numeric levels, named colours, retry once.
- 2026-11-11: round 9: ES/DE after the MVP, phrases in config, speed judged by feel; device for later open (Pi vs ESP32).
- 2026-11-11: round 10: Pi standalone later, bar on top edge of primary monitor, keeps listening during calls.
- 2026-11-11: idea → ready
