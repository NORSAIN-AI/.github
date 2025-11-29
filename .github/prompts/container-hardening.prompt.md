---
agent: agent
---

# Container Security & Docker Hardening (2025 Standard)

## Purpose
Denne prompten instruerer agenten til å gjennomføre en full sikkerhets- og robusthetsrevisjon av alle Docker-relaterte artefakter i repoet og implementere anbefalte forbedringer.

## Tasks the agent must perform

### 1. Dockerfile Analysis
- Identifiser:
  - Bruk av root-bruker
  - Manglende `USER`-statement
  - Uspesifikke base-images (f.eks. `latest`)
  - Manglende `HEALTHCHECK`
  - Manglende `ENTRYPOINT`/`CMD`
  - Layer-inflasjon eller unødvendige pakker
  - Uoptimal caching (reordering av RUN-steps)

### 2. Multi-stage Optimization
- Foreslå og implementer multi-stage build om:
  - binary-build → runtime-image
  - ts/python → dist → runtime
- Optimaliser image-størrelse og sikkerhetsfotavtrykk.

### 3. Security Hardening
- Implementer:
  - Non-root user
  - Drop of capabilities
  - Read-only filesystem når mulig
  - Minimale base-images (distroless/alpine)
  - Eksplisitte versjoner på alle images

### 4. Docker Compose / Kubernetes / OCI Files
- Sjekk for:
  - Overly permissive settings (privileged, hostPath)
  - Unsecure env-vars
  - Manglende resource limits
  - Udefinert restart policy

### 5. Deliverables
Agenten skal produsere:
- En commit/PR som forbedrer sikkerhet, stabilitet og ytelse.
- En rapport i PR-beskrivelsen med:
  - Funn
  - Endringer
  - Risikoer
  - Videre tiltak

## Constraints
- Ingen breaking changes i runtime med mindre nødvendig og merket.
- Endringer skal være reversible og dokumentert.
