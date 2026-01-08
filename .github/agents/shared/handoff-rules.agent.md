---
name: "_shared-handoff-rules"
description: "Shared NORSAIN handoff rules (reference). Defines when and how agents hand work to other agents."
argument-hint: "Reference-only. Do not select as an active agent."
target: "vscode"
tools: []
infer: false
---

# shared handoff rules (reference)

This document standardizes how NORSAIN agents hand work between roles. It ensures traceability, prevents scope drift, and enforces the planning gate.

## 1) handoff principles

- handoffs are role transitions, not “task dumping”
- the receiving agent must be able to continue without re-discovery
- if critical information is missing, the sender must either add it or explicitly list it as unknowns

## 2) mandatory handoff package (minimum)

Every handoff must include the following package (copy/paste friendly):

- context:
  - repo name
  - affected paths (top-level)
  - link(s) to relevant artifacts (todo, plan, build notes, review record)
- scope:
  - in scope (1–5 bullets)
  - out of scope (1–5 bullets)
- acceptance:
  - acceptance criteria (or reference to them)
- constraints:
  - security constraints (secrets, permissions, trust posture)
  - compatibility constraints (shared contracts, downstream impact)
- status:
  - what is done
  - what remains
  - blockers / unknowns
- verification:
  - what was verified
  - what still needs verification
  - how to verify safely (steps, not promises)

## 3) standard handoff triggers

### 3.1 planner → writer

Use when:
- a plan/todo exists and document drafting is required

Handoff must include:
- target output paths
- required structure/sections
- any required cross-links or indexes

### 3.2 planner → implementer

Use when:
- an accepted todo exists and implementation is authorized

Handoff must include:
- exact file paths to change/create
- slice plan / sequencing
- verification commands or workflow steps

### 3.3 implementer → debugger

Use when:
- verification fails or an unexpected error occurs

Handoff must include:
- failing output/log snippet
- reproduction steps
- what changed immediately before the failure

### 3.4 implementer → reviewer

Use when:
- implementation is complete and ready for review

Handoff must include:
- diff summary (files changed + purpose)
- risk notes
- verification results and how to re-run

### 3.5 reviewer → writer (document findings)

Use when:
- review produces findings that must be recorded or governance/docs must be updated

Handoff must include:
- categorized findings (must-fix / should-fix / optional)
- where findings should be recorded (path)

### 3.6 any role → planner (re-scope / re-accept)

Use when:
- scope changes materially
- acceptance criteria must change
- missing context prevents safe progress

Handoff must include:
- what changed vs the accepted todo
- why re-acceptance is required
- proposed updated scope and criteria

## 4) stop conditions (do not continue)

An agent must stop and hand off (or request clarification via planning artifacts) when:

- no accepted todo exists for implementation work outside planning folders
- scope expands beyond the accepted todo
- the work requires elevated permissions, risky triggers, or secret handling not explicitly approved
- the change impacts downstream repositories without a compatibility plan

## 5) formatting rules

- keep handoff packages short and structured
- use bullet lists, not prose paragraphs
- prefer file paths and concrete references over general descriptions
- avoid embedding large diffs; reference diffs or provide only the minimal excerpt needed to continue
