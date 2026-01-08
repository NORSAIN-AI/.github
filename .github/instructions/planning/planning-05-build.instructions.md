.github/instructions/planning/planning-05-build.instructions.md
---
description: "Build stage rules for execution notes and evidence capture."
applyTo: "docs/00-09-admin/03-planning-workspace/build/**/*.md"
---

# planning workspace — build

## purpose

Capture execution progress and evidence while implementing an accepted todo, ensuring traceability from todo → changes → verification.

## entry criteria

Work belongs in build when:

- an accepted todo exists
- implementation has begun or is about to begin
- evidence and verification notes must be recorded

## allowed operations

- log execution steps and key choices made during implementation
- record change slices (commits/PRs) mapped to the todo
- record evidence (test outputs, lint outputs, screenshots, links)
- document deviations from plan and rationale
- update verification progress against acceptance criteria

## exit criteria

Move a build item out of build when:

- implementation is complete and ready for review verification (build → reviews)
- the todo is paused/canceled (build → archive, with reason)

## required artifacts

Build notes should include:

- link/reference to the todo
- list of changes produced (commits/PRs, high level)
- evidence list (what was verified and how)
- known issues or follow-ups (if any)
- confirmation that acceptance criteria are met (or gaps listed)

## handoff expectations

When moving to reviews:

- provide a concise change summary
- provide evidence references aligned to acceptance criteria
- highlight any risk areas or notable deviations

## guardrails

- do not change scope silently; update todo if scope changes materially
- do not treat “it works on my machine” as verification; capture evidence
- keep build notes factual and traceable

---
