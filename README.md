# NORSAIN-AI /.github

[![Org Policy](https://img.shields.io/badge/org--policy-enforced-blue?style=flat-square)](https://github.com/NORSAIN-AI) [![CI Status](https://github.com/NORSAIN-AI/.github/actions/workflows/ci-reusable.yml/badge.svg)](https://github.com/NORSAIN-AI/.github/actions/workflows/ci-reusable.yml)

Alle repos under `NORSAIN-AI` bør referere til dette repoet for felles policy, workflows og Copilot-governance.

---

## 1. Formål og omfang

`.github`-repoet har følgende hovedformål:

- Standardisere pull request-prosesser, etiketter og kvalitetskrav.
- Tilby gjenbrukbare GitHub Actions-workflows for NORSAIN-AI-prosjekter.
- Samle og forvalte felles bidrags- og kodestandarder.
- Kontrollere og dokumentere Copilot-oppførsel (patch/diff-only, ingen automatiske commits).
- Forvalte felles maler for:
  - agenter (`*.agent.md`)
  - instructions (`*.instructions.md`)
  - oppgaveprompter (`*.prompt.md`)
  - repo-spesifikke Copilot-instruksjoner.

Repoet skal betraktes som en plattformkomponent: endringer her påvirker flere prosjekter og krever tilsvarende kvalitet og governance.

---

## 2. Struktur og innhold

| Kategori           | Fil / mappe                                       | Beskrivelse                |
|--------------------|---------------------------------------------------|----------------------------|
| Workflows          | `.github/workflows/ci-reusable.yml`              | Gjenbrukbar CI-workflow som kan kalles fra andre repos via `workflow_call`. |
|                    | `.github/workflows/pr-checks.yml`                | Referanse-workflow som demonstrerer bruk av `ci-reusable.yml`. |
|                    | `.github/workflows/security-sast.yml`            | Reusable Semgrep SAST-workflow (Platform-tilkoblet med graceful OSS-fallback og Reviewdog inline PR-kommentarer). |
|                    | `.github/workflows/security-secrets.yml`         | Reusable secrets-scanning workflow (Gitleaks per PR + TruffleHog ukentlig deep sweep med issue-opprettelse). |
| Issue templates    | `.github/ISSUE_TEMPLATE/bug_report.yml`          | Standardmal for feilrapportering med auto-labels. |
|                    | `.github/ISSUE_TEMPLATE/feature_request.yml`     | Mal for feature requests.   |
|                    | `.github/ISSUE_TEMPLATE/config.yml`              | Konfigurasjon som styrer tilgjengelige issue-typer og peker brukere til riktige maler. |
| PR-mal             | `PULL_REQUEST_TEMPLATE.md`                       | Standard PR-mal med typevalg, sjekkliste og krav til dokumentasjon og tester. |
| Copilot-governance | `copilot-instructions.md`                        | Organisasjonsomfattende Copilot-regler og retningslinjer for AI-assistert utvikling. |
| Contributing       | `CONTRIBUTING.md`                                | Bidragsguide for NORSAIN-AI, inkludert kodestandarder og commit-konvensjoner. |
| LLM-templates      | `llm/agents/*.agent.template.md`                 | Maler for repo-spesifikke agenter under `.github/agents/` (ekspertprofiler og roller). |
|                    | `llm/instructions/*.instructions.template.md`    | Maler for globale, områdespesifikke og agent-bundne instrukser under `.github/instructions/`. |
|                    | `llm/prompts/*.prompt.template.md`               | Maler for oppgaveprompter under `.github/prompts/` som knyttes til definerte agenter. |
|                    | `llm/copilot/copilot-instructions.template.md`   | Mal for repo-spesifikke Copilot-instruksjoner (`.github/copilot-instructions.md` i hvert repo). |
|                    | `llm/meta/*.md`                                  | Felles retningslinjer for navnekonvensjoner, bruk og struktur av LLM-relaterte .github-filer. |
| Lisens             | `LICENSE`                                        | Gjeldende lisens for NORSAIN-AI/.github og relaterte artefakter. |

(LLM-mappene kan introduseres og utvides gradvis; README er den autoritative oversikten over hva som til enhver tid er i bruk.)

---

## 3. Bruk i andre repos

Prosjekt-repos under `NORSAIN-AI` skal:

1. Konfigurere sine CI-workflows til å kalle `ci-reusable.yml` via `workflow_call`.
2. Bruke de sentrale PR- og issue-malene ved å følge GitHub sin standardoppsett for `.github/ISSUE_TEMPLATE` og `PULL_REQUEST_TEMPLATE.md`.
3. Følge retningslinjene i `CONTRIBUTING.md` for commit-format, kodekvalitet og PR-prosess.
4. Respektere Copilot-policyen definert i `copilot-instructions.md`.
5. For LLM/agent-oppsett:
   - Basere `.github/agents/*.agent.md` på malene i `llm/agents/`.
   - Basere `.github/instructions/*.instructions.md` på malene i `llm/instructions/`.
   - Basere `.github/prompts/*.prompt.md` på malene i `llm/prompts/`.
   - Opprette repo-spesifikke `copilot-instructions.md` basert på `llm/copilot/copilot-instructions.template.md`.

Detaljer om konkret konfigurering av workflows og LLM-templates ligger i hvert enkelt prosjekt-repo, men alle skal peke tilbake til dette repoet som kilden for policy, maler og gjenbrukbare komponenter.

---

## 3a. Security Workflows

Reusable security workflows in `.github/workflows/` provide a shared baseline
for SAST and secrets scanning across all NORSAIN-AI repos. Callers must use
`secrets: inherit` so org-level secrets (e.g. `SEMGREP_APP_TOKEN`) reach the
reusable workflow context.

- `security-sast.yml` — Semgrep SAST with Platform-connected mode when
  `SEMGREP_APP_TOKEN` is present (org `norsain_com`, native PR comments,
  dashboard), gracefully falling back to OSS `semgrep scan` with Reviewdog
  inline PR comments. Fails on findings at or above `fail-severity`
  (default `ERROR`). Uploads `semgrep.json` as a workflow artifact.
- `security-secrets.yml` — Gitleaks on every PR/push (uses repo-root
  `.gitleaks.toml`, posts PR comment, fails on find) plus a weekly
  TruffleHog deep sweep (Monday 06:00 UTC, `--only-verified`) that opens a
  tracked GitHub issue on verified findings. Also runnable via
  `workflow_dispatch`.

After this repo is tagged `v1`, callers wire in the reusable workflows:

```yaml
name: Security
on:
  pull_request:
  push:
    branches: [main]

jobs:
  sast:
    uses: NORSAIN-AI/.github/.github/workflows/security-sast.yml@v1
    secrets: inherit
  secrets-scan:
    uses: NORSAIN-AI/.github/.github/workflows/security-secrets.yml@v1
    secrets: inherit
```

---

## 4. Copilot- og LLM-policy

Copilot-styringen for NORSAIN-AI er definert i `copilot-instructions.md` og skal anses som autoritativ på organisasjonsnivå.
Repo-spesifikke `copilot-instructions.md` skal baseres på malen i `llm/copilot/` og være i tråd med disse prinsippene.
Overordnede prinsipper:

- Copilot skal ikke opprette commits, pushe branches eller opprette/endre pull requests.
- Copilot skal kun foreslå patch/diff-baserte endringer, med forklaring og forslag til tester.
- Forslag skal begrenses til et kontrollert antall filer per endring.
- Alle forslag skal følge retningslinjene i `CONTRIBUTING.md` og `PULL_REQUEST_TEMPLATE.md`.
- Kodeforslag skal være lesbare, typesikre der relevant og testbare.
- LLM-/agent-arbeidsflyt skal bruke definerte:
  - agenter (`.github/agents/*.agent.md`)
  - instructions (`.github/instructions/*.instructions.md`)
  - prompts (`.github/prompts/*.prompt.md`)
  og ikke introdusere ad-hoc roller eller policyer i enkeltfiler.

Detaljerte krav til omfang, begrensninger og forventet kvalitet beskrives i `copilot-instructions.md` og tilhørende LLM-templates.

---

## 6. Contributing og endringshåndtering

Endringer i `.github`-repoet påvirker alle repos som bruker disse standardene. Følg derfor retningslinjene i `CONTRIBUTING.md`.
Overordnede prinsipper:

- Direkte push til `main` skal ikke benyttes; alle endringer gjøres via pull requests.
- Endringer som berører workflows, Copilot-policy, PR- og issue-maler, LLM-templates eller `CONTRIBUTING.md` skal reviewes av definerte vedlikeholdere for `.github`-repoet.
- Hver pull request skal tydelig beskrive:
  - hva som er endret
  - hvorfor endringen er nødvendig
  - hvordan endringen påvirker andre repos som bruker disse artefaktene

---

## 7. Lisens

Se `LICENSE` for gjeldende lisensvilkår.

© NORSAIN-AI, 2025.  
Felles retningslinjer, LLM-templates og automasjon for konsistente DevOps- og AI-prosesser på tvers av organisasjonen.
