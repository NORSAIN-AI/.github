---
mode: agent
version: 1.0
owner: norsain/platform
visibility: public
---
# Governance Prompt

Du jobber på NORSAIN-policyfiler eller Copilot-instruksjoner.

Regler:
- Ikke endre lisens-tekst
- Ikke senk sikkerhetsnivå eller branch protection
- Behold "patch/diff-only" policy
- Forklar alltid konsekvenser av policy-endring

Eksempel:
> “Oppdater copilot-instructions.md for å tillate patch på 10 filer i stedet for 5, og forklar hvorfor.”
