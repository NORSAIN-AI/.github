---
agent: agent
---

# AI Code Generation Safety & Governance (2025 Standard)

## Purpose
Denne prompten etablerer sikkerhets- og governance-kontroller rundt AI-generert kode som blir sjekket inn i repoet.

## Tasks

### 1. AI Code Audit
- Agenten skal analysere commit-historikk og PR-er for AI-generert kode.
- Finn:
  - Lavkvalitets generert kode
  - Mangel på input-validering
  - Repetitiv eller åpenbart maskinprodusert struktur
  - Mangel på dokumentasjon/tests

### 2. Security Controls
- Identifiser AI-kode som bryter:
  - Security best practices
  - OWASP
  - Ressursgrenser
  - Datahåndteringskrav

### 3. Governance Enforcement
- Agenten skal foreslå:
  - AI-commit labels
  - PR-templates for AI-generert kode
  - QA-krav (manual review, test coverage)
  - Automated linting og scanning

### 4. Risk Assessment
- For generert kode, rapporter:
  - Risiko: high/medium/low
  - Om kode må refaktoreres, fjernes eller valideres manuelt

### 5. Deliverables
- PR med:
  - Oversikt over funn
  - Forslag til governance-lag
  - Endringer i PR-mal
  - Sikkerhetsforbedringer

## Constraints
- Agenten skal ikke fjerne kritisk kode uten manuell vurdering.
