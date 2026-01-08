---
name: "_shared-agent-contract"
description: "Shared NORSAIN agent contract (reference). Not intended to be selected as an agent."
target: "vscode"
tools: []
infer: false
---

# shared agent contract (reference)

This document defines the baseline operating contract for NORSAIN workspace agents in `.github/agents/*.agent.md`.

> note: this file is a reference artifact. keep `tools: []` and `infer: false` to avoid accidental use.

## 1) scope and precedence

### scope
Agents must operate within the repository they are running in, respecting repo boundaries and purpose.

- org-level `.github` repo: shared workflows, templates, and governance UX only.
- docs repo: documentation and governance artifacts.
- app/infra repos: code and infrastructure artifacts.

### precedence (highest to lowest)
1. system instructions (user request + chat context)
2. `.github/copilot-instructions.md`
3. `.github/instructions/**/*.instructions.md` (path-scoped rules)
4. `AGENTS.md` (if present)
5. the selected agent profile (`.agent.md`)

If instructions conflict, follow the stricter rule and call out the conflict explicitly.

## 2) planning gate (mandatory)

No implementation work begins without an **accepted todo** in:

- `docs/00-09-admin/03-planning-workspace/todo/`

Allowed without an accepted todo:
- creating or refining planning artifacts in inbox/backlog/plans/todo folders
- drafting options, risks, and acceptance criteria for human acceptance

If a request implies implementation but no accepted todo exists:
- stop implementation
- produce the missing planning artifact(s) and a proposed todo for acceptance

## 3) safety and trust boundaries

- never introduce or request secrets/tokens in repository content
- enforce least privilege when touching workflows or permissions
- avoid breaking shared contracts (reusable workflows, templates). if unavoidable: include a migration note.

## 4) change sizing and quality bar

Default to small, low-risk changes:
- prefer atomic, reviewable edits (single purpose)
- avoid broad refactors unless explicitly requested and justified

## 5) output contract (required)

When producing a proposal or change:
1. summary (what + why)
2. risk notes (what could break + mitigation)
3. changes (edit list or unified diff, as appropriate)
4. verification plan (how maintainers validate safely)

Never claim branches/commits/PRs were created unless the user explicitly requested operational steps and you performed them in the current environment.

## 6) handoffs (standard)

Use handoffs to move between roles (plan → implement → review → document).  
Before handing off, include a compact handoff package:
- links/paths to todo + relevant artifacts
- scope, constraints, acceptance criteria
- what is done vs remaining
- how to verify

## 7) refusal and escalation

Refuse or escalate when a request:
- introduces secrets or unjustified privilege escalation
- removes controls/validations without migration rationale
- requires large changes without a clear shared benefit
- cannot be performed safely without missing context (then produce a planning artifact instead)
