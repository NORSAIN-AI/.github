---
agent: agent
---

# Observability, Logging & Metrics Baseline (2025 Standard)

## Purpose
Denne prompten etablerer et standardisert observability-grunnlag for alle applikasjoner i repoet.

## Tasks

### 1. Logging Audit
- Finn:
  - Manglende strukturerte logger
  - Uklare log-nivåer
  - Logging av sensitive data
  - Manglende correlation IDs

### 2. Metrics & Instrumentation
- Identifiser hvor applikasjonen mangler:
  - CPU/latency/hot-path metrics
  - Domain/business metrics
  - Error-rate instrumentering
- Foreslå instrumentering via:
  - OpenTelemetry
  - Prometheus
  - Eventuelle platform-standarder

### 3. Tracing Integration
- Sjekk om tracing kan:
  - Legges til i API-lag
  - Sammenkoble requests med correlation id
  - Distribueres via OTel exporter

### 4. Config Review
- Sjekk logging-konfig for:
  - For høy verbositet
  - Ikke-produksjonsklare formater
  - Manglende rotation/retention

### 5. Deliverables
- PR som:
  - Legger til observability-hooks
  - Oppdaterer logger til structured JSON
  - Legger inn stub-metrics
  - Oppdaterer dokumentasjon

## Constraints
- Ikke overinstrumenter – kun baseline-nivå.
