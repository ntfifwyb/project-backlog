---
title: File Converter
status: ready
created: 2026-11-11
updated: 2026-11-11
owner: montinaops
repo:
tags: [converter, ffmpeg, downloader, desktop, web]
stack: [tauri, rust, ffmpeg, yt-dlp]
effort:
priority:
---

# File Converter

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
- [ ] The installed app, without engines, is under 10 MB.

## Scope *

### Must (MVP)

- Convert video, audio, images and documents (e.g. PDF → EPUB) from day one.
- Download videos from YouTube, Instagram Reels, TikTok and similar sites, from a small
  app window: paste a link, pick video or audio-only, saved to Downloads.
- Extra tools: compress a video or image, trim a clip, merge PDFs.
- A desktop app with a right-click context menu on files to convert them (like 7-Zip),
  Windows first.

### Later

- macOS and Linux desktop apps.
- Top-level Windows 11 menu entry (not under "Show more options"), once signed: apply to
  SignPath Foundation (free open-source signing) at launch. It needs builds made on a
  public CI such as GitHub Actions, an exception to the local-CI rule to settle then.
- Other UI languages.
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
- The app ships and installs its engines itself (ffmpeg, yt-dlp, a document engine); the
  user never installs them. The app stays under 10 MB: an engine downloads on first use of
  the tool that needs it, and yt-dlp keeps itself updated.
- The right-click submenu lists every supported target format for that file. The user
  should never open a dedicated UI for a one-time action; bulk jobs (e.g. 100 files) are
  what the app window is for.
- If the output name exists, add "-converted" (video.mp4 → video-converted.mp4). If that
  exists too, overwrite it, but move the old one to the Recycle Bin first so nothing is
  lost.
- Right-clicking several selected files converts all of them, no window.
- Progress and errors show in a very small standalone toast of the app's own, not a
  Windows notification (the user has those muted).
- No monthly fees, for signing or anything else.
- The MVP uses the classic context menu (unsigned, $0); on Windows 11 it sits under "Show
  more options" until the app is signed (see Later).
- UI in English only.
- The website, when built, is hosted on a free static host (GitHub Pages or Cloudflare
  Pages).
- Desktop MVP is Windows only.
- Downloads start from a small app window (paste link, video or audio-only).
- MVP tools beyond conversion: compress, trim, merge PDFs.
- Licence: GPL-3.0, open source (compatible with GPL ffmpeg builds and Calibre).
- Name: `file-converter`, repo `montinaops/file-converter`.
- Distribution: unsigned installer on GitHub Releases plus a winget package ($0; users
  click past SmartScreen at first).
- Look: minimal and monochrome; as small as possible, both file size and screen size.
- The web downloader's server (host, DMCA and IP-block policy) is decided when the
  website launches.
- Stack: Tauri (Rust + web UI), so the UI can be reused for the website.

## Open questions *

- [x] MVP: desktop or website first? → Desktop first (right-click menu); website later.
- [x] Website conversions in the browser or on a server? → In the browser.
- [x] Downloader on the website too? → Yes, website too.
- [x] Public or just for the user? → Public, free.
- [x] Right-click flow? → Two clicks, output next to the original, no window.
- [x] MVP formats? → Media, images and documents.
- [x] Engines bundled or user-installed? → Bundled, yt-dlp self-updating.
- [x] Platforms? → Windows only for now; macOS/Linux later.
- [x] How does a desktop download start? → Small app window: paste a link.
- [x] Extra tools in the MVP? → Compress, trim, merge PDFs.
- [x] Licence? → GPL-3.0.
- [x] Desktop stack? → Tauri (Rust + web UI).
- [x] Name? → `file-converter`, under the `montinaops` org.
- [x] The web downloader needs a server (browsers can't fetch YouTube/TikTok directly):
  how does it run? → Decide when the website launches.
- [x] Code signing? → Unsigned; GitHub Releases + winget.
- [x] Look and feel? → Minimalistic, monochrome, as small as possible (file size and
  screen size).
- [x] Win11 menu? → Top-level Win11 menu.
- [x] Submenu length? → Every supported format; bulk jobs go through the app window.
- [x] Size goal? → App under 10 MB; engines download on first use.
- [x] Name collision? → Add "-converted".
- [x] The top-level Win11 menu needs a signed sparse package, which contradicts "unsigned",
  and the user wants no monthly fees. How? → Classic menu first; free SignPath
  Foundation signing for the top-level menu at launch.
- [x] First session? → Right-click video → MP4.
- [x] Website host? → Free static host.
- [x] Languages? → English only.
- [x] Multi-select? → Converts all selected files.
- [x] Second collision? → Overwrite, but send the old file to the Recycle Bin first.
- [x] Feedback without a window? → A very small standalone toast, not a Windows
  notification.

## Risks and unknowns

- Document conversions (PDF → EPUB) aren't ffmpeg's job: another engine is needed
  (e.g. Calibre, Pandoc, LibreOffice), with its own size and licence.
- A website that converts on a server costs money and handles other people's files; one
  that converts in the browser (ffmpeg.wasm) is limited by browser memory.
- A web downloader is a public server fetching videos for strangers: hosting cost, DMCA
  notices, and platforms blocking its IPs. Desktop downloads avoid all three.
- Downloader sites change often and break extractors; a maintained dependency is needed.

## First session

- A Tauri app that installs a classic context-menu entry and converts one video to MP4
  via ffmpeg, output next to the original, with the small toast: the core flow end to end.

## References

- [Anthropic Usage Policy](https://www.anthropic.com/legal/aup): basis of the policy verdict.

## Log

- 2026-11-11: created.
- 2026-11-11: round 1 answered (desktop first, browser-side web conversion, web downloader, public).
- 2026-11-11: round 2 answered (two-click right-click, media+images+docs, bundled engines, Windows only).
- 2026-11-11: round 3 answered (download window, compress/trim/merge, GPL-3.0, Tauri).
- 2026-11-11: round 4 answered; renamed from universal-file-converter to file-converter, owner montinaops.
- 2026-11-11: round 5 answered (top-level Win11 menu, every format in submenu, <10 MB app, -converted suffix).
- 2026-11-11: round 6 answered (no monthly fees, multi-select, recycle-bin overwrite, own toast).
- 2026-11-11: round 7 answered (classic menu first, first session, static web host, English only).
- 2026-11-11: marked ready.
- 2026-11-11: idea → ready
