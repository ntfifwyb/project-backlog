---
title: Universal File Converter
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [converter, ffmpeg, downloader, desktop, web]
stack: []
effort:
priority:
---

# Universal File Converter

## Summary *

A general file converter (an ffmpeg wrapper "or whatever" does the job) that converts files
to other formats, plus tools like YouTube / Instagram Reels / TikTok downloads. It replaces
the free web tools (e.g. a PDF-to-EPUB converter) that work but are full of ads and
annoying UI. It ships as both a website and a desktop app that adds a right-click context
menu on files to convert them, the way 7-Zip does for compression.

## Problem *

Converting a file today means finding a free web converter for that pair of formats, each
one covered in ads and with an annoying UI. Downloading videos from YouTube, Reels or TikTok
means more of the same sites.

## Users and context

- The user, on their own machine (Windows, via right-click on a file) and in a browser.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Convert files between formats (media via ffmpeg; documents such as PDF → EPUB).
- Download videos from YouTube, Instagram Reels, TikTok and similar sites.
- A website.
- A desktop app with a right-click context menu on files to convert them (like 7-Zip).

### Later

- 

### Not doing

- No ads, no cluttered UI.

## Constraints

- Development costs $0 (workspace rule); paid hosting is a launch decision.
- Anthropic policy check (AUP effective 2026-11-12, read 2026-11-11): **allowed with
  limits.** Converting files is fine. The downloader is allowed only as a front end to an
  existing downloader (e.g. yt-dlp) for content the user has the right to save; it must not
  bypass DRM, paywalls, logins or a platform's anti-bot protections, since the AUP forbids
  violating IP rights and "actions or behaviors that circumvent the guardrails or terms of
  other platforms or services". Recheck if scope adds anything of that kind.
- Third-party risk (the user's call): YouTube's and TikTok's terms restrict downloading
  outside their own features, and copyright law applies to what is downloaded. A **public
  website** that downloads for others carries more risk (DMCA notices, platforms blocking
  the server's IPs) than a local desktop tool.

## Decided

- 

## Open questions *

- [ ] Final name? (Suggested: `universal-file-converter`.)

## Risks and unknowns

- Document conversions (PDF → EPUB) aren't ffmpeg's job: another engine is needed
  (e.g. Calibre, Pandoc, LibreOffice), with its own size and licence.
- A website that converts on a server costs money and handles other people's files; one
  that converts in the browser (ffmpeg.wasm) is limited by browser memory.
- Downloader sites change often and break extractors; a maintained dependency is needed.

## First session

- 

## References

- [Anthropic Usage Policy](https://www.anthropic.com/legal/aup): basis of the policy verdict.

## Log

- 2026-11-11: created.
