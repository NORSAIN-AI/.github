AGENTS.md
# agents — norsain-ai/.github

This file provides instructions for coding agents working in NORSAIN’s organization-level `.github` repository. This repository contains shared GitHub standards and automations consumed by downstream private repositories.

## scope

This repository is limited to:

- reusable workflows and templates under `.github/workflows/`
- repository templates and governance UX under `.github/` (PR templates, issue forms, CODEOWNERS, contributing docs)
- documentation that explains how downstream repositories should consume the above

Do not generate application or product code that belongs in downstream repositories.

## working agreement

### baseline behavior

- keep changes small and low-risk by default (prefer a single purpose PR; target ≤ 5 files)
- treat reusable workflows as shared contracts: avoid breaking changes; when unavoidable, include a migration note and versioning guidance
- never introduce or request secrets/tokens in repo content
- prefer explicitness and determinism over “magic” automation

### planning gate (required)

Before implementation work begins, verify there is an **accepted todo** artifact for the change.

- if an accepted todo exists: proceed
- if not: create a planning artifact (inbox/backlog/plans) and propose a todo for human acceptance; do not implement until it is accepted

If the repository does not yet contain the planning workspace structure, propose the minimal structure and stop.

## security baseline for workflows

When changing workflows, enforce:

- **least privilege for `GITHUB_TOKEN`**: set minimal `permissions:` (read by default; elevate per job only when required)
- avoid executing untrusted PR code with elevated permissions or secret access
- **do not use `pull_request_target`** unless explicitly requested and mitigations are documented
- prefer pinned and reputable actions; avoid adding new third-party actions for privileged jobs without justification
- failures must be clear and actionable (what is missing and how to fix it)

## change workflow

### proposal-first

For any non-trivial change, produce a short plan before editing:

- what will change
- why it is needed
- risks and mitigations
- verification approach

### implementation rules

- prefer minimal diffs and stable naming
- keep required checks names stable (avoid breaking enforcement in downstream repos)
- avoid file moves/renames unless there is clear shared benefit and a migration note
- keep documentation in sync with templates/workflows when behavior changes

## verification

At minimum, ensure:

- YAML is valid and workflow syntax is correct
- permissions are minimal and justified
- templates render correctly (PR template + issue forms)
- changes can be validated via a safe PR flow (test branch or limited-scope change)

If the repository defines lint/validation scripts or workflows, run/trigger them and report results.

## output contract

When you respond with a proposed change, include:

1. summary (2–6 sentences): what + why
2. risk notes: what could break and mitigations
3. unified diff (per file)
4. verification plan: how maintainers should validate safely

## precedence and related files

- repository-wide chat guidance: `.github/copilot-instructions.md`
- path-scoped guidance: `.github/instructions/**/*.instructions.md`
- custom agents (VS Code): `.github/agents/*.agent.md`

If instructions conflict, follow the stricter rule and call out the conflict explicitly.
