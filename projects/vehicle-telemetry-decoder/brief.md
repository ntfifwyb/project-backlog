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

- [ ] When the check-engine light is on, the app lists each fault code with a
  plain-language explanation within 10 s of connecting.
- [ ] While driving, the app shows RPM, speed, coolant temperature and engine load,
  updating at least once per second.
- [ ] The app can record live data for a drive and show it as charts afterwards.
- [ ] After a repair, the app can clear stored fault codes, after the user confirms.

## Scope *

### Must (MVP)

- Read-only, with one exception: the app reads the car (fault codes, live data) and
  explains it. The only write is the standard OBD-II "clear fault codes" command, run
  only after the user confirms.
- Fault codes listed with plain-language explanations.
- Live gauges: RPM, speed, coolant temperature, engine load.
- Trip recording, shown as charts afterwards.
- Explanations and suggestions come from rules and descriptions built into the app
  (offline, $0).

### Later

- Tuning (writing to the engine computer), under the limits in Constraints.

### Not doing

- Building the adapter: an off-the-shelf one is bought.
- Support for cars other than the user's own.
- A server or cloud sync for trips.

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

- The device that connects to the car is an off-the-shelf OBD-II adapter, bought, not built.
- The interface is on the user's phone, an iPhone. The user would like it to be a web app
  if possible rather than a native one (see Open questions: plain Safari can't reach the
  adapter).
- First version is read-only (except clearing fault codes); tuning comes later.
- The app is a web app opened in an iOS browser with Web Bluetooth (e.g. Bluefy), talking
  to a Bluetooth LE OBD-II adapter. Developed from the user's Windows/WSL PC, no Mac.
- Explanations and suggestions come from built-in rules, not an AI model.
- Hosted on GitHub Pages (free HTTPS, needed for Web Bluetooth), so the repo is public.
- Look: dark dashboard, big high-contrast gauges readable at a glance in the car.
- Metric units (km/h, °C, kPa, litres).
- Recorded trips are stored on the phone (in the browser) and exportable as CSV; no
  server.
- Built for the user's own car only.

## Open questions *

- [ ] Which car (make, model, year, engine, petrol or diesel)? Decides what data and
  tuning are possible. The user will say later.
- [x] Android or iPhone? → iPhone. The user asked whether it could just be a local web
  page in Safari: not by itself, since iOS Safari has no Web Bluetooth and can't open the
  raw TCP socket a Wi-Fi adapter uses.
- [x] Is tuning in the first version, or read-only first? → Read-only first.
- [x] Buy an adapter or build one? → Buy one.
- [x] One car or any car? → The user's car only.
- [x] How does the iPhone reach the adapter? → Web app in a Web Bluetooth browser
  (e.g. Bluefy) with a Bluetooth LE adapter.
- [x] Where do modification suggestions come from? → Built-in rules, offline, $0.
- [x] What must the first version do? → Codes with explanations, live gauges, trip
  recording, clearing codes (see Success criteria).
- [x] Hosting? → GitHub Pages (public repo).
- [x] Look and feel? → Dark dashboard.
- [x] Units? → Metric.
- [x] Where do trips live? → On the phone, CSV export.

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
- 2026-11-11: round 1: iPhone, read-only first, bought adapter, user's car only.
- 2026-11-11: round 2: web app in a Web Bluetooth browser, built-in rules, four MVP features (incl. clearing codes); car still to be named.
- 2026-11-11: round 3: GitHub Pages, dark dashboard, metric, trips on the phone with CSV export.
