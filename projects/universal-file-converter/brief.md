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

- The public, for free: anyone who would otherwise use an ad-filled converter site. The
  user is the first user.
- Desktop (Windows first, right-click on a file) and a browser.

## Success criteria *

- [ ] When the user right-clicks a video in Windows Explorer and picks Convert → MP4, the
  converted file appears next to the original, with no window opening.

## Scope *

### Must (MVP)

- Convert video, audio, images and documents (e.g. PDF → EPUB) from day one.
- Download videos from YouTube, Instagram Reels, TikTok and similar sites.
- A desktop app with a right-click context menu on files to convert them (like 7-Zip),
  Windows first.

### Later

- macOS and Linux desktop apps.
- The website: conversions run in the browser (files never leave the device), plus the
  video downloader.

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

- Desktop app first; the website comes after.
- Public and free, not a personal-only tool.
- Website conversions run in the browser, not on a server.
- The website offers the video downloader too, not only the desktop app.
- Right-click converts in two clicks (Convert → format), output next to the original, no
  window.
- The installer bundles the engines (ffmpeg, yt-dlp, a document engine) and keeps yt-dlp
  updated itself.
- Desktop MVP is Windows only.

## Open questions *

- [x] MVP: desktop or website first? → Desktop first (right-click menu); website later.
- [x] Website conversions in the browser or on a server? → In the browser.
- [x] Downloader on the website too? → Yes, website too.
- [x] Public or just for the user? → Public, free.
- [x] Right-click flow? → Two clicks, output next to the original, no window.
- [x] MVP formats? → Media, images and documents.
- [x] Engines bundled or user-installed? → Bundled, yt-dlp self-updating.
- [x] Platforms? → Windows only for now; macOS/Linux later.
- [ ] Final name? (Suggested: `universal-file-converter`.)
- [ ] The web downloader needs a server (browsers can't fetch YouTube/TikTok directly):
  who pays for and runs it, and how are DMCA notices and IP blocks handled?

## Risks and unknowns

- Document conversions (PDF → EPUB) aren't ffmpeg's job: another engine is needed
  (e.g. Calibre, Pandoc, LibreOffice), with its own size and licence.
- A website that converts on a server costs money and handles other people's files; one
  that converts in the browser (ffmpeg.wasm) is limited by browser memory.
- A web downloader is a public server fetching videos for strangers: hosting cost, DMCA
  notices, and platforms blocking its IPs. Desktop downloads avoid all three.
- Downloader sites change often and break extractors; a maintained dependency is needed.

## First session

- 

## References

- [Anthropic Usage Policy](https://www.anthropic.com/legal/aup): basis of the policy verdict.

## Log

- 2026-11-11: created.
- 2026-11-11: round 1 answered (desktop first, browser-side web conversion, web downloader, public).
- 2026-11-11: round 2 answered (two-click right-click, media+images+docs, bundled engines, Windows only).
