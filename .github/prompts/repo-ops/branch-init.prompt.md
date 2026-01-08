---
description: "Prepare a new branch using NORSAIN conventions (no implementation, planning-gate enforced)."
name: "branch-init"
argument-hint: "type=feat title='short title' todo='path/to/todo' base=main"
agent: "ask"
---

## goal

Prepare a new feature branch consistently and safely, without implementing changes.

## your task

You must guide the maintainer through a standardized branch initialization routine for NORSAIN repositories. You must enforce the planning gate, propose a compliant branch name, and output an actionable checklist and readiness statement.

## hard constraints

- do not implement changes
- do not modify files
- do not create branches, commits, or PRs automatically
- output must be a short, actionable plan for a human to execute
- respect the planning gate: no implementation work without an accepted todo

## inputs (ask only if missing)

- repository name (or confirm from context)
- the accepted todo path (or confirm none exists)
- short feature title (human-readable)
- type: `feat` | `fix` | `docs` | `chore` | `ci` | `refactor`
- target base branch (default: `main`)

## step 1 — planning gate check

1. confirm whether an accepted todo exists in:
   - `docs/00-09-admin/03-planning-workspace/todo/`
2. if no accepted todo exists:
   - stop and provide a minimal todo candidate outline (goal, scope in/out, acceptance criteria, verification)
   - do not proceed to branch preparation

## step 2 — propose branch name

Produce exactly one recommended branch name:

- format: `<type>/<yyyy-mm-dd>-<kebab-short-title>`
- rules:
  - lowercase
  - kebab-case for title
  - max ~60 characters total
  - avoid internal IDs unless they exist in the accepted todo

Output:
- recommended branch name
- 1–2 alternate names (optional) only if ambiguity exists

## step 3 — pre-flight checklist (human executes)

Provide a minimal checklist for a clean start:

- verify you are on the base branch and it is clean
- fetch and update base branch from origin
- create the new branch from updated base branch
- confirm upstream tracking is set when pushing

Do not include long command blocks. If commands are requested, provide only the minimal set.

## step 4 — branch readiness statement

Produce a short readiness statement that the maintainer can paste into the planning workspace build notes:

- references the accepted todo path
- states the branch name
- states the intended scope and the first slice (high level)

## output format (required)

Return the following sections only:

1. planning gate result
2. branch name
3. pre-flight checklist
4. readiness statement
