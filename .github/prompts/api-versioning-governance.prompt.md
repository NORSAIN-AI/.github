---
agent: agent
---

# Backend API Stability & Versioning Governance (2025 Standard)

## Purpose
Denne prompten skal gi agenten mandat til å gjennomføre en full API-stabilitetsanalyse og etablere governance rundt API-versjonering, endringskontroll og backward compatibility.

---

## Tasks

### 1. API Inventory
Agenten skal kartlegge:
- Alle API-endepunkter (REST/GraphQL/gRPC)
- Hvilke modeller, DTOer og kontrakter som brukes
- API-forbrukere (interne/eksterne)
- Versjonsstrategi som evt. allerede er i bruk

### 2. Breaking Change Detection
Analysér API-kontraktene og identifiser:
- Endringer som bryter backward compatibility
- Endringer som mangler migrasjon
- Inkonsekvent naming/struktur
- Utydelig validering

### 3. Versioning Governance
Agenten skal:
- Definere eller harmonisere versjonsstrategi:
  - SemVer
  - URL-versjonering
  - Header-basert versjonering
- Anbefale depraction-policyer
- Anbefale stability-status (deprecated/beta/stable)

### 4. API Design Quality Review
Sjekk for:
- Uklare responstyper
- For store payloads
- Manglende idempotens på POST/PUT
- Manglende dokumentasjon (OpenAPI/GraphQL schema)
- Manglende input-validering

### 5. Deliverables
Agenten skal produsere:
- API governance-rapport
- Liste over breaking changes
- Forslag til forbedringer i struktur, dokumentasjon og versjonering
- Oppdaterte API-dokumentasjonsfiler

---

## Constraints
- Ikke fjerne API-endepunkter uten deprecation-flow
- Behold backward compatibility der det er mulig
