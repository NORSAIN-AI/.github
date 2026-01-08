---
description: "Standardize post-merge hygiene: sync main, clean working tree, and close the loop (proposal-first)."
name: "post-merge-cleanup"
argument-hint: "base=main merged_pr='#123' delete_branch=true"
agent: "agent"
tools: []
---

## goal

Return the repository to a clean, synchronized baseline after a PR has been merged, so the maintainer can start the next work item safely.

## your task

You must guide the maintainer through a standardized post-merge routine for NORSAIN repositories. You must ensure local and remote `main` are aligned, the working tree is clean, and the planning workspace is updated for traceability. You must not execute actions automatically unless explicitly requested.

## hard constraints

- proposal-first: do not run commands or modify files unless explicitly asked
- do not rewrite history
- do not delete branches without explicit confirmation in the inputs
- do not bypass required checks or governance gates
- output must be short, actionable, and ordered

## inputs (ask only if missing)

- base branch (default: `main`)
- merged PR reference (number or link)
- whether the feature branch should be deleted locally and/or remotely:
  - `delete_local_branch`: true | false
  - `delete_remote_branch`: true | false
- whether there is a planning workspace item to close:
  - accepted todo path and/or review/archive target path (optional but preferred)

## step 1 — confirm merge state

Confirm the PR is merged and identify:
- base branch
- merged branch name (if known)
- merge strategy used (merge/squash/rebase) if provided

If the PR is not merged, stop and recommend switching to `pr-draft` or review steps instead.

## step 2 — sync local base branch

Provide a minimal, safe sequence to ensure local `main` matches `origin/main`:

- switch to base branch
- fetch updates
- fast-forward pull (no merge commits)
- confirm working tree is clean

Do not include long command blocks. If commands are requested, provide only the minimal set.

## step 3 — workspace hygiene checklist

Return a checklist to confirm:

- no uncommitted changes remain
- no stale branches are being worked on
- local branch list is sane (no unexpected divergence)
- the repository is ready for the next branch-init

## step 4 — branch cleanup (conditional)

If deletion is requested (inputs indicate true), provide ordered steps for:

- deleting the local feature branch (only after confirming you are not on it)
- deleting the remote feature branch (only if it exists and deletion is intended)

If deletion is not requested, include a short note describing when to delete and why.

## step 5 — planning workspace closure (conditional)

If an accepted todo / review record is provided, propose the closure update:

- ensure build notes and review record reference the merged PR
- move or mark items as archived per planning-workspace rules
- note any follow-up items that should go to inbox/backlog

If planning artifacts are missing, propose the minimal “close-out note” content without creating files.

## output format (required)

Return the following sections only:

1. merge confirmation
2. sync base branch steps
3. hygiene checklist
4. branch cleanup steps (conditional)
5. planning workspace close-out (conditional)
