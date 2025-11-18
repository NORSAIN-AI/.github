
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

Resultat
