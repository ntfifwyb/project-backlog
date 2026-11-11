---
title: In-place decompressor
status: idea
created: 2026-11-11
updated: 2026-11-11
owner: ntfifwyb
repo:
tags: [cli, filesystem, compression]
stack: []
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

## Success criteria *

- [ ] 

## Scope *

### Must (MVP)

- Extract a compressed file while freeing the archive's already-processed bytes, so peak
  disk use stays close to the output size instead of archive + output.

### Later

- 

### Not doing

- 

## Constraints

- Development costs $0 (workspace rule).

## Decided

- Policy check (2026-11-11, Anthropic Usage Policy effective 2026-11-12): **allowed**. It's a
  local file utility. Nothing in the policy covers it, and it doesn't use Anthropic's
  services at runtime.

## Open questions *

- [ ] 

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
- **Prior art.** Not checked yet. The project may already exist.

## First session

- 

## References

- 

## Log

- 2026-11-11: created. The user asked whether in-place extraction is possible. Feasibility
  was explained and they asked to build a project on it.
