# copilot instructions — norsain-ai/.github

You are working in NORSAIN’s organization-level `.github` repository. This repo provides shared GitHub standards and automations for many downstream private repositories.

## 1) scope

This repository is limited to:

- reusable workflows and workflow templates under `.github/workflows/`
- PR and issue templates under `.github/`
- contribution and usage documentation (`README.md`, `CONTRIBUTING.md`, `docs/*`)

Do not propose or generate project-specific application code. If a request belongs in a project repo, say so and explain where it should go.

## 2) operating principles

Follow these rules unless the user explicitly overrides them:

- **small and safe by default:** prefer minimal, atomic changes (target ≤ 5 files).
- **least privilege:** minimize GitHub Actions permissions and access. Never broaden permissions without a clear reason. :contentReference[oaicite:1]{index=1}
- **no secrets:** never request, generate, or store secrets/tokens in the repository.
- **backwards compatibility:** reusable workflows are shared contracts. Avoid breaking changes; if unavoidable, include a migration note and versioning plan.
- **determinism over magic:** prefer explicit inputs/outputs, clear defaults, and readable failure modes.

## 3) allowed work (default)

You may propose patches that improve:

- workflow readability, robustness, logging, and input validation
- permissions hardening and secure trigger patterns
- template clarity (PR/issue forms), checklists, and contribution guidance
- documentation sync across README/CONTRIBUTING/docs

## 4) changes requiring explicit approval

Do not propose these without the user explicitly asking for them:

- changing workflow trigger semantics (e.g., switching event types or adding high-risk triggers)
- changing default permissions or adding write scopes (e.g., `contents: write`)
- adding new reusable workflows intended to be adopted broadly
- removing validations (labels/milestones/required metadata) without a documented migration path
- changing behavior relied on by downstream repositories without a compatibility plan

## 5) workflow security baseline

When editing workflows, enforce:

- **permissions:** set minimal `permissions:` at workflow or job level; avoid broad defaults. :contentReference[oaicite:2]{index=2}
- **untrusted code:** avoid patterns where untrusted PR code can execute with elevated privileges or access to secrets.
- **pull_request_target:** do not use `pull_request_target` with write access or secret access unless there is a strong, documented justification and mitigations. :contentReference[oaicite:3]{index=3}
- **action pinning:** prefer pinned action versions and avoid unreviewed third-party actions for privileged jobs.
- **clear failures:** failures must explain what is missing and how to fix it (labels, milestones, required fields).

## 6) output contract for proposals

When suggesting changes, always return:

1. **summary (2–6 sentences):** what + why.
2. **risk notes:** what could break and how to mitigate.
3. **unified diff:** per file, with correct paths.
4. **verification plan:** how a maintainer can validate safely (e.g., test branch / workflow_dispatch / minimal scenario).

Default to producing a diff first. Do not claim to have created branches, commits, or PRs unless the user explicitly requests operational steps.

## 7) refusal criteria

Refuse or redirect when a request:

- introduces secrets, broad permissions, or unclear privilege escalation
- removes controls or validations without migration/justification
- attempts to add application/project CI pipelines that belong in other repositories
- requests large refactors without clear shared benefit to downstream repos

## 8) language and formatting

- write in a concise, professional style
- do not add emojis to templates or documentation
- keep templates consistent and easy to scan
- keep the repository “policy-first”: document intent and constraints, not long operational scripts

---
