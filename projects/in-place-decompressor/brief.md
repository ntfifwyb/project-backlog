---
title: In-place decompressor
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [cli, filesystem, compression]
stack: [rust]
effort:
priority:
---

# In-place decompressor

## Summary *

A tool that extracts a compressed file and deletes the parts of it it has already read as
it goes, so extracting doesn't need disk space for both the archive and its output. In the
user's words: "uncompress files and delete those bits simultaneously, so a compressed file
doesn't require x2 its size in the drive to be able to uncompress."

## Problem *

A normal extraction keeps the whole archive on disk until it finishes. Peak use is the
archive plus everything extracted from it. On a nearly full drive, a large archive can't be
extracted even though the result alone would fit. Today's workaround is to free space
elsewhere or extract to another drive.

## Users and context

- The user, on their own machines.
- The cmprssd game engines (`~/projects/cmprssd`): installing a game from a compressed
  package (for example one copied off the travel disc) onto a nearly full drive, without
  needing room for both the package and the installed game.

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Extract a compressed file while freeing the archive's already-processed bytes, so peak
  disk use stays close to the output size instead of archive + output.
- A Rust library crate that the cmprssd engines depend on, plus a small CLI for any archive.
- Formats: zstd (`.tar.zst`, `.zst`), gzip (`.tar.gz`, `.gz`) and ZIP.
- Windows NTFS first, freeing space with sparse-file hole punching (`FSCTL_SET_ZERO_DATA`).
- Crash-safe from the start: a journal, output flushed before every free, resume after an
  interrupted run, and tests that kill the process at each step.

### Later

- Linux (ext4 and others) after Windows.

### Not doing

- 

## Constraints

- Development costs $0 (workspace rule).

## Decided

- **Build our own engine**, not one based on HatchZip (user's choice, 2026-11-11, made
  knowing HatchZip exists).
- Form: a Rust crate plus a CLI, in its own repo.
- First version: zstd, gzip and ZIP; Windows NTFS first; crash-safe with resume.
- Used by cmprssd to install a game from a compressed package or disc copy.
- Policy check (2026-11-11, Anthropic Usage Policy effective 2026-11-12): **allowed**. It's a
  local file utility. Nothing in the policy covers it, and it doesn't use Anthropic's
  services at runtime.

## Open questions *

- [x] Build on HatchZip or build our own? → Build our own.
- [x] Where in cmprssd? → Installing a game from a compressed package or disc copy, not
  converting the game's own install.
- [x] Form? → A Rust crate plus a CLI (not a module inside cmprssd only).
- [x] First formats? → zstd, gzip and ZIP (not zstd only).
- [x] First platform? → Windows NTFS, then Linux.
- [x] Crash safety in the first version? → Yes: journal, resume, kill tests.

## Risks and unknowns

- Feasibility (explained in the capture session): most filesystems can free the start of a
  file without rewriting it ("hole punching"): `fallocate(FALLOC_FL_PUNCH_HOLE)` on Linux
  ext4/XFS/btrfs, `F_PUNCHHOLE` on macOS APFS, and sparse files with
  `FSCTL_SET_ZERO_DATA` on Windows NTFS. Loop: read a chunk, decompress it, write and
  flush the output, then punch out the chunk that was read.
- **Interrupted runs destroy data.** If the process dies partway, the archive is already
  partly gone. Output has to be flushed to disk before each punch, and the tool probably
  needs a journal so it can resume.
- **Formats.** Stream formats (`.tar.gz`, `.tar.zst`, `.tar.xz`) fit front-to-back
  processing. ZIP keeps its index at the end, so that has to be read into memory first.
  Formats that need random access, or solid archives (7z, RAR), are harder.
- **Filesystems without hole punching** (FAT32, exFAT: most USB drives and SD cards) can
  only shrink a file from the end, which most compressed formats don't allow.
- **Prior art exists** (checked 2026-11-11; see References). HatchZip already does this
  well, so a new engine mostly duplicates it. Its design (journal, flush before freeing,
  crash tests) is a reference, and its MIT/Apache licence allows reading and reusing code.

## First session

- 

## References

- [HatchZip](https://github.com/xevrion/hatchzip): the closest existing tool. Rust,
  licensed MIT or Apache-2.0. A desktop app and a CLI, plus the library crate
  `hatchzip-core` (0.1.10 on crates.io; reads every format but RAR). Created 2026-10-21,
  about 2.8k stars, 11 releases, last push 2026-11-10. Handles ZIP, 7z (solid with limits),
  RAR, tar, `.tar.gz` and multi-block `.tar.xz`. It frees space by cutting the end off the
  archive everywhere, and by hole punching on Linux, Windows and macOS. Its README marks
  NTFS and APFS hole punching as "not yet verified". It keeps a journal and resumes after a
  crash, and its crash tests kill the process at each step. **It refuses `.tar.zst`
  ("planned")** and tar links, devices and sparse files.
- [ReclaimArc](https://github.com/harlixay7/ReclaimArc): Windows NTFS/ReFS only, ZIP and
  RAR. Rust, licensed MIT or Apache-2.0, small (16 commits).
- [Synczipr](https://www.synczipr.com/): a site that claims ZIP extraction with hole
  punching. Its page couldn't be read, so nothing about it is verified.

## Log

- 2026-11-11: created. The user asked whether in-place extraction is possible. Feasibility
  was explained and they asked to build a project on it.
- 2026-11-11: prior art checked: HatchZip (Rust, MIT/Apache) already does this, except
  `.tar.zst`.
- 2026-11-11: decided to build our own; the cmprssd use is installing from a package or disc.
- 2026-11-11: decided form (Rust crate + CLI), formats (zstd, gzip, ZIP), platform
  (Windows NTFS first) and crash safety from the start.
