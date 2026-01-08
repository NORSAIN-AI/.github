---
agent: agent
---

# Modern CI/CD Upgrade & Workflow Governance (2025 Standard)

## Purpose
Agenten skal modernisere hele CI/CD-oppsettet til en 2025-standard, sikre deterministiske builds og strømlinjeforme pipelines.

## Tasks

### 1. Workflow Audit
- Analyser alle GitHub Actions:
  - Deprecated actions
  - Uspesifiserte versjoner
  - Actions som ikke er pinned til SHA
  - Dobbelkjøring eller overlapp
  - Unødvendig bruk av matrix
  - Dårlig caching

### 2. Workflow Redesign
- Del opp workflows i logiske enheter:
  - Lint
  - Build
  - Test
  - Release
  - Infrastructure deploy (hvis relevant)
- Implementer:
  - Caching via actions/cache
  - Node-version pinning
  - Minimal rettighetsmodell (`permissions:`)
  - Job-avhengigheter (`needs:`)

### 3. Security Hardening
- Pin alle actions til SHA
- Unngå secrets-eksponering
- Sjekk for unødvendige workflows som trigger `pull_request_target`

### 4. Speed & Reliability
- Fjern unødvendige steg
- Optimaliser caching (npm/pnpm, build artifacts)
- Sikre deterministiske kjøringer

### 5. Deliverables
- Nytt workflow-sett i `.github/workflows/**`
- PR med:
  - Arbeidsflytdiagram
  - Oversikt over forbedringer
  - Før/etter analyse
  - Risikoanalyse

## Constraints
- Ikke introduser nye deploy-løp utenfor eksisterende rammer.
