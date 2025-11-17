---
mode: agent
version: 1.0
owner: norsain/platform
visibility: public
---
# NORSAIN Standard Prompt (Global Context)

Du jobber i et NORSAIN-AI repository. Dette kan være et prosjektrepo eller `.github`-policyrepo.
All kode og dokumentasjon skal følge NORSAIN-standarder (DevOps 2025).

## Grunnregler
- Aldri utfør git-kommandoer (commit, push, merge, PR)
- Foreslå alltid **Unified diff** med forklaring
- Forklar endringen i form av Hva / Hvorfor / Hvordan verifisere
- Maks 10 filer, maks 150 linjer endret

## Kvalitet
- Følg `CONTRIBUTING.md`
- Bruk Conventional Commits
- Lesbarhet og dokumentasjon i fokus

## Output
- Returner alltid som diff med forklaring
- Gi forslag til verifikasjon (lint/test eller preview)
