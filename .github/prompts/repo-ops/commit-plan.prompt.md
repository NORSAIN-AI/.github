---
description: "Analyze pending changes and propose a structured commit strategy (proposal-first; no commits unless explicitly requested)."
name: "commit-plan"
argument-hint: "todo='path/to/todo' convention=conventional"
agent: "agent"
tools: []
---

## goal

Produce a clear, minimal-risk commit plan for the current working tree changes, aligned to NORSAIN conventions.

## your task

You must analyze the current change set (files/intent) and return an atomic commit strategy with conventional commit messages. You must enforce the planning gate and map each proposed commit to the accepted todo.

## hard constraints

- proposal-first: do not create commits unless explicitly asked
- do not modify files unless explicitly asked
- do not rewrite history unless explicitly asked
- do not bundle unrelated changes
- respect the planning gate: no commit planning without an accepted todo
- output must be structured and actionable

## inputs (ask only if missing)

- accepted todo path (required to proceed)
- change context (one of):
  - changed file list grouped by area (preferred)
  - `git status` summary
  - short description of what changed
- commit convention (default: conventional commits)

## step 1 — planning gate check

1. confirm an accepted todo exists in:
   - `docs/00-09-admin/03-planning-workspace/todo/`
2. if the todo is missing:
   - stop and output a todo candidate outline (goal, scope in/out, acceptance criteria, verification)
   - do not proceed

## step 2 — change classification

Classify changes into minimal categories:
- documentation
- governance/standards
- workflows/ci
- scripts/tooling
- schemas/registers
- refactors (no behavior change)
- behavior changes (must be explicit)

For each category, list:
- affected paths
- risk level: low | medium | high
- downstream impact: none | possible | likely

## step 3 — commit slicing strategy

Propose a commit sequence that is:
- atomic (one purpose per commit)
- ordered (safe sequence)
- reviewable (small diffs)

Rules:
- separate formatting-only commits from functional commits
- isolate permissions/security-relevant workflow changes
- isolate high-risk changes into their own commit
- avoid mixing schema changes with consumers where possible

## step 4 — commit messages

For each commit, provide:
- message: `<type>(<scope>): <summary>` (≤ 72 chars)
- optional body notes only when risk/compatibility warrants it
- todo reference recommendation for body/footer

## step 5 — pre-commit verification plan

Provide a minimal checklist:
- confirm no secrets or accidental files
- confirm boundaries (no unrelated paths)
- confirm verification steps (only what is known to exist; if unknown, ask)

## output format (required)

Return the following sections only:

1. planning gate result
2. change classification
3. commit slicing strategy
4. commit messages
5. pre-commit verification plan
