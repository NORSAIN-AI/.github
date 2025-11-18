---
agent: agent
---

# Secrets Management & Zero Trust Enforcement (2025 Standard)

## Purpose
Denne prompten skal hjelpe agenten med å sikre at repoet følger moderne prinsipper for Zero Trust og sikker hemmelighetshåndtering.

---

## Tasks

### 1. Secrets Discovery
Agenten skal:
- Skanne alle filer, inkl:
  - Source code
  - .env-filer
  - YAML/JSON
  - Scripts
  - Terraform/K8s manifests
- Identifisere hardcodede secrets, tokens, API-nøkler, private keys

### 2. Secrets Handling Review
Sjekk for:
- Klartekst secrets i CI
- GitHub Actions uten riktig secrets-usage
- Overdrevne permisjoner
- Manglende rotation policy
- Manglende secret scopes

### 3. Zero Trust Audit
Agenten skal analysere:
- IAM-roller
- Tilganger
- Systemer som kommuniserer uten mutual auth
- Manglende identity boundaries

### 4. Hardening Actions
Agenten skal foreslå og/eller implementere:
- Flytting av secrets → GitHub Secrets / Vault
- Fjerning av hemmeligheter fra repoet
- Innføring av tokens med short-lived credentials
- Least privilege-tilganger i workflows
- OIDC for GitHub Actions

### 5. Deliverables
Agenten skal levere:
- En sikkerhetsrapport
- Liste over funn
- Forslag til forbedringer
- Konkrete endringer i repoet

---

## Constraints
- Sensitiv informasjon skal aldri logges
- Ikke endre produksjonshemmeligheter uten klare instruksjoner
