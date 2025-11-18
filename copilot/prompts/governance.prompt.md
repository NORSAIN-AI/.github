---
mode: agent
version: 1.1
owner: norsain/platform
visibility: public
permissions:
  commit: conditional
  pull_request: conditional
---
# Governance Prompt (NORSAIN-AI)

Du jobber på NORSAINs policy- og automasjonsrepo (`.github`).

## 📋 Retningslinjer

- Default: **ikke opprett commit eller PR automatisk**.
  Lever **Unified diff** først med forklaring.
- Når bruker eksplisitt ber om det (f.eks. *“lag commit”*, *“åpne PR mot main”*),
  kan du gjøre det — så lenge:
  - endringen er liten og tydelig (≤ 5 filer, ≤ 150 linjer)
  - PR følger NORSAIN-standard (Conventional Commits, sjekkliste, forklaring)
  - det ikke bryter sikkerhets- eller governance-policy

## 🧩 Trygge områder

- Oppdatere `.github/workflows/*.yml` (permissions, beskrivelser, validering)
- Forbedre `PULL_REQUEST_TEMPLATE.md` og issue-maler
- Oppdatere `README.md`, `CONTRIBUTING.md`, og `docs/README-DESIGN.md`
- Gjøre patcher relatert til Copilot- eller policy-instruksjoner

## ⚠️ Ikke gjør dette uten forespørsel

- Endre `LICENSE`
- Senke sikkerhetsnivå (permissions, branch protection)
- Fjerne validering (labels/milestone)
- Legge til hemmeligheter eller tokens

## 🧠 Husk

- Forklar alltid *Hva*, *Hvorfor* og *Hvordan verifisere*.
- Foreslå eller utfør endringer på en måte som er **gjennomsiktig og reproduserbar**.
- Ved commits/PRs: bruk `docs(...)`, `ci(...)`, `chore(...)`, eller `fix(...)` som commit-type.

> Kort sagt: du kan gjøre commits og PR-er **når du blir bedt om det** – men aldri på egen hånd.

© 2025 NORSAIN-AI • Copilot Governance Mode
