# project-backlog

Projects I haven't started yet, one brief each. A brief is a spec written so that
starting the project later takes one sentence: "start <name> from the backlog".

## How it works

1. **Capture**: `/new-idea` (or `backlog new <name>`) creates `projects/<name>/brief.md`
   from the template. Status `idea`: rough is fine.
2. **Refine**: fill in the brief until `backlog check` accepts it as `ready` (success
   criteria, an MVP, every open question answered).
3. **Start**: `/start-project <name>` creates the repo, copies the brief in as its spec,
   records the decisions, writes the first handoff, and marks the brief `started`.
4. **Archive**: ideas I drop stay here as `archived`, with the reason in their Log.
5. **Triage**: `/triage-backlog` now and then: stale ideas, gaps, overlaps, what to start next.

Statuses: `idea` → `ready` → `started`, or `archived` from any of them.

## Layout

```
projects/<name>/
  brief.md   the spec (frontmatter + sections; see _template/brief.md)
  refs/      material the project needs: links, PDFs, screenshots, sample data
  notes.md   loose thinking, not instructions (optional)
_template/   brief.md (the template) and EXAMPLE.md (a finished brief)
```

`<name>` is the future repo name: lowercase, kebab-case, the full name, no abbreviations.

## Index

Rebuilt by `backlog index`; don't edit by hand.

<!-- backlog:index:start -->
### Idea (1)

| Project | Summary | Tags | Pri | Effort | Updated |
|---|---|---|---|---|---|
| [quantum-zeno-effect](projects/quantum-zeno-effect/brief.md) | A GitHub Pages site where you learn about the quantum Zeno effect. | education, physics, quantum, web |  |  | 2026-10-28 |

### Started (1)

| Project | Repo | Summary | Updated |
|---|---|---|---|
| [higher-dimensions-explorer](projects/higher-dimensions-explorer/brief.md) | [ntfifwyb/higher-dimensions-explorer](https://github.com/ntfifwyb/higher-dimensions-explorer) | A public, browser-based course for properly learning how dimensions work: 4D first, then 5D, 6D and beyond. | 2026-10-27 |
<!-- backlog:index:end -->
