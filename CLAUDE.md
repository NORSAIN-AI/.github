# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository purpose

`NORSAIN-AI/.github` is the organization-level governance repo, not an application. It ships:

- Reusable GitHub Actions workflows (`.github/workflows/*.yml`) consumed by downstream repos via `workflow_call`, pinned by the `@v1` tag.
- Org-level starter workflows (`workflow-templates/`) that appear in GitHub's "New workflow" picker for every NORSAIN-AI repo.
- Issue/PR templates, CODEOWNERS, labels (`labels.yml`), and Copilot governance (`.github/copilot-instructions.md`).
- LLM prompt/agent/instruction templates (`llm/`) that downstream repos copy into their own `.github/agents/`, `.github/instructions/`, `.github/prompts/`.

Do not add application or product code here — it belongs in downstream repos. See `AGENTS.md` for the full working agreement (planning gate, security baseline, output contract).

## Common commands

This repo has no build or test runner. Quality is enforced by pre-commit and CI.

```bash
# Run all lint hooks locally (yamllint + markdownlint + whitespace/EOF/yaml/json checks)
pre-commit run --all-files

# Run a single hook
pre-commit run yamllint --all-files
pre-commit run markdownlint --all-files

# Lint one file
yamllint -c .yamllint.yaml .github/workflows/ci-reusable.yml
markdownlint -c .markdownlint.json README.md

# Validate a workflow's syntax without running it (requires `act` or GitHub UI)
actionlint .github/workflows/*.yml   # if installed
```

Config files: `.pre-commit-config.yaml`, `.yamllint.yaml`, `.markdownlint.json`, `.gitleaks.toml`.

## Reusable workflow contract

Files under `.github/workflows/` are shared contracts. Downstream repos reference them by tag:

```yaml
uses: NORSAIN-AI/.github/.github/workflows/security-sast.yml@v1
secrets: inherit
```

Rules when editing these:

- Treat inputs, job names, and required check names as a public API — renaming breaks enforcement in every downstream repo.
- Breaking changes require a migration note and a new major tag; backward compatibility is the default (`CONTRIBUTING.md`).
- `secrets: inherit` is how callers pass org secrets (e.g. `SEMGREP_APP_TOKEN`). Do not hardcode secret names in example snippets that won't resolve.
- `security-sast.yml` has a Platform-connected mode (when `SEMGREP_APP_TOKEN` is present) and a graceful OSS fallback with Reviewdog — preserve both paths.
- `security-secrets.yml` runs Gitleaks per-PR and TruffleHog weekly; the weekly job opens tracked GitHub issues on verified findings.

## Security baseline (non-negotiable)

Enforced by `AGENTS.md` and the org Copilot policy:

- Set minimal `permissions:` on every workflow job; default to read-only, elevate per-job.
- Do not use `pull_request_target` unless explicitly requested, with documented mitigations.
- Pin third-party actions; avoid adding new ones for privileged jobs without justification.
- Never introduce secrets or tokens into repo content.

## Change workflow

- Never push directly to `main`. All changes go through a PR (`CONTRIBUTING.md`).
- Branches use kebab-case `type/description` (e.g. `chore/update-pr-template`, `feat/security-sast`).
- Conventional Commits required. Prefer ≤ 5 files / ≤ 150 lines per PR.
- PRs must have a label and milestone — CI (`require-labels.yml`, `enforce-milestone.yml`, `semantic-pr.yml`) will fail otherwise.
- Before implementation, confirm there is an accepted planning artifact (see `AGENTS.md` "planning gate"). If the planning workspace is missing, propose minimal structure and stop.

## LLM template layout

When editing or adding templates, keep the source-of-truth vs. downstream-copy distinction clear:

- `llm/agents/*.agent.template.md` → downstream copies to `.github/agents/*.agent.md`
- `llm/instructions/*.instructions.template.md` → downstream `.github/instructions/**/*.instructions.md`
- `llm/prompts/*.prompt.template.md` → downstream `.github/prompts/*.prompt.md`
- `llm/copilot/copilot-instructions.template.md` → downstream `.github/copilot-instructions.md`

The org-level `.github/copilot-instructions.md` at the repo root governs this repo itself and is authoritative for policy; repo-specific copies in downstream projects derive from the template but must align with it.

## Precedence

When guidance conflicts: follow the stricter rule and call out the conflict. Order of precedence per `AGENTS.md`:

1. This file (`CLAUDE.md`)
2. `AGENTS.md` (coding-agent working agreement)
3. `.github/copilot-instructions.md` (repo-wide chat guidance)
4. `.github/instructions/**/*.instructions.md` (path-scoped)

## Documentation Handoff

All non-exception documentation goes to `~/code/docs/` via the handoff protocol. See `.claude-mpm/DOC_HANDOFF.md` and the global rule in `~/.claude/CLAUDE.md` -> "Cross-Repo Documentation Handoff Policy".
