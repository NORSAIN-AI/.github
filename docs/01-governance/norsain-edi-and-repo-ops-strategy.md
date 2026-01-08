---
title: norsain edi and repo ops strategy 2026
document_type: strategy
classification: internal
version: 0.1.0-draft
status: draft
owner_role: platform-architecture
applies_to: all-private-repos
platforms: [vscode, github, wsl2]
---

# norsain edi and repo ops strategy 2026

## 1. purpose and outcomes

NORSAIN standardizes editor configuration (EDI), repository operations, and planning workflows to ensure consistent execution across all private repositories—independent of individual developer habits.

Target outcomes:

- consistency: predictable structure, conventions, and developer experience across repos
- repeatability: the same workflows produce the same results (branching, committing, PRs, planning gates)
- reduced friction: fewer “how do we do this here?” questions; faster onboarding
- auditability: traceable ownership, decisions, and change flow (planning → implementation → review → merge)
- safety: controlled execution of tasks, agents, and automation through trust boundaries and governance

## 2. scope and non-goals

In scope (v0.1.0):

- VS Code user baseline (developer machine posture) for Windows 11 + WSL2
- VS Code repo workspace baseline (`.vscode/`) for consistent repo behavior
- GitHub repo hygiene baseline (`.github/` templates, CODEOWNERS, contribution UX)
- GitHub enforcement and quality gates (required reviews, required checks, merge policy)
- planning workspace as shared control plane (inbox → backlog → plans → todo → build → reviews → archive)
- organization `.github` repository as CI platform (workflow templates and reusable workflows)
- minimal Copilot baseline integration (taxonomy and intent of files; no “advanced automation” yet)

Non-goals (explicitly out of scope for v1):

- selecting a single “one true” SQL engine for all repos (repo-specific decision)
- defining full Copilot prompt libraries for branch/commit/PR/post-merge (handled in a later iteration)
- standardizing every lint/build toolchain across all repo types (only baseline patterns and hooks)
- replacing human ownership of merges, approvals, or risk decisions with automation or agents

Assumptions:

- all repos are private
- development is done inside WSL2 for all repos
- standards are introduced incrementally with a pilot-first rollout

## 3. operating model by repo type

NORSAIN uses a baseline + deltas operating model:

- baseline: global standards that apply to all repositories
- deltas: repo-type and repo-specific additions that extend the baseline without contradicting it

Repo-type profiles:

| repo type | primary content | typical tooling | typical deltas |
|---|---|---|---|
| docs | governance + documentation + schemas | markdown, yaml, diagrams, astro/starlight | docs IA rules, schema mappings, publishing pipeline |
| app | application code | node/ts, python, tests, build | language-specific rules, runtime/build tasks |
| infra | infrastructure as code | terraform, policies, CI | stricter gates, drift controls, secrets hygiene |
| monorepo | mixed domains | multi-toolchain | scoped baselines per package/folder |

Baseline must always be present:

- planning workspace method and gates
- `.vscode/` baseline structure and rules
- `.github/` hygiene and enforcement minimums
- documentation integrity rules (naming, placement, metadata expectations)

Deltas must be modular:

- language/tooling instruction packs (python, sqlite, terraform, etc.) only where relevant
- CI jobs per repo type, but always wired to the same governance gates

## 4. configuration hierarchy and ownership

### 4.1 precedence model

Configuration sources are layered:

1. platform defaults (VS Code defaults, GitHub platform behavior)
2. user settings (developer machine baseline)
3. workspace settings (`.vscode/settings.json` in repo)
4. folder settings (multi-root workspaces; folder-level overrides)

Policy:

- workspace settings may override user settings only to enforce repo constraints
- multi-root folder overrides are permitted only with explicit justification (avoid hidden divergence)
- JSON config files must be valid JSON (no comments)

### 4.2 ownership boundaries

| configuration area | owner role | change gate |
|---|---|---|
| global strategy and baselines | platform-architecture | PR + required review |
| repo `.vscode/` baseline | platform-architecture + repo owners | PR + required review |
| repo `.github/` hygiene and templates | platform-architecture + repo owners | PR + required review |
| enforcement / gates | platform-architecture | PR + required review + staged rollout |
| planning workspace method | governance + platform-architecture | PR + required review |
| repo-specific deltas | repo owners | PR + required review |

Rule: baseline artifacts are “shared contracts”. Repo-specific deltas must not weaken baseline constraints.

## 5. security and trust boundaries

### 5.1 workspace trust posture

- unknown workspaces default to restricted posture
- trusted posture is granted only for known repositories and verified working copies
- tasks, debugging, and agent execution are treated as privileged operations

Baseline rules:

- do not run tasks/commands from untrusted workspaces
- do not accept “generated scripts” or “one-liners” without review when in restricted posture
- extensions must be sourced from recommended baseline only (avoid random extension sprawl)

### 5.2 secrets and credentials

- never store secrets in repo settings files, prompts, or instruction files
- prefer environment-based secret injection and secret managers where applicable
- ensure review gates apply to workflow files and any secret-adjacent configuration

### 5.3 agent and automation boundaries

- agents may propose changes, but humans own approvals and merges
- no implementation work without an accepted todo (planning gate)
- do not allow autonomous execution to bypass quality gates

## 6. vs code baseline strategy

### 6.1 user baseline (developer machine)

The user baseline standardizes:

- WSL2-first development posture
- repository trust policy defaults
- enabling instruction file consumption (so repo guidance actually applies)
- consistent formatter/linter posture across file types (without forcing every repo to the same stack)

User baseline is maintained as a normative pack and applied by developers voluntarily but strongly recommended.

### 6.2 workspace baseline (per repo)

Each repo contains a `.vscode/` folder that standardizes:

- recommended extensions (`extensions.json`)
- workspace constraints (`settings.json`)
- optional tasks/launch policy where relevant (keep minimal in docs repos)

Workspace baseline must remain:

- small, deterministic, and repo-appropriate
- focused on editor behavior and guardrails, not operational scripts

### 6.3 multi-root workspaces

Policy:

- use multi-root only when necessary (cross-repo orchestration)
- avoid folder-level overrides unless the repo structure requires it
- document any multi-root conventions in the repo’s documentation

## 7. repository structure baseline

Baseline placement conventions:

- `.vscode/` lives at repo root
- `.github/` lives at repo root
- `docs/` is the primary documentation space for technical + governance content in the repo
- governance content lives under `governance/` when the repo hosts governance as code

README policy:

- root `README.md` explains purpose, how to use, and where governance/docs live
- deeper docs go under `docs/` or `governance/` with index-first navigation

File hygiene baseline:

- `.editorconfig` is required
- `.gitignore` is required and maintained
- no “mystery directories” without an index or purpose statement

## 8. github repo hygiene baseline

Minimum required assets per repo:

- PR template (single or multi-template strategy)
- issue templates (markdown or issue forms) appropriate to repo type
- CODEOWNERS for ownership and review routing
- contribution UX (lightweight, private-friendly)

Baseline UX rules:

- templates must reduce ambiguity (what to include, how to verify, acceptance criteria)
- CODEOWNERS must reflect actual ownership boundaries (not aspirational)

Private-only note:

- organization-wide “default community health files” via an org `.github` repo cannot be relied upon in private-only mode; therefore hygiene must be applied per repo (or via repo templates).

## 9. github enforcement and quality gates

Baseline merge policy for `main` (or equivalent):

- require PRs for merge
- require at least one approval from code owners (or designated reviewers)
- require status checks to pass before merge
- protect workflow files and baseline governance files with stricter review requirements

Rulesets vs branch protection:

- use the strongest available enforcement mechanism supported by your GitHub plan
- document plan constraints explicitly and ensure the policy is implementable for private repos

Required checks policy:

- each repo defines a minimal set of checks by repo type (docs/app/infra)
- check names must remain stable over time (avoid breaking enforcement)
- enforcement is staged: first introduce checks, then mark as required

## 10. planning workspace as the control plane

NORSAIN standardizes a shared planning workspace across repositories:

- inbox: intake and capture (unstructured)
- backlog: triage, prioritization, and scope shaping
- plans: structured plans and decision prep
- todo: accepted, executable work packages (gating artifact)
- build: execution notes and evidence collection
- reviews: review records and verification
- archive: closed work, preserved for traceability

Hard gating rule:

- no implementation work (code, infra, governance changes) without an accepted todo artifact

Planning workspace standardization:

- each stage has a dedicated instruction file that defines entry criteria, allowed ops, and exit criteria
- the instruction pack is identical across repos (global baseline)
- repo owners may add deltas only when they do not weaken gates

## 11. org `.github` repo as the ci platform

The organization `.github` repository is treated as a CI platform and template source:

- workflow templates (starter workflows)
- reusable workflows (centralized CI logic)
- reference patterns for checks naming and gating logic

Constraints:

- it must not be assumed that private repos automatically inherit “community health defaults”
- repo-specific wrappers may be needed to call reusable workflows consistently

Platform principles:

- keep reusable workflows small, versioned, and backward compatible
- prefer stable interfaces (inputs/outputs) over frequent rewrites
- treat CI as a product: documentation, changelog, and migration notes

## 12. copilot baseline integration

Copilot is integrated as part of EDI and repo operations, but only at baseline level in v1.

Baseline taxonomy (intent only):

- repo-wide instructions: global guardrails for the repo
- path-specific instructions: deltas that apply to subsets of files/folders
- prompt files: on-demand playbooks (reserved for later “advanced” iteration)
- agents: role-based work with handoffs (already in use; standardized gradually)

Baseline Copilot rules:

- Copilot does not replace planning gates (todo required)
- Copilot does not bypass review/CI enforcement
- Copilot outputs must be compatible with repo conventions and governance constraints

## 13. rollout plan and adoption path

Rollout strategy:

1. pilot
   - apply planning workspace instruction pack
   - apply VS Code workspace baseline (`.vscode/`)
   - apply GitHub hygiene baseline (`.github/` templates + CODEOWNERS)
2. wave rollout by repo type
   - docs repos first (highest governance leverage)
   - infra repos next (highest risk; benefits from gates)
   - app repos last (largest surface; requires toolchain alignment)
3. CI platform rollout
   - establish `.github` repo as reusable workflow platform
   - migrate repos to call reusable workflows in controlled steps

Adoption guidance:

- do not block active delivery; introduce standards in small PRs
- avoid “big bang” refactors of structure unless needed for compliance
- keep a breakglass path: document how to temporarily bypass enforcement for urgent incidents (with audit trail)

## 14. definition of done and verification

A repo is “2026 baseline compliant” when:

VS Code:

- `.vscode/extensions.json` exists and matches baseline for repo type
- `.vscode/settings.json` exists and applies repo constraints without breaking user baseline

GitHub hygiene:

- PR template present and used
- issue templates/forms present where appropriate
- CODEOWNERS present and correct

GitHub enforcement:

- `main` merges require PR + approval(s)
- required checks are defined, stable, and passing

Planning workspace:

- standard planning workspace path exists
- stage instruction pack exists and is applied
- implementation work references an accepted todo

CI platform:

- repo uses either local workflows or reusable workflows consistently (documented choice)
- workflow changes are protected by review and checks

Verification approach:

- manual checklist for pilot
- automated checks added gradually (lint, schema validation, CI required checks)

## 15. governance, versioning, and change control

Versioning:

- strategy document uses semver-style versioning while in draft; move to stable once adopted
- normative packs are versioned independently (each pack has its own lifecycle)

Change control:

- changes to baselines require PR and required review (CODEOWNERS)
- changes that alter enforcement must include a rollout plan and migration notes
- deprecations require a transition period and clear replacement guidance

Review cadence:

- annual review of the strategy
- quarterly review of enforcement/gates and CI platform stability
- continuous improvement via backlog items in the planning workspace

---

# normative pack sequence

## priority order (recommended)

1. planning-workspace-instructions-pack
   - Per-stage instruction files for inbox/backlog/plans/todo/build/reviews/archive; used in all repos.
   - Output: global instruction pack + stage definitions + migration checklist.

2. vscode-user-settings-baseline-2026
   - Machine-level baseline for WSL2-first development, trust posture, and enabling instruction-file consumption.
   - Output: normative user settings policy + rollout guidance.

3. vscode-workspace-baseline-standard
   - Repo-level `.vscode/` baseline: settings + extensions + policy for tasks/launch.
   - Output: `.vscode/` file set per repo type (docs/app/infra) + delta rules.

4. github-repo-hygiene-baseline-standard
   - `.github/` templates/forms, PR template, CODEOWNERS policy, and README placement rules.
   - Output: minimal hygiene pack + templates per repo type.

5. github-enforcement-and-quality-gates-standard
   - Branch protection/rulesets policy and required status checks standards (including troubleshooting and maintainability).
   - Output: enforcement profiles per repo type + staged enablement plan.

6. org-github-ci-platform-standard
   - Målstruktur + gap-sjekkliste + oppgraderingsrekkefølge for `NORSAIN-AI/.github` (workflow templates + reusable workflows + access model).
   - Output: CI platform blueprint + reusable workflow catalog + adoption guide.

7. copilot-baseline-standard
   - Minimal Copilot taxonomy and intent for instructions/prompts/agents (advanced workflows and agent graphs are a later iteration).
   - Output: file taxonomy + baseline constraints + integration points with planning gates.

---
