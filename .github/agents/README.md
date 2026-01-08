# agents index

This folder contains NORSAIN workspace agents used with VS Code / Copilot workflows. Agents are role-scoped. They must follow the shared contract and use handoffs to keep work traceable and gated.

## shared references

- shared contract: `shared/agent-contract.agent.md`
- shared handoff rules: `shared/handoff-rules.agent.md`

## planning gate (mandatory)

No implementation work begins without an **accepted todo** in:

- `docs/00-09-admin/03-planning-workspace/todo/`

If an accepted todo does not exist, use `docs-planner` to produce a todo candidate for acceptance.

## agents catalog

| agent | purpose | when to use | outputs |
|---|---|---|---|
| `docs-planner.agent.md` | Convert inbox/backlog inputs into plans and todo candidates. | Any time scope/approach/acceptance criteria are unclear, or a todo is missing. | Plan or todo candidate with scope, criteria, verification. |
| `docs-writer.agent.md` | Draft or update documents and governance artifacts from plan/todo. | Writing or updating docs after scope is defined. | Ready-to-commit docs + verification notes. |
| `docs-debugger.agent.md` | Fix doc validation issues (markdown/yaml/links/frontmatter) with minimal edits. | Lint/schema/link failures or consistency issues. | Minimal fix set + rerun guidance. |
| `code-implementer.agent.md` | Implement approved changes (scripts/configs/workflows) from accepted todo only. | Implementation work that is explicitly authorized. | Minimal diffs + verification steps. |
| `code-debugger.agent.md` | Debug failing validation/tests/builds with targeted fixes. | When verification fails during build/CI. | Root cause + minimal fix + verification. |
| `code-reviewer.agent.md` | Review changes for correctness, safety, maintainability (no edits). | Before merge, or when risk is unclear. | Findings (must/should/optional) + risks + verification guidance. |

## handoff map

The standard work flow is:

1. intake and triage
   - `docs-planner` (inbox/backlog → plans)
2. accept and gate
   - `docs-planner` (plans → todo candidate → accepted todo)
3. execute
   - `code-implementer` (todo → build changes)
4. debug if needed
   - `code-debugger` (failures → targeted fixes)
5. review
   - `code-reviewer` (findings, risks, verification)
6. document and sync
   - `docs-writer` (docs updates, review notes)
7. validate docs
   - `docs-debugger` (lint/schema/link fixes)
8. close out
   - update planning artifacts (build/reviews/archive) as required

### common handoff patterns

- planner → writer
  - use when the plan/todo requires new or updated documentation
- planner → implementer
  - use only when an accepted todo exists
- implementer → reviewer
  - use when implementation is ready for merge decision
- implementer → debugger
  - use when CI/local validation fails
- reviewer → writer
  - use to record findings and update docs/templates as required
- any role → planner
  - use when scope changes materially or re-acceptance is required

## selection rules

Use these rules to choose the right agent:

- unclear request, missing scope, or missing todo: start with `docs-planner`
- writing or updating documents from an approved plan/todo: use `docs-writer`
- fixing doc lint/schema/link issues: use `docs-debugger`
- implementing approved changes: use `code-implementer`
- debugging failing checks/tests: use `code-debugger`
- objective review (no edits): use `code-reviewer`

## conventions

- agent files end with `.agent.md`
- shared reference files live in `shared/` and use `infer: false` and `tools: []`
- all agents must link to:
  - `shared/agent-contract.agent.md`
  - `shared/handoff-rules.agent.md`

---
