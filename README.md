# .github

Standard policies, templates, and workflows for all NORSAIN-AI repositories — centralizing CI/CD, security, and contribution guidelines.

## 📋 Overview

This repository contains organization-wide configuration files, issue templates, pull request templates, reusable workflows, and documentation that can be used across all NORSAIN-AI repositories.

## 🗂️ Repository Structure

```
.github/
├── .github/
│   ├── ISSUE_TEMPLATE/          # Issue templates for bugs and features
│   │   ├── bug_report.yml
│   │   ├── feature_request.yml
│   │   └── config.yml
│   ├── workflows/               # Reusable GitHub Actions workflows
│   │   ├── ci-reusable.yml
│   │   ├── semantic-pr.yml
│   │   ├── require-labels.yml
│   │   ├── enforce-milestone.yml
│   │   ├── release-please.yml
│   │   ├── stale.yml
│   │   ├── codeql.yml
│   │   └── container-scan.yml
│   ├── PULL_REQUEST_TEMPLATE.md # PR template with checklist
│   ├── CODEOWNERS               # Code ownership definitions
│   └── labeler.yml              # Automated PR labeling config
├── profile/
│   └── README.md                # Organization profile README
├── CONTRIBUTING.md              # Contribution guidelines
├── SECURITY.md                  # Security policy
└── labels.yml                   # Label taxonomy

```

## 🚀 Using Templates in Your Repository

### Issue Templates

Issue templates are automatically available in any NORSAIN-AI repository. Users will see them when creating a new issue.

### Pull Request Template

The pull request template is automatically available when creating a PR in any NORSAIN-AI repository.

### Labels

To sync the standard label taxonomy to your repository, you can use the [GitHub Labeler Action](https://github.com/marketplace/actions/github-labeler) or manually create labels based on `labels.yml`.

## 🔄 Using Reusable Workflows

### CI Reusable Workflow

The `ci-reusable.yml` workflow provides automatic linting and testing for Node.js and Python projects.

**Create a workflow file** in your repository at `.github/workflows/ci.yml`:

```yaml
name: CI
on: [push, pull_request]

jobs:
  ci:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
```

**What it does:**
- Automatically detects Node.js projects (via `package.json`)
- Sets up Node.js 22 with pnpm and caching
- Runs `pnpm install`, `pnpm lint`, and `pnpm test`
- Automatically detects Python projects (via `pyproject.toml`)
- Sets up Python 3.12 with pip caching
- Runs Python linting and tests

### Semantic PR Workflow

Enforces conventional commit format for PR titles.

```yaml
name: PR Checks
on:
  pull_request:
    types: [opened, edited, synchronize, reopened]

jobs:
  semantic-pr:
    uses: NORSAIN-AI/.github/.github/workflows/semantic-pr.yml@main
```

### Require Labels Workflow

Ensures PRs have required labels (type + priority).

```yaml
name: PR Checks
on:
  pull_request:
    types: [opened, labeled, unlabeled, synchronize]

jobs:
  require-labels:
    uses: NORSAIN-AI/.github/.github/workflows/require-labels.yml@main
```

### Enforce Milestone Workflow

Ensures PRs are assigned to a milestone.

```yaml
name: PR Checks
on:
  pull_request:
    types: [opened, edited, synchronize, reopened]

jobs:
  enforce-milestone:
    uses: NORSAIN-AI/.github/.github/workflows/enforce-milestone.yml@main
```

### Release Please Workflow

Automates releases and changelog generation.

```yaml
name: Release
on:
  push:
    branches:
      - main

jobs:
  release-please:
    uses: NORSAIN-AI/.github/.github/workflows/release-please.yml@main
    permissions:
      contents: write
      pull-requests: write
```

### Stale Issues/PRs Workflow

Automatically marks and closes stale issues and PRs.

```yaml
name: Stale
on:
  schedule:
    - cron: '0 0 * * *'
  workflow_dispatch:

jobs:
  stale:
    uses: NORSAIN-AI/.github/.github/workflows/stale.yml@main
    permissions:
      issues: write
      pull-requests: write
```

### CodeQL Analysis Workflow

Performs security code scanning.

```yaml
name: CodeQL
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
  schedule:
    - cron: '0 6 * * 1'

jobs:
  codeql:
    uses: NORSAIN-AI/.github/.github/workflows/codeql.yml@main
    permissions:
      actions: read
      contents: read
      security-events: write
```

### Container Security Scan Workflow

Scans for vulnerabilities using Trivy.

```yaml
name: Security Scan
on:
  push:
    branches: [ main ]
  pull_request:
    branches: [ main ]
  schedule:
    - cron: '0 8 * * 1'

jobs:
  trivy:
    uses: NORSAIN-AI/.github/.github/workflows/container-scan.yml@main
    permissions:
      contents: read
      security-events: write
```

## 🏷️ Label System

Our repositories use a structured labeling system:

### Type Labels
- `bug` - Something isn't working
- `feature` - New feature or request
- `documentation` - Documentation improvements
- `tech-debt` - Technical debt and refactoring

### Priority Labels
- `priority: high` - Critical issues requiring immediate attention
- `priority: medium` - Important issues to address soon
- `priority: low` - Nice-to-have improvements

### Status Labels
- `status: in-progress` - Work is actively being done
- `status: blocked` - Work is blocked by dependencies
- `status: ready-for-review` - Ready for review

### Special Labels
- `type: breaking` - Breaking changes requiring major version bump

## 📝 Contributing

Please read our [CONTRIBUTING.md](CONTRIBUTING.md) for details on:
- Conventional Commits format
- PR review process
- How to use labels and milestones
- Development workflow

## 🔒 Security

Please read our [SECURITY.md](SECURITY.md) for information on:
- How to report security vulnerabilities
- Supported versions
- Security best practices

## 📄 License

This repository is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🤝 Support

If you have questions or need help:
- Open an issue in the relevant repository
- Contact @NORSAIN-AI/platform-team
- Check our documentation

---

**Made with ❤️ by NORSAIN-AI**
