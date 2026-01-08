---
agent: agent
---

# Infrastructure Drift Detection & IaC Compliance Enforcement (2025 Standard)

## Purpose
Agenten skal gjennomføre en full analyse av infrastrukturkode (IaC) i repoet for å oppdage drift-avvik, sikkerhetsavvik og konsistensproblemer.

## Tasks

### 1. IaC Inventory
- Identifiser alle filer relatert til:
  - Terraform
  - Pulumi
  - Kubernetes manifests
  - Docker compose
  - Cloud-init / scripts
- Bygg en oversikt i PR-beskrivelsen.

### 2. Drift Detection & Consistency
- Sjekk om:
  - Ressurser mangler tags/labels
  - Naming-conventions brytes
  - Sikkerhetspolicyer mangler
  - Versjonskrav er udefinert
  - Ulike miljøer (dev/test/prod) er inkonsistente

### 3. Security Review
- Sjekk for:
  - Publicly exposed resources
  - Løse IAM-policyer
  - Manglende encryption-at-rest
  - Manglende network-restriksjoner
  - Manglende audit-logging

### 4. Compliance Enforcement
- Implementer:
  - Standard tags
  - Sert standard naming-conventions
  - Ressursgrenser
  - Minstelogging
  - Kodeformat (terraform fmt + lint)

### 5. Deliverables
- PR med:
  - Drift report
  - Compliance fixes
  - Risikoanalyse
  - Forslag til fremtidige forbedringer

## Constraints
- Ikke utfør destruktive endringer uten eksplisitt markering.
