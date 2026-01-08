---
agent: agent
---

# Repository Knowledge Graph Builder (2025 Standard)

## Purpose
Denne prompten gir agenten mandat til å bygge en *intern kunnskapsgraf* for repoet: filer, moduler, komponenter, APIs, scripts, workflows og deres relasjoner.

---

## Tasks

### 1. Repo Structure Mapping
Agenten skal analysere:
- Alle mapper og fil relasjoner
- Import-kjeder (TS/JS/Python hvis relevant)
- CI-pipelines og hvordan de kobles sammen
- Scripts og deres avhengigheter

### 2. Knowledge Graph Construction
Agenten skal generere:
- En grafstruktur (JSON/YAML) representert som noder og edges:
  - Node = fil, modul eller komponent
  - Edge = dependency/usage/import
- Klassifisering av noder:
  - frontend
  - backend
  - infra
  - scripts
  - domains

### 3. Hotspot & Risk Detection
- Identifiser:
  - Overkomplekse moduler
  - Single points of failure
  - High fan-in/fan-out noder
  - Ulogiske avhengigheter

### 4. Deliverables
Agenten skal lage:
- `/docs/repository-knowledge-graph.json` eller `.yaml`
- En PR med:
  - Grafen
  - Dokumentasjon
  - Visualiseringsforslag (kan være eksternt)

---

## Constraints
- Ikke endre kode utenfor mapping
- Kun les/analyser—ingen modifikasjon
