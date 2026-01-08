---
description: "Draft a PR title and description using the repo PR template (proposal-first; no PR creation unless explicitly requested)."
name: "pr-draft"
argument-hint: "todo='path/to/todo' base=main head='branch-name'"
agent: "agent"
tools: []
---

## goal

Produce a complete, review-ready PR draft (title + description) aligned to NORSAIN conventions and the repository PR template.

## your task

You must generate a paste-ready PR title and PR body that map to the accepted todo, reflect actual changes, and include risk notes and verification guidance. You must not create a PR unless explicitly asked.

## hard constraints

- proposal-first: do not create a PR unless explicitly asked
- do not modify files unless explicitly asked
- respect the planning gate: no PR draft without an accepted todo
- do not invent repository-specific checks; if unknown, ask
- output must be structured and paste-ready

## inputs (ask only if missing)

- accepted todo path (required to proceed)
- base branch (default: `main`)
- head branch name (required)
- change summary (one of):
  - list of commits (preferred)
  - list of changed files grouped by area
  - short description of what changed
- issue links (optional): `Fixes #` / `Relates to #`

## step 1 — planning gate check

1. confirm an accepted todo exists in:
   - `docs/00-09-admin/03-planning-workspace/todo/`
2. if the todo is missing:
   - stop and output a todo candidate outline (goal, scope in/out, acceptance criteria, verification)
   - do not proceed

## step 2 — propose PR title

Produce exactly one recommended PR title:
- format: `<type>(<scope>): <summary>` (≤ 72 chars)
- type: `feat` | `fix` | `docs` | `chore` | `ci` | `refactor`
- scope: primary area (examples: `ci`, `docs`, `governance`, `agents`, `prompts`)

## step 3 — draft PR description (template-first)

If a PR template exists in the repo, use it and fill it out.

If the template cannot be located or provided, use this minimal structure:

- summary
- scope (in / out)
- changes (bulleted)
- acceptance criteria mapping (met / not met + notes)
- risks and mitigations
- verification plan (reviewer-friendly)
- references (todo, plans/build notes, issues)

## step 4 — reviewer guidance

Provide:
- what areas/files are most important to review
- which risks to focus on
- what evidence to look for

## step 5 — final PR checklist

Provide a compact checklist:
- todo referenced
- scope matches todo
- risks documented
- verification included
- required checks (if known) addressed

## output format (required)

Return the following sections only:

1. planning gate result
2. pr title
3. pr description (paste-ready)
4. reviewer guidance
5. final pr checklist
