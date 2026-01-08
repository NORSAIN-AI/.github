.github/instructions/planning/planning-03-plans.instructions.md
---
description: "Plans stage rules for structured planning, decisions, and acceptance criteria."
applyTo: "docs/00-09-admin/03-planning-workspace/plans/**/*.md"
---

# planning workspace — plans

## purpose

Convert backlog items into an executable plan with clear scope, decisions, acceptance criteria, and a slicing approach that can produce an accepted todo.

## entry criteria

Work belongs in plans when:

- outcome and priority are known
- planning and decision-making are needed before execution
- the work benefits from decomposition and explicit acceptance criteria

## allowed operations

- define scope precisely (in/out)
- define acceptance criteria that are testable/verifiable
- document assumptions, constraints, and risks
- choose an approach (and record rationale)
- identify required standards and guardrails that apply
- produce a slicing plan (commits/PR strategy at a high level)
- draft the todo artifact content

## exit criteria

Move an item out of plans when:

- scope is clear and bounded
- acceptance criteria are complete
- an execution slice plan exists
- the work package is ready to be accepted as todo

Typical exit:

- plans → todo

## required artifacts

A plan should include:

- goal and scope (in/out)
- acceptance criteria
- constraints and assumptions
- decision points and outcomes (where relevant)
- slice plan (how work will be broken down)
- verification plan (how “done” will be proven)

## handoff expectations

When moving to todo:

- ensure the todo is self-contained and actionable
- include references to relevant standards/instructions
- include explicit verification steps and evidence expectations

## guardrails

- do not start implementation from plans
- avoid scope creep; if scope grows, split the work
- keep decisions explicit; do not rely on implicit consensus

---
