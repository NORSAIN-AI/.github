.github/instructions/planning/planning-07-archive.instructions.md
---
description: "Archive stage rules for closed work and preserved traceability."
applyTo: "docs/00-09-admin/03-planning-workspace/archive/**/*.md"
---

# planning workspace — archive

## purpose

Preserve closed work with traceability, ensuring historical accountability without cluttering active stages.

## entry criteria

Work belongs in archive when:

- it is completed and merged, with reviews recorded
- it is rejected/canceled/superseded, with rationale recorded
- it is a duplicate that has been resolved elsewhere (with pointers)

## allowed operations

- finalize closure notes (outcome, links, key decisions)
- add pointers to PRs, tags, releases, or evidence locations
- mark final status (completed, canceled, rejected, superseded)

## exit criteria

Archive is terminal for the work item.

## required artifacts

An archived item should include:

- final status
- closure summary (what happened)
- references (todo, build, review, PRs)
- date closed and responsible owner/role

## handoff expectations

- follow-ups should be created as new inbox/backlog items, not appended indefinitely to archived records

## guardrails

- do not delete history; archive preserves traceability
- do not keep active work in archive; only closed items belong here
- keep closure notes concise and reference-based

---
