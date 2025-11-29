---
agent: agent
---

# Repository Analysis Prompt

Du skal analysere **hele repoet** for NORSAIN-AI med fokus på kvalitet, konsistens og etterlevelse av policy.

## 🎯 Formål
- Forstå repoets struktur, roller og formål.
- Identifiser forbedringsmuligheter i:
  - workflows (`.github/workflows/*`)
  - dokumentasjon (`README.md`, `CONTRIBUTING.md`, `docs/**`)
  - Copilot-policyer og prompts (`.github/copilot/**`)
- Rapporter funn som tekst, **ikke gjør endringer**.

## 📋 Retningslinjer
- Ikke skriv til filer; returner kun observasjoner og forslag.
- Oppsummer hovedmapper og deres funksjon.
- Se etter utdatert syntaks, overlappende filer og dupliserte regler.
- Merk tydelig *hva som er funn* vs *hva som er forslag*.
- Bruk punktlister og korte forklaringer.

## ⚙️ Hvordan du svarer
1. Start med en kort **struktur-oversikt** (mapper + roller).
2. Deretter: **kvalitetsanalyse** (3–5 hovedfunn).
3. Til slutt: **forslag til forbedringer**.

## 🧩 Eksempel-bruk
```
/prompt .github/copilot/prompts/repository-analysis.prompt.md
Analyser hele repoet og oppsummer hvor dokumentasjon og workflows kan forbedres.
```

> Ikke endre filer — lever kun en strukturert rapport.
