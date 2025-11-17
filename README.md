<<<<<<< HEAD
# NORSAIN-AI .github

[![Org Policy](https://img.shields.io/badge/org--policy-enforced-blue?style=flat-square)](https://github.com/NORSAIN-AI)
[![CI Status](https://github.com/NORSAIN-AI/.github/actions/workflows/ci-reusable.yml/badge.svg)](https://github.com/NORSAIN-AI/.github/actions/workflows/ci-reusable.yml)
[![License](https://img.shields.io/github/license/NORSAIN-AI/.github?style=flat-square)](LICENSE)

> Sentral policy-, mal- og automasjonsrepo for alle NORSAIN-AI-prosjekter.
> Inneholder felles **CI/CD-workflows**, **PR- og issue-maler**, **Copilot-instruksjoner**, og **bidragsstandarder**.

---

## 📚 Innholdsfortegnelse

1. [Formål](#-formål)
2. [Innhold](#-innhold)
3. [Hurtigstart](#-hurtigstart)
4. [Copilot-instruksjoner](#-copilot-instruksjoner)
5. [Gjenbrukbare workflows](#-gjenbrukbare-workflows)
6. [Contributing](#-contributing)
7. [Policy & Governance](#-policy--governance)
8. [Lisens](#-lisens)

---

## 🎯 Formål

Dette repoet fungerer som **organisasjonens felles konfigurasjons- og policy-senter**.
Alle repos under `NORSAIN-AI` kan referere hit for:
- 🧩 gjenbrukbare **GitHub Actions-workflows**
- 🪶 standard **PR- og issue-maler**
- 🤖 **Copilot-styring** (patch/diff-only)
- ⚙️ felles **bidrags- og commit-standarder**

---

## 🧰 Innhold

| Kategori | Fil / Mappe | Beskrivelse |
|-----------|-------------|--------------|
| 🔄 Workflows | `.github/workflows/ci-reusable.yml` | Gjenbrukbar CI-workflow som validerer PR-krav |
|  | `.github/workflows/pr-checks.yml` | Eksempel på bruk av den gjenbrukbare workflowen |
| 🐛 Issues | `.github/ISSUE_TEMPLATE/{bug_report.yml,feature_request.yml}` | Standardiserte maler med auto-labels |
| ⚙️ PR-mal | `PULL_REQUEST_TEMPLATE.md` | Standard PR-mal med tydelig sjekkliste |
| 🤖 AI Policy | `copilot-instructions.md` | Repo-spesifikke Copilot-instruksjoner |
| 👥 Contributing | `CONTRIBUTING.md` | Bidragsguide for hele organisasjonen |
| ⚖️ Lisens | `LICENSE` | Gjeldende lisens for NORSAIN-AI |
| 🧩 Konfigurasjon | `.github/ISSUE_TEMPLATE/config.yml` | Dirigerer brukere til riktige maler |

---

## ⚡ Hurtigstart

Bruk dette repoet som baseline i et prosjekt-repo.

```bash
# Klon ditt prosjekt-repo
git clone git@github.com:NORSAIN-AI/<prosjekt>.git
cd <prosjekt>

# Opprett en workflow som peker til orgens reusable CI
mkdir -p .github/workflows
cat > .github/workflows/ci.yml <<'YML'
name: CI
on:
  pull_request:
  push:
    branches: [main]
jobs:
  validate:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      check-milestone: true
      check-labels: true
YML
git add .github/workflows/ci.yml
git commit -m "chore: enable org-level reusable CI"
git push origin main
```
Resultat:
=======
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
>>>>>>> 4684363f966abdf601e2ec1d930641275f097b94

CI validerer PR-er (milestone + label)

standard PR-mal lastes automatisk

issues bruker felles maler

Copilot følger NORSAIN-policy

---

## 🧠 Copilot-instruksjoner

Dette repoet styrer hvordan Copilot opererer i NORSAIN-miljøet.
Les copilot-instructions.md for full policy.

**Hovedregler**
- Copilot skal aldri opprette commits eller PR-er
- Kun foreslå patch/diff med testforslag
- Maks 10 filer per forslag
- Følg CONTRIBUTING.md og PULL_REQUEST_TEMPLATE.md
- Alt arbeid skal være typesikkert, dokumentert, og testbart

---

## 🔁 Gjenbrukbare Workflows

**ci-reusable.yml**
Validerer PR-er og sikrer god hygiene på tvers av repos.

**Funksjoner**

✅ Sjekker milestone og label

✅ Kan slås av via input (check-milestone: false)

✅ Kjører lint, test, typecheck (kan utvides)

```yaml
jobs:
<<<<<<< HEAD
  validate:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
```

**pr-checks.yml**
Et referanse-eksempel som viser hvordan ci-reusable.yml brukes internt.

---

## 🤝 Contributing

Se CONTRIBUTING.md for detaljer:

- Kodestandarder (Airbnb TS/JS, PEP8, Effective Go)
- Conventional commits
- PR-prosedyre og sjekklister
- Retningslinjer for bug- og feature-forslag

---

## 🔒 Policy & Governance

- Direkte push til main er deaktivert (branch protection anbefales)
- Endringer i .github/** krever review fra @norsain/platform
- Nye workflows, Copilot-instruksjoner eller maler må dokumenteres i PR-beskrivelsen (Hva / Hvorfor / Hvordan)

---

## ⚖️ Lisens

Distribueres under LICENSE.

© NORSAIN-AI — 2025 • Felles DevOps-policy og automasjon 🚀
jobs:

# NORSAIN-AI .github

Dette er organisasjonens sentrale **policy- og automasjonsrepo**.
Her defineres standarder for **CI/CD**, **PR-prosesser**, **issue-maler**, og **AI (Copilot)-instruksjoner** som gjelder for alle NORSAIN-repositorier.

---

## 📦 Formål

- Standardisere **pull request-prosesser**, etiketter og sjekker
- Tilby **gjenbrukbare GitHub Actions-workflows**
- Samle felles **bidrags- og kodestandarder**
- Kontrollere og dokumentere **Copilot-oppførsel** (patch/diff-only)
- Sikre konsistente **issue- og PR-maler** på tvers av alle prosjekter

---

## 🧰 Innhold

| Kategori | Fil / Mappe | Beskrivelse |
|-----------|-------------|--------------|
| 🔄 Workflows | `.github/workflows/ci-reusable.yml` | Gjenbrukbar CI-workflow (kan kalles fra andre repos med `workflow_call`) |
|  | `.github/workflows/pr-checks.yml` | Eksempel som viser bruk av CI-workflow |
| 🐛 Issue Templates | `.github/ISSUE_TEMPLATE/bug_report.yml` | Standardisert feilrapportering med auto-labels |
|  | `.github/ISSUE_TEMPLATE/feature_request.yml` | Feature request-template |
| ⚙️ PR Template | `PULL_REQUEST_TEMPLATE.md` | Standard PR-mal med typevalg, tester og sjekkliste |
| 🤖 Copilot Governance | `copilot-instructions.md` | Repo-spesifikke Copilot-regler og policy (ikke generisk) |
| 👥 Contributing | `CONTRIBUTING.md` | Organisasjonsomfattende bidragsguide |
| ⚖️ Lisens | `LICENSE` | Gjeldende lisens for NORSAIN-prosjekter |
| 🧪 Konfigurasjon | `.github/ISSUE_TEMPLATE/config.yml` | Slår av frie issues og peker brukere mot riktige maler |

---

## 🚀 Bruk i andre repos

For å bruke org-workflows, legg til følgende i prosjektets `.github/workflows`:

```yaml
name: CI
on:
  pull_request:
  push:
    branches: [main]

jobs:
  validate:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      check-milestone: true
      check-labels: true
```

PR-validering sikrer at:

- PR har minst ett label
- PR har tildelt milestone (kan slås av med check-milestone: false)
- PR bruker standardmal (PULL_REQUEST_TEMPLATE.md)

---

## 🧠 Copilot-instruksjoner

Dette repoet har sin egen Copilot-policy i `copilot-instructions.md`

**Formål:**
Gi Copilot kontekst for hvordan NORSAIN-repoet fungerer — ikke som generell AI-trening, men som et styringsdokument for patch/diff-baserte forslag.

**Hovedregler:**
- Copilot skal aldri committe, pushe eller opprette PR-er
- Foreslår kun patch/diff med forklaring og testforslag
- Maks 10 endrede filer per forslag
- Skal følge CONTRIBUTING.md og PR-malen
- Kodeforslag må være typesikre, lesbare, og testbare

---

## 🧩 Reusable Workflow: ci-reusable.yml

Denne workflowen brukes i alle NORSAIN-prosjekter for å sikre standard PR-policy.

**Funksjoner**
- ✅ Sjekker at PR har milestone
- ✅ Sjekker at PR har minst ett label
- ⚙️ Kan konfigureres via input-verdier

**Eksempel:**

```yaml
jobs:
  validate:
    uses: NORSAIN-AI/.github/.github/workflows/ci-reusable.yml@main
    with:
      check-milestone: false
      check-labels: true
```

---

## 💬 Contributing

Se `CONTRIBUTING.md` for:

- Kodestandarder (Airbnb JS/TS, PEP8, Effective Go)
- Commit-format (Conventional Commits)
- PR-prosess og sjekklister
- Retningslinjer for bug reports og feature requests

---

## 🔒 Policy & Governance

- Alle workflows, PR-maler og Copilot-regler må godkjennes via PR med review fra @norsain/platform
- Direkte push til main er deaktivert (branch protection anbefales)
- Nye workflows og AI-prompter må dokumenteres i PR-beskrivelse med Hva / Hvorfor

---

## 🧾 Lisens

Se `LICENSE` for gjeldende lisensvilkår.

© NORSAIN-AI — 2025
Felles retningslinjer og automasjon for enhetlige DevOps-prosesser 🚀
=======
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
>>>>>>> 4684363f966abdf601e2ec1d930641275f097b94
