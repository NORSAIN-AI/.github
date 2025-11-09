# Contributing to NORSAIN-AI

Thank you for your interest in contributing to NORSAIN-AI! This document provides guidelines and best practices for contributing to our projects.

## Table of Contents

- [Code of Conduct](#code-of-conduct)
- [Getting Started](#getting-started)
- [Conventional Commits](#conventional-commits)
- [Pull Request Process](#pull-request-process)
- [Labels and Milestones](#labels-and-milestones)
- [Reusable CI Workflows](#reusable-ci-workflows)

## Code of Conduct

We are committed to providing a welcoming and inclusive environment. Please be respectful and constructive in all interactions.

## Getting Started

1. **Fork the repository** you want to contribute to
2. **Clone your fork** locally
3. **Create a branch** for your changes
4. **Make your changes** following our guidelines
5. **Test your changes** thoroughly
6. **Submit a pull request** to the main repository

## Conventional Commits

We follow the [Conventional Commits](https://www.conventionalcommits.org/) specification for all commit messages and PR titles. This helps us automatically generate changelogs and semantic versions.

### Format

```
<type>[optional scope]: <description>

[optional body]

[optional footer(s)]
```

### Types

- `feat`: A new feature
- `fix`: A bug fix
- `docs`: Documentation only changes
- `refactor`: Code change that neither fixes a bug nor adds a feature
- `chore`: Changes to build process or auxiliary tools
- `test`: Adding missing tests or correcting existing tests
- `perf`: Performance improvements
- `build`: Changes that affect the build system or external dependencies
- `ci`: Changes to CI configuration files and scripts

### Examples

```
feat: add user authentication
fix: resolve memory leak in data processor
docs: update installation instructions
refactor: simplify error handling logic
chore: update dependencies
```

## Pull Request Process

1. **Create a descriptive PR title** following Conventional Commits format
2. **Apply required labels**:
   - One type label: `feature`, `bug`, `documentation`, or `tech-debt`
   - One priority label: `priority: high`, `priority: medium`, or `priority: low`
3. **Assign to a milestone** to track progress
4. **Fill out the PR template** completely
5. **Ensure CI checks pass**:
   - All tests must be green
   - Linting must pass
   - No security vulnerabilities
6. **Request reviews** from appropriate team members (see CODEOWNERS)
7. **Address feedback** promptly and respectfully

### Review Policy

- All PRs require at least one approval from a code owner
- PRs cannot be merged if CI checks are failing
- Breaking changes require additional review and documentation
- Security-related changes require review from the security team

## Labels and Milestones

### Labels

We use a structured labeling system to categorize and prioritize work:

#### Type Labels
- `bug`: Something isn't working
- `feature`: New functionality
- `documentation`: Documentation improvements
- `tech-debt`: Technical debt and refactoring

#### Priority Labels
- `priority: high`: Critical issues requiring immediate attention
- `priority: medium`: Important issues to address soon
- `priority: low`: Nice-to-have improvements

#### Status Labels
- `status: in-progress`: Work is actively being done
- `status: blocked`: Work is blocked by dependencies
- `status: ready-for-review`: Ready for review

#### Special Labels
- `type: breaking`: Breaking changes that require major version bump

### Milestones

Milestones are used to track progress toward specific goals or releases. Always assign your PR to the appropriate milestone to help with planning and tracking.

## Reusable CI Workflows

We provide reusable CI workflows that can be consumed by all NORSAIN-AI repositories. These workflows handle common tasks like linting, testing, and security scanning.

### Using the Reusable CI Workflow

To use our reusable CI workflow in your repository, create a workflow file (e.g., `.github/workflows/ci.yml`) with the following content:

```yaml
name: CI
on: [push, pull_request]

jobs:
  ci:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
```

The reusable workflow will automatically:
- Detect Node.js projects (via `package.json`) and run linting/tests with pnpm
- Detect Python projects (via `pyproject.toml`) and run linting/tests
- Use appropriate caching for faster builds

### Available Reusable Workflows

- **ci-reusable.yml**: Comprehensive CI workflow for linting and testing
- Additional workflows may be added in the future

## Questions?

If you have questions or need help, please:
- Open an issue for discussion
- Contact the platform team
- Check existing documentation and issues

Thank you for contributing to NORSAIN-AI! 🎉
