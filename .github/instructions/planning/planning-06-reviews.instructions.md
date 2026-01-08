.github/instructions/planning/planning-06-reviews.instructions.md
---
description: "Reviews stage rules for verification records and review outcomes."
applyTo: "docs/00-09-admin/03-planning-workspace/reviews/**/*.md"
---

# planning workspace — reviews

## purpose

Record verification and review outcomes for completed work, ensuring acceptance criteria are met and governance gates are satisfied before closure.

## entry criteria

Work belongs in reviews when:

- implementation is complete or ready for formal verification
- PR(s) exist and are ready for review/merge decisions
- evidence has been captured in build notes

## allowed operations

- perform verification against acceptance criteria
- record reviewer notes and required changes
- confirm required checks and gates are satisfied
- document approval/decision outcomes
- identify any follow-up work (new inbox/backlog items)

## exit criteria

Move a review item out of reviews when:

- the work is approved and merged (reviews → archive)
- the work requires changes (reviews → build, with clear actions)
- the work is rejected/canceled (reviews → archive, with reason)

## required artifacts

A review record should include:

- link/reference to the todo and build notes
- verification result per acceptance criterion
- list of reviewers/approvers and dates
- confirmation of required checks status
- final decision (approved/changes required/rejected) and rationale

## handoff expectations

- if changes are required, create explicit build actions and reference them
- if follow-up work is needed, create new intake items (inbox/backlog)

## guardrails

- do not close without verifying acceptance criteria
- do not merge without required approvals and checks
- record decisions explicitly; avoid implicit closure

---
