---
agent: agent
---

# Secure Codebase & Dependency Hardening Audit (2025 Standard)

## Purpose
Denne prompten skal brukes av en repo-agent til å gjennomføre en full sikkerhetsrevisjon av kodebasen, avhengigheter, konfigurasjon og CI/CD. Målet er å sikre at repoet oppfyller moderne standarder for programvaresikkerhet i 2025.

## Tasks the agent must perform

### 1. Repository Security Scan
- Identifiser usikre mønstre i kildekode (TS, Python, YAML, Docker, scripts)
- Finn hardcodede hemmeligheter, API-nøkler, tokens eller unødvendig sensitive data
- Marker usikre konfigurasjoner (f.eks. brede IAM-roller, eksponerte porter, feilaktig CORS)

### 2. Dependency Hardening
- Analyser alle dependencies i:
  - package.json
  - requirements/dependencies (hvis relevante)
  - Dockerfile
- Identifiser sårbarheter (CVE-er), deprecated pakker og versjonskonflikter
- Foreslå sikre versjoner og evt. erstatning av pakker

### 3. CI/CD Security Review
- Sjekk GitHub Actions for:
  - Uspesifiserte versjoner
  - Actions som ikke er pinned med SHA
  - Actions som kjører scripts uten sandbox
  - Secrets-håndtering og minst-privilegium
- Anbefal forbedringer

### 4. Infrastructure & Config Security
- Analyser:
  - Dockerfile
  - K8s-manifester
  - Terraform/infra (hvis tilstede)
  - .env.example
- Identifiser svakheter: root-bruk, utilstrekkelig logging, manglende ressurspolicyer, osv.

### 5. Deliverables
Agenten skal lage:
- Full rapport i PR-beskrivelse
- Liste over funn (severity: high/medium/low)
- Konkrete forslag til forbedringer
- Forslag til auto-fix commits der det er trygt
- En sikkerhets-baseline for miljøet

## Constraints
- Ikke utfør breaking changes uten tydelig merking
- Ingen hemmeligheter skal logges
- Endringer skal være reversible
