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
