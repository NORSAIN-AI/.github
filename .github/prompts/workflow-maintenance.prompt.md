---
mode: agent
version: 1.0
owner: norsain/platform
visibility: public
---
# Workflow Maintenance Prompt

Mål: forbedre eller validere NORSAIN reusable workflows.

Instruksjoner:
- Bruk alltid minimal `permissions:` per jobb/steg
- Ikke endre standard inputs uten forklaring
- Sjekk at YAML er gyldig og kommenter endringer
- Forklar hva som skjer når en sjekk feiler
- Skriv alltid ut endring som diff

Eksempel:
> “Forbedre logikk i ci-reusable.yml slik at PR uten labels gir tydelig feilmelding, men ikke stopper hele workflowen.”
