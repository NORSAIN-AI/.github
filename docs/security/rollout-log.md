# NORSAIN Security Rollout — Backlog & Status

Single source of truth for the security/test strategy rollout. Cross-references the full plan at `plans/hvordan-kan-vi-bygge-magical-hinton.md` (lives in the operator's local workspace, summarized here).

**Last updated**: 2026-04-22
**Owner**: hs@norsain.com
**Plan version**: v2

## Legend
- [x] done + merged to main
- [~] in progress (PR open)
- [ ] not started
- [!] blocked (external dependency)
- [M] manual action required from operator

---

## Phase 0 — Foundation (NORSAIN-AI/.github)

### Batch 1 — SAST + Secrets (PR #12)
- [x] `.github/workflows/security-sast.yml` — Semgrep (Platform + OSS fallback) + Reviewdog + graceful degradation
- [x] `.github/workflows/security-secrets.yml` — Gitleaks (PR) + TruffleHog (weekly cron)
- [x] `.gitleaks.toml` — NORSAIN baseline (AWS/GCP/GitHub/Slack/OpenAI/Anthropic keys)
- [x] README.md — Security Workflows section
- Status: merged to main
- PR: https://github.com/NORSAIN-AI/.github/pull/12

### Batch 1.5 — Label automation (PR #13)
- [~] `.github/workflows/auto-label-triage.yml` — auto-apply `triage` on PR open
- [~] `require-labels.yml` — prepend `triage` to allowed list
- Status: PR open, self-demonstrating (own PR auto-labeled), all green
- PR: https://github.com/NORSAIN-AI/.github/pull/13

### Batch 2 — Python + IaC (PR #14)
- [~] `.github/workflows/security-python.yml` — uv + Ruff `--select S` + Reviewdog
- [~] `.github/workflows/security-iac.yml` — Checkov + Reviewdog + severity gate
- [~] README.md — add rows for new workflows
- Status: PR open, all checks green
- PR: https://github.com/NORSAIN-AI/.github/pull/14

### Batch 3 — Deps + Self-host CodeQL (not started)
- [ ] `.github/workflows/security-deps.yml` — OSV-Scanner (pnpm-lock + uv.lock)
  - Blocked by [!]: waiting for Renovate baseline to go green on pilot repo first
- [ ] `.github/workflows/codeql-selfhost.yml` — CodeQL on `.github` itself (public, free GHAS)

### Batch 4 — Semgrep rules + templates + docs (not started)
- [ ] `.github/semgrep/norsain-rules.yml` — custom NORSAIN rules (start with stub)
- [ ] `.github/semgrep/.semgrepignore` — shared ignore patterns
- [ ] `workflow-templates/security-full.yml` — bundled caller starter for new repos
  - Note: existing templates (`semgrep-security-scan.yml`, `codeql-security-scan.yml`, `container-security-scan.yml`, `sonarqube-code-analysis.yml`, `org-ci-starter.yml`) need audit for overlap — decide to keep, replace, or delete
- [ ] `docs/security/triage-runbook.md` — how to triage findings
- [ ] `docs/security/exception-policy.md` — 90-day expiring exceptions
- [x] `docs/security/rollout-log.md` — this file

---

## Phase 1 — External prerequisites (operator manual actions)

- [ ] [M] Review + merge PR #13 (auto-triage labels)
- [x] [M] Review + merge PR #12 (SAST + secrets batch) — merged
- [ ] [M] Review + merge PR #14 (Python + IaC batch)
- [ ] [M] Tag `v1` on `NORSAIN-AI/.github` after merges: `gh release create v1 --target main --repo NORSAIN-AI/.github --notes "Initial reusable security workflows"`
- [ ] [M] Install Renovate on `NORSAIN-AI` org: https://github.com/apps/renovate → select all repos
- [ ] [M] Generate `SEMGREP_APP_TOKEN` (CI-type) at https://semgrep.dev/orgs/norsain_com/settings/tokens
- [ ] [M] Store `SEMGREP_APP_TOKEN` as **Organization Secret** on `NORSAIN-AI` (GitHub Settings → Secrets and variables → Actions → New organization secret → all repos)
- [ ] [M] Wait for Renovate to stabilize lockfiles across fleet (green dep-baseline)

---

## Phase 2 — Pilot migration (agentic-orchestrator)

- [ ] [M] Verify pilot repo has needed org-wide secrets accessible
- [ ] Pilot PR: replace existing `security-scan` job in `agentic-orchestrator/.github/workflows/ci.yml` with callers to reusable workflows
- [ ] Verify parity with existing baseline (gitleaks + secretlint + audit-filter → now SAST + secrets reusable workflows)
- [ ] Dummy-PR test: introduce known smell → Semgrep fails PR with inline comment on exact line
- [ ] Dummy-PR test: commit fake AWS key (format `AKIAIOSFODNN7EXAMPLE`) → gitleaks blocks pre-commit + CI
- [ ] Dummy-PR test: change `pnpm-lock.yaml` to version with known HIGH CVE → OSV-Scanner fails
- [ ] Verify: remove `SEMGREP_APP_TOKEN` → graceful fallback to OSS
- [ ] Remove legacy `security-scan` job after caller proven equivalent

---

## Phase 3 — Fleet rollout (6 remaining repos)

Order per plan (IaC repos last due to Checkov readiness):

- [ ] `memory-federator` — caller PR
- [ ] `infra-mcp-gateway` — caller PR
- [ ] `growth` — caller PR
- [ ] `farloft` — caller PR (Terraform-heavy)
- [ ] `infra-platform` — caller PR (Terraform-only)
- [ ] `norsain-docs` — caller PR
- [ ] `norsain-nexus` — caller PR (not backed by GitHub — check if applicable)

---

## Phase 4 — Observations & gaps (flagged during rollout)

- **labels.yml not synced**: labels declared in `NORSAIN-AI/.github/labels.yml` are not auto-synced to repos. Consider `crazy-max/ghaction-github-labeler` workflow. Priority: medium. Owner: TBD.
- **Existing workflow-templates overlap**: `semgrep-security-scan.yml`, `codeql-security-scan.yml`, `container-security-scan.yml`, `sonarqube-code-analysis.yml` pre-existed. Must decide: keep (legacy compat), replace (point to new reusable callers), or delete (avoid confusion). Priority: high before fleet rollout.
- **SCA overlap**: Semgrep Supply Chain (Platform) + OSV-Scanner both do dep scanning. Decide primary after 60 days of parallel data. Priority: low.

---

## Phase 5 — Not in scope (future layers)

- DAST (OWASP ZAP, Nuclei)
- Fuzzing (`@fast-check` TS, AFL++/libFuzzer Python)
- SBOM (Syft) + signing (Cosign) + SLSA provenance
- Container-runtime security (Falco)
- GHAS license (cost-benefit revisit annually)

---

## Changelog

- 2026-04-22: Initial backlog created. Phase 0 batch 1 (PR #12) merged. Batches 1.5 (PR #13) and 2 (PR #14) have PRs open. Phases 1-5 pending.
