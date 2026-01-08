---
agent: agent
---

# Frontend Quality & UI Accessibility Audit (WCAG 2.2 Standard)

## Purpose
Denne prompten skal brukes av en repo-agent til å utføre en fullstendig kvalitetssjekk av frontend-koden, inkludert UX, struktur, tilgjengelighet og ytelse. Agenten skal sikre at frontend-en koden er robust, forståelig, lett å vedlikeholde og følger WCAG 2.2.

---

## Tasks the agent must perform

### 1. Frontend Codebase Analysis
- Identifiser:
  - Duplisert UI-kode
  - For lange komponenter
  - Mangel på modulær struktur
  - Inkonsekvent state-håndtering
  - Overdreven bruk av any/unkown (TS)

### 2. WCAG 2.2 Accessibility Audit
Agenten skal sjekke for:
- Manglende `aria-*` attributter
- Manglende label-for-koblinger
- Manglende tastaturnavigasjon
- Kontrastkrav (minimum AA)
- Semantiske HTML-feil
- Fokusfeller eller manglende focus-ring
- Umerkede interaktive elementer
- Manglende alt-tekster

### 3. Performance & Rendering Review
- Identifiser:
  - Uoptimal rendering (re-renders)
  - Manglende memoization
  - Store bundle sizes
  - Tunge komponenter som ikke bør være i UI-laget
  - Blocking JS

### 4. CSS/Design Consistency
- Oppdag:
  - Inline styling som burde vært abstrahert
  - Hardcodede farger/spacing
  - Manglende design-tokens
  - Ubrukte eller dupliserte klasser

### 5. Deliverables
Agenten skal levere:
- Funnrapport (WCAG, performance, maintainability)
- Forslag til refactor
- Konkrete kodeendringer som:
  - Bedrer tilgjengelighet
  - Reduserer teknisk gjeld
  - Øker UI-konsistens
- Oppdaterte docs for frontend-standarder

---

## Constraints
- Ikke endre visuell design drastisk uten merking
- Ytelsesoptimaliseringer må være trygge og målbare
