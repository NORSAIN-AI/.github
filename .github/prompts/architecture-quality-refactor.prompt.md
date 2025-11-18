---
agent: agent
---

# Code Quality, Architecture & Technical Debt Refactor (2025 Standard)

## Purpose
Denne prompten skal brukes av en repo-agent til å identifisere teknisk gjeld, arkitektoniske svakheter, duplisert kode og forbedringsmuligheter. Målet er å holde kodebasen sunn, konsistent og modernisert gjennom hele 2025.

## Tasks the agent must perform

### 1. Code Quality Review
- Analyser hele kodebasen for:
  - duplisert kode
  - ubrukte funksjoner, moduler eller config
  - anti-patterns (f.eks. for lange filer, store funksjoner, dårlig navngivning)
  - utilstrekkelige typer (TS), untyped APIs

### 2. Architecture Assessment
- Kartlegg:
  - mappestruktur
  - modulgrenser
  - coupling vs. cohesion
  - utils vs. core-domenemodeller
- Foreslå forbedret arkitektur for 2025-standarder (modulært, lett testbart, domain-driven eller ports/adapters)

### 3. Performance & Maintainability Review
- Identifiser ineffektiv kode:
  - unødvendige IO-operasjoner
  - dårlig caching/lagring
  - ineffektiv dataflyt
- Foreslå konkrete forbedringer

### 4. Documentation & Developer Experience
- Analyser README, docs, scripts, Makefile
- Foreslå forbedringer til:
  - onboarding
  - developer setup
  - build-modellen
  - test-strategi

### 5. Deliverables
Agenten skal produsere:
- En komplett PR-beskrivelse med:
  - Funn
  - Refactor-plan (trinnvis)
  - Faktiske endringer (kommitter)
  - Dokumentasjonsoppdateringer
- En «Technical Debt Register» som kan følges opp videre

## Constraints
- Agenten skal IKKE endre forretningslogikk
- Bare forbedre struktur, kvalitet og maintainability
- Refactor må være 100 % bakoverkompatibel
