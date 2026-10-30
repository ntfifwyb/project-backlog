# project-backlog

Briefs for projects that don't exist yet. Nothing here is built or run: this repo is the
input to new projects, not their home. The workspace rules (`~/projects/CLAUDE.md`) apply.

## Rules

- One folder per project: `projects/<name>/`, where `<name>` is the future repo name
  (lowercase, kebab-case, full name). The brief is `projects/<name>/brief.md` and follows
  `_template/brief.md`. Supporting material goes in `projects/<name>/refs/`.
- Use the toolkit skills: **new-idea** to capture or refine a brief, **start-project** to
  start one, **triage-backlog** to review them all. The `backlog` command (`backlog help`)
  does the mechanical parts.
- Write what the user said. Don't invent requirements, success criteria or answers to
  open questions; ask, or leave the question open. Your own suggestions go under Open
  questions as options, never under Decided.
- Keep `updated:` current and add a dated line to the brief's Log on every status change.
- Never delete a brief, with one exception: when a project starts, **start-project** moves
  its brief into the new repo (`docs/BRIEF.md`) and `backlog start` replaces it here with
  `started/<name>.md`, a few lines saying where it went. A dropped idea becomes
  `status: archived` with the reason in its Log.
- After any change, run `backlog index` (rebuilds the README table) and `backlog check`,
  and commit both. `.local-ci` runs the same check.
- No secrets, passwords, personal documents or other people's private data in briefs or
  refs: the repo is read into many sessions. Link to where they live instead.
- Started projects keep only their `started/<name>.md` record here (title, repo, dates,
  one-line summary), as a history of what came out of the backlog. Their own repo is the
  source of truth; don't add more to the record.

## Commits

Commit straight to `main` (`brief: add <name>`, `brief: <name> ready`, `brief: start <name> (moved to <owner>/<name>)`),
with no PR: briefs are notes, not code. Push after each change.
