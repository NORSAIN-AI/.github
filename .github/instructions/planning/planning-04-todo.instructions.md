.github/instructions/planning/planning-04-todo.instructions.md
---
description: "Todo stage rules (accepted executable work package). This is the gating artifact for implementation."
applyTo: "docs/00-09-admin/03-planning-workspace/todo/**/*.md"
---

# planning workspace — todo

## purpose

The todo stage contains **accepted executable work packages**. A todo is the required gate to begin implementation.

## entry criteria

A work item may enter todo only when:

- scope is bounded (in/out)
- acceptance criteria are complete
- verification steps are defined
- ownership and execution intent are clear
- the todo is explicitly accepted (by the designated human gatekeeper)

## allowed operations

- finalize the executable work package
- adjust wording for clarity and testability
- refine the slice plan and sequencing
- add required references (standards, methods, constraints)
- record acceptance (who accepted, when, and any conditions)

## exit criteria

Move a todo out of todo when:

- execution begins and build evidence must be captured (todo → build)
- the work is canceled or superseded (todo → archive, with reason)

## required artifacts

A todo must include at minimum:

- goal and scope (in and out)
- acceptance criteria (clear and verifiable)
- constraints and assumptions
- impacted areas (paths/domains) and risk notes
- execution plan (slice plan / sequencing)
- verification steps (how to prove done)
- review requirements (who must review and what evidence is required)
- acceptance record (accepted by, accepted on, conditions if any)

## handoff expectations

When moving to build:

- reference the todo from build notes
- follow the slice plan or update the todo and re-accept if changes are material
- maintain evidence links and verification notes as work proceeds

## guardrails

- do not begin implementation without an accepted todo
- do not broaden scope without updating and re-accepting the todo
- do not merge changes that violate acceptance criteria or required checks

---
