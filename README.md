# .github

**Standard policies, templates, and workflows for all NORSAIN-AI repositories**

This repository centralizes organization-wide GitHub configurations, reusable workflows, issue/PR templates, and community health files. It serves as the single source of truth for CI/CD, security policies, and contribution guidelines across all NORSAIN-AI projects.

## 📋 Contents

### Issue & PR Templates

- **Bug Report** (`.github/ISSUE_TEMPLATE/bug_report.yml`) - Structured form for reporting bugs
- **Feature Request** (`.github/ISSUE_TEMPLATE/feature_request.yml`) - Template for suggesting new features
- **Pull Request Template** (`.github/PULL_REQUEST_TEMPLATE.md`) - Standardized PR checklist

### Reusable Workflows

Located in `.github/workflows/`, these workflows can be called from any repository:

#### 🔄 CI/CD Workflows

**`ci-reusable.yml`** - Reusable CI workflow supporting multiple languages

Example usage in your repository:

```yaml
name: CI

on: [push, pull_request]

jobs:
  test:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      language: 'node'
      node-version: '20'
      build-command: 'npm run build'
      test-command: 'npm test'
      lint-command: 'npm run lint'
```

Supported languages: `node`, `python`, `go`, `java`

**`release-please.yml`** - Automated release management

- Automatically creates release PRs based on conventional commits
- Generates changelogs
- Manages semantic versioning
- Tags releases with major/minor versions

#### 🔒 Security Workflows

**`codeql.yml`** - Code security scanning

- Runs CodeQL analysis on push/PR
- Scans for security vulnerabilities
- Supports multiple languages
- Weekly scheduled scans

**`container-scan.yml`** - Container security scanning

- Scans Dockerfiles with Trivy
- Scans container images with Trivy and Grype
- Uploads results to GitHub Security tab
- Runs on Dockerfile changes and weekly schedule

#### ✅ Quality & Automation Workflows

**`semantic-pr.yml`** - Enforce semantic PR titles

- Validates PR titles follow conventional commit format
- Types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`
- Ensures consistency for automated releases

**`require-labels.yml`** - Require labels on issues and PRs

- Ensures all items have at least one label
- Helps with organization and filtering
- Adds helpful comments when labels are missing

**`enforce-milestone.yml`** - Enforce milestone assignment

- Requires milestones on PRs and issues
- Can be bypassed with `no-milestone` label
- Helps with release planning

**`stale.yml`** - Close stale issues and PRs

- Marks inactive items as stale after 60 days
- Closes stale items after 14 additional days
- Respects exempt labels: `pinned`, `security`, `roadmap`
- Respects assigned milestones and assignees

### Configuration Files

- **`labeler.yml`** - Automatic PR labeling based on changed files
- **`labels.yml`** - Organization-wide label taxonomy (standardized labels for all repos)

### Community Health Files

These files are automatically inherited by all repositories in the organization:

- **`CODEOWNERS`** - Define code ownership and required reviewers
- **`CONTRIBUTING.md`** - Contribution guidelines and development workflow
- **`SECURITY.md`** - Security policy and vulnerability reporting process

### Organization Profile

- **`profile/README.md`** - Public organization profile displayed on GitHub

## 🚀 Using Reusable Workflows

### Basic CI/CD Example

```yaml
# .github/workflows/ci.yml in your repository
name: CI

on:
  push:
    branches: [main, develop]
  pull_request:
    branches: [main]

jobs:
  test:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      language: 'python'
      python-version: '3.11'
      test-command: 'pytest'
      lint-command: 'flake8'
```

### Advanced CI Example with Multiple Jobs

```yaml
name: CI

on: [push, pull_request]

jobs:
  # Run tests
  test:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      language: 'node'
      node-version: '20'
      build-command: 'npm run build'
      test-command: 'npm test'
      lint-command: 'npm run lint'
  
  # Security scan
  security:
    uses: NORSAIN-AI/.github/.github/workflows/codeql.yml@main
```

### Language-Specific Examples

#### Node.js / TypeScript

```yaml
jobs:
  ci:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      language: 'node'
      node-version: '20'
      build-command: 'npm run build'
      test-command: 'npm test'
      lint-command: 'npm run lint'
```

#### Python

```yaml
jobs:
  ci:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      language: 'python'
      python-version: '3.11'
      test-command: 'pytest --cov'
      lint-command: 'black . --check && flake8'
```

#### Go

```yaml
jobs:
  ci:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      language: 'go'
      go-version: '1.21'
      build-command: 'go build ./...'
      test-command: 'go test ./... -v'
      lint-command: 'golangci-lint run'
```

#### Java

```yaml
jobs:
  ci:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      language: 'java'
      java-version: '17'
      build-command: 'mvn clean install'
      test-command: 'mvn test'
```

## 📦 Repository Setup

### For New Repositories

1. **Automatic Inheritance**: Issue templates, PR templates, and community health files are automatically inherited by all org repositories

2. **Add Workflows**: Copy relevant workflows from `.github/workflows/` or use reusable workflows

3. **Configure CODEOWNERS**: Create a repository-specific `CODEOWNERS` file if needed

4. **Apply Labels**: Use the label definitions from `labels.yml` for consistency

### Applying Standard Labels

To sync labels across repositories, you can use tools like:

- [github-label-sync](https://github.com/Financial-Times/github-label-sync)
- GitHub CLI with scripts
- GitHub API

Example with `github-label-sync`:

```bash
npm install -g github-label-sync
github-label-sync --labels labels.yml NORSAIN-AI/your-repo
```

## 🔧 Customization

### Overriding Templates

To override organization templates in a specific repository:

1. Create the same file path in your repository (e.g., `.github/ISSUE_TEMPLATE/bug_report.yml`)
2. Your repository's version will take precedence over the organization default

### Customizing Reusable Workflows

You can customize reusable workflows by:

1. Forking and modifying for specific needs
2. Using workflow inputs to configure behavior
3. Extending with additional jobs in your repository

## 📖 Documentation

- [GitHub Community Health Files](https://docs.github.com/en/communities/setting-up-your-project-for-healthy-contributions/creating-a-default-community-health-file)
- [Reusable Workflows](https://docs.github.com/en/actions/using-workflows/reusing-workflows)
- [Issue Templates](https://docs.github.com/en/communities/using-templates-to-encourage-useful-issues-and-pull-requests)
- [Conventional Commits](https://www.conventionalcommits.org/)

## 🤝 Contributing

To propose changes to organization-wide templates and workflows:

1. Fork this repository
2. Create a feature branch
3. Make your changes
4. Open a pull request
5. Request review from `@NORSAIN-AI/core-team`

See [CONTRIBUTING.md](CONTRIBUTING.md) for detailed guidelines.

## 🔒 Security

Report security vulnerabilities following our [Security Policy](SECURITY.md).

## 📄 License

This repository is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

Inspired by best practices from leading open-source organizations and GitHub's recommendations for maintaining healthy, secure, and collaborative projects.

---

**Maintained by NORSAIN-AI** | [Organization Profile](https://github.com/NORSAIN-AI)
