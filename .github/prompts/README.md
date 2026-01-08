.github/prompts/README.md
# prompts index

This folder contains reusable prompt playbooks for NORSAIN repo operations. Prompts are designed to be run manually by maintainers to standardize workflows across repositories.

Prompts are not policies. They must not override:
- `.github/copilot-instructions.md`
- `.github/instructions/**/*.instructions.md`
- `AGENTS.md` (if present)
- `.github/agents/shared/*` shared contracts

## planning gate alignment

Prompts must respect the planning gate:

- no implementation work begins without an accepted todo in:
  - `docs/00-09-admin/03-planning-workspace/todo/`

If a prompt is invoked without an accepted todo, it must respond by creating or requesting the missing planning artifact instead of proceeding.

## folder structure

- `repo-ops/`
  - branch initialization and naming
  - commit planning and commit message strategy
  - PR drafting using the PR template
  - post-merge cleanup and sync routines
- `docs/`
  - documentation planning and release notes routines
- `ci/`
  - workflow safety checks and reusable workflow change routines

## prompts catalog

| area | prompt | purpose |
|---|---|---|
| repo-ops | `branch-init.prompt.md` | Prepare a new feature branch (naming + readiness), without implementing changes. |
| repo-ops | `commit-plan.prompt.md` | Analyze pending changes and propose a structured commit strategy + commit messages. |
| repo-ops | `pr-draft.prompt.md` | Draft a PR description from the PR template and change analysis; prepare for review. |
| repo-ops | `post-merge-cleanup.prompt.md` | Standardize post-merge hygiene: sync main, remove branches, confirm clean state. |
| docs | `docs-change-plan.prompt.md` | Convert a request into a docs plan and todo candidate (no implementation). |
| docs | `docs-release-notes.prompt.md` | Draft release notes from merged PRs and planning artifacts. |
| ci | `workflow-change-safety-check.prompt.md` | Safety checklist and risk analysis for workflow/reusable workflow changes. |

## usage rules

- prompts should be short and repeatable
- prefer structured outputs (lists, checklists, proposed commands) over prose
- do not include secrets
- do not claim actions were performed; output must be actionable steps for a human to run
