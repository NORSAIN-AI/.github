# Contributing to NORSAIN-AI/.github

This document governs contributions to the NORSAIN-AI/.github repository, which serves as the source of truth for organization-wide GitHub policies, workflows, and automation. This is **not** a general product or code repository.

## Scope and Audience

- This repo is for NORSAIN-AI maintainers and trusted contributors only.
- Contributions are limited to policy, workflow, template, and governance improvements.
- External feature requests, UI/UX, translations, and generic code changes are **not** relevant here.

## What Contributions Are Relevant?

- Improvements to reusable workflows (`.github/workflows/*.yml`)
- Enhancements to PR/issue templates and documentation
- Security and permissions hardening
- Copilot/governance policy updates
- Consistency and compliance improvements across org-level automation

## Governance and Risk

- Changes here affect **all NORSAIN-AI repositories**.
- All changes must be reviewed by designated maintainers.
- Breaking changes to workflows must follow semver and be documented in a changelog.
- Backward compatibility is required unless explicitly approved.
- All org-level changes should be tested in a dry-run or test-repo before merging.

## Process

1. **Create a branch** using kebab-case, e.g. `chore/update-pr-template`.
2. **Make focused, minimal changes** (≤ 5 files, ≤ 150 lines preferred).
3. **Follow [Conventional Commits](https://www.conventionalcommits.org/)** for commit messages.
4. **Open a Pull Request** and fill out the PR template.
5. **Assign appropriate labels and milestones** (required by CI).
6. **Request review** from a NORSAIN-AI maintainer.
7. **Document impact**: Clearly state which repos or workflows are affected.
8. **Link to relevant policies** (see below).

## Coding and File Standards

- Only YAML, Markdown, and shell scripting are relevant here.
- Follow existing formatting and linting rules (see `.yamllint.yaml`, `.markdownlint.json`).
- Do **not** add language-specific standards for JS/TS, Python, Go, etc.

## Copilot and AI Governance

- All contributors must read and follow [`copilot-instructions.md`](.github/copilot-instructions.md).
- Copilot/AI changes must be small, auditable, and follow NORSAIN governance.
- Do **not** use Copilot to create commits or PRs unless explicitly requested.

## Security and Permissions

- Never add secrets, tokens, or lower security settings.
- All permission changes must be justified and reviewed.
- Do not remove validation steps (labels, milestones) without migration plan.

## Code of Conduct and Policies

- All contributors must follow the [NORSAIN-AI Code of Conduct](https://github.com/NORSAIN-AI/.github/blob/main/CODE_OF_CONDUCT.md).
- See [`copilot-instructions.md`](.github/copilot-instructions.md) for AI governance.
- For org-wide dev standards, refer to internal documentation if available.

## Internal vs. External Contributions

- This repo is primarily for internal NORSAIN-AI maintainers.
- External contributions are accepted only by prior agreement.

## License

By contributing, you agree your work is licensed under the same license as this repository (see LICENSE).

---

**Summary:**
This is a governance and automation repo. All changes must be minimal, auditable, and reviewed. Focus on workflows, templates, security, and policy—not product code or community features.
