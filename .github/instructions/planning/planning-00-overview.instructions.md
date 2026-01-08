.github/instructions/planning/planning-00-overview.instructions.md
---
description: "Planning workspace overview and gating contract (applies to all planning workspace stages)."
applyTo: "docs/00-09-admin/03-planning-workspace/**/*.md"
---

# planning workspace — overview

## purpose

The planning workspace is NORSAIN’s shared control plane for intake, prioritization, execution gating, evidence capture, and review. It standardizes how work moves from idea to merged change across all repositories.

## gating rule

No implementation work (code, configuration, documentation that changes system behavior, workflows, or governance baselines) shall begin without an **accepted todo** artifact in `docs/00-09-admin/03-planning-workspace/todo/`.

If an accepted todo does not exist, the correct action is to create or improve planning artifacts first (inbox/backlog/plans), then produce an accepted todo.

## lifecycle stages

- inbox: capture raw inputs and requests
- backlog: triage, prioritize, and shape scope
- plans: structure approach, decisions, and acceptance criteria
- todo: accepted executable work package (gating artifact)
- build: execution notes and evidence capture
- reviews: verification and review records
- archive: closed work preserved for traceability

## standard sections per stage

Each stage instruction file defines:

- entry criteria
- allowed operations
- exit criteria
- required artifacts
- handoff expectations
- guardrails

## handoff package (minimum)

When moving work from planning into execution (todo → build), the todo must contain at minimum:

- goal and scope (in and out)
- acceptance criteria (clear and testable)
- constraints and assumptions
- affected areas (paths/domains) and risk notes
- execution plan (slicing approach)
- verification steps (how to prove done)
- review requirements (who, what evidence)

## guardrails

- do not implement while still in inbox/backlog/plans
- do not broaden scope during build without updating todo and re-accepting it
- do not skip reviews for baseline/governance/CI changes
- keep artifacts concise and decision-oriented

---
