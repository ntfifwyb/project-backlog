# project-backlog

Projects I haven't started yet, one brief each. A brief is a spec written so that
starting the project later takes one sentence: "start <name> from the backlog".

## How it works

1. **Capture**: `/new-idea` (or `backlog new <name>`) creates `projects/<name>/brief.md`
   from the template. Status `idea`: rough is fine.
2. **Refine**: fill in the brief until `backlog check` accepts it as `ready` (success
   criteria, an MVP, every open question answered).
3. **Start**: `/start-project <name>` creates the repo, copies the brief in as its spec,
   records the decisions, writes the first handoff, and removes the brief from here.
4. **Archive**: ideas I drop stay here as `archived`, with the reason in their Log.
5. **Triage**: `/triage-backlog` now and then: stale ideas, gaps, overlaps, what to start next.

Statuses: `idea` → `ready`, or `archived` from either. A started project leaves the
backlog; only `started/<name>.md` (a few lines: repo, dates, summary) stays, as history.

## Layout

```
projects/<name>/
  brief.md   the spec (frontmatter + sections; see _template/brief.md)
  refs/      material the project needs: links, PDFs, screenshots, sample data
  notes.md   loose thinking, not instructions (optional)
started/<name>.md   what a started project leaves behind: repo, dates, one-line summary
_template/   brief.md (the template) and EXAMPLE.md (a finished brief)
```

`<name>` is the future repo name: lowercase, kebab-case, the full name, no abbreviations.

## Index

Rebuilt by `backlog index`; don't edit by hand.

<!-- backlog:index:start -->
### Started (3)

| Project | Repo | Summary | Started |
|---|---|---|---|
| [higher-dimensions](started/higher-dimensions.md) | [instructional-pages/higher-dimensions](https://github.com/instructional-pages/higher-dimensions) | A public, browser-based course for properly learning how dimensions work: 4D first, then 5D, 6D and beyond. | 2026-10-27 |
| [nfsh](started/nfsh.md) | [cmprssd/nfsh](https://github.com/cmprssd/nfsh) | nfsh is a heavily optimized version of **Need for Speed: Heat** (Ghost Games / EA, 2019), in the same spirit as `cmprssd/swjkja`: the same game, but a smaller footprint on disk, much faster, and more reliable. | 2026-10-30 |
| [quantum-zeno-effect](started/quantum-zeno-effect.md) | [instructional-pages/quantum-zeno-effect](https://github.com/instructional-pages/quantum-zeno-effect) | A GitHub Pages site where you learn about the quantum Zeno effect. | 2026-10-30 |
<!-- backlog:index:end -->
