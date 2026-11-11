---
title: Vehicle Telemetry Decoder
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [automotive, obd-ii, mobile]
stack: []
effort:
priority:
---

# Vehicle Telemetry Decoder

## Summary *

A tool the user will actually use on their own car: a device plugged into the car sends
its raw data to an app on the user's phone, which decodes it and shows what's wrong,
suggests modifications, and possibly tunes the car, the way people with modded cars tune
their engine computers. Inspired by NextWork's "Build a Vehicle Telemetry Decoder" exercise
(hex frames decoded through JSON profiles), but with real data from a real car.

## Problem *

The user wants to understand and improve their car but knows little about car electronics.
Today, finding out what's wrong means a mechanic or a generic scanner app; tuning means
someone else's software.

## Users and context

- The user, on their own car, from their phone.
- The device that connects to the car is not built by the user: an off-the-shelf one
  (e.g. bought on Amazon). Building one is an open question.
- The user has very little knowledge of the domain, so the app has to explain what it
  shows.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- 

### Later

- 

### Not doing

- 

## Constraints

- Development costs $0 (workspace rule); the adapter hardware is the user's purchase.
- **Anthropic usage policy (read 2026-11-11, version effective 2026-11-12): allowed with limits.**
  - Reading the car (fault codes, live sensor data) and suggesting changes is allowed: it
    is "monitoring, sensing, or reporting on equipment without controlling it".
  - Tuning (writing to the engine computer) only on a car the user owns, and every write
    must be reviewed and approved by the user before it runs; nothing is written to the car
    automatically. Otherwise the policy's high-risk physical actions rules apply.
  - No tunes or features whose purpose is to defeat emissions controls or bypass the car's
    security on cars the user doesn't own: these fall under the policy's illegal-activity
    and unauthorized-access rules.
- Third-party risks (the user's call, not a policy question): emissions and roadworthiness
  laws where the car is registered, the car's warranty, inspection, insurance, and the risk
  of damaging the engine or making the car unsafe with a bad tune.

## Decided

- The device that connects to the car is bought, not built (unless decided otherwise
  below).
- The interface is on the user's phone.

## Open questions *

- [ ] Which car (make, model, year, engine, petrol or diesel)? Decides what data and
  tuning are possible.
- [ ] Android or iPhone? Decides which adapters work (many cheap ones are classic
  Bluetooth, which iPhones can't use).
- [ ] Is tuning in the first version, or read-only first?
- [ ] Buy an adapter or build one?
- [ ] Where do modification suggestions come from (fixed rules, a knowledge base, an AI
  model)?

## Risks and unknowns

- Manufacturer-specific data and engine tuning are often proprietary or locked; what's
  possible depends heavily on the car.
- A bad write to the engine computer can damage the engine or leave the car undrivable.

## First session

- 

## References

- [NextWork: Build a Vehicle Telemetry Decoder](https://nextwork.ai/projects/17aca6a8-803e-43bb-9e3f-b1ca0b779f29):
  the inspiration. A Python CLI that decodes hex frames with JSON profiles
  (value = raw byte × scale + offset), fictional data only, no hardware.
- [Anthropic Usage Policy](https://www.anthropic.com/legal/aup): basis for the verdict
  under Constraints.

## Log

- 2026-11-11: created from the user's description; usage policy verdict: allowed with limits.
