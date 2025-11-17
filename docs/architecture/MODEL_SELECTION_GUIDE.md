# 🧠 MODEL_SELECTION_GUIDE.md
### NORSAIN Platform — Modellvalg for AI-agenter og Prompter
**Oppdatert:** 9. november 2025
**Formål:** Sikre riktig valg av LLM-modell til hver oppgavetype i prosjektet.

---

## 🎯 Mål
Denne guiden definerer **standardmodell per agent-type** i `prompts/`-mappen
og ved bruk i utvikling, CI/CD og dokumentasjon.

Målet er:
- Optimal **balanse mellom kostnad, hastighet og nøyaktighet**
- Konsistent **modellbruk i metadata (`model:`)**
- Raskere og tryggere kjøring av agenter og Copilot-kommandoer

---

## ⚙️ Modellmatrise

| Kategori | Oppgavetype | Anbefalt modell | Alternativ | Kommentar |
|-----------|--------------|-----------------|-------------|------------|
| 🧱 **Bootstrap & Setup** | Repo-struktur, migrasjoner, pipelines<br>*(f.eks. `ims-db-bootstrap`, `bootstrap-app-structure`)* | **GPT-5** | GPT-4o | Best i presisjon og multi-fil generering (TypeScript/SQL). |
| 🔐 **Auth / Security / Config** | Middleware, env-validering, headers | **GPT-5 mini** | GPT-5 | Rask, trygg og presis for kode + validering. |
| 🔍 **Repoanalyse / Kvalitet** | Pre-commit, pre-flight, repo-analyse | **Claude Sonnet 4.5** | Claude Sonnet 3.5 | Overlegen på policy, språk og analyse. |
| ⚙️ **CI/CD & Release** | Workflows, commit/PR, release-prep | **GPT-4.1** | Claude 4.5 | YAML/semver/logikk – svært pålitelig. |
| 🧩 **Refaktorering & Autofix** | Struktur og lint-forbedringer | **Grok Code Fast 1** | GPT-5 mini | Spesialisert på rask kodeanalyse og sikker autofix. |
| 🧪 **Testing & Verifikasjon** | Vitest-generering, feilsjekk | **GPT-5 mini** | GPT-5 | Genererer gode, trygge testcases. |
| 📘 **Dokumentasjon & Readmes** | Docs, guides, changelogs | **Claude Sonnet 4.5** | Claude Haiku 4.5 | Presis, kortfattet og teknisk korrekt tekst. |
| 🧠 **Læringsagenter** | Next.js / Web App læring | **GPT-5** | GPT-4o | Lang kontekst og avansert læringsforklaring. |

---

## 🧩 Retningslinjer for bruk

1. **Default-modell:**
   Hvis ikke annet er spesifisert i prompt-metadata, bruk `model: GPT-5`.

2. **Mini-varianter (f.eks. GPT-5 mini):**
   Brukes for raske operasjoner (≤150 linjer, små diffs, autofix, tester).

3. **Claude Sonnet-serien:**
   Bruk ved språklig analyse, policy-gjennomgang eller dokumentasjon.
   Ideell for markdown, PR-tekster og repo-review.

4. **Grok Code Fast 1:**
   Kun for *trygge refaktoreringer* — ikke bruk til feature-generering.

5. **Gemini 2.5 Pro:**
   Valgfri som tredjepartssjekk ved komplekse ML eller RAG-scenarier.

---

## 🧮 Modellprioritet ved fallback

| Nivå | Modell | Når brukes |
|------|---------|------------|
| 1️⃣ | GPT-5 | Standard for alle kodeoppgaver |
| 2️⃣ | GPT-5 mini | Ved små, raske operasjoner |
| 3️⃣ | Claude Sonnet 4.5 | Ved dokumentasjon eller analyse |
| 4️⃣ | GPT-4.1 | YAML/CI/CD og semver |
| 5️⃣ | Grok Code Fast 1 | Autofix/refactor |
| 6️⃣ | Gemini 2.5 Pro | Backup ved AI-integrasjoner |

---

## 🧾 Eksempel på prompt-metadata

```yaml
---
mode: agent
description: "Generate Turbo pipelines for optimized builds."
model: GPT-5
tools: ["code-editor", "file-manager"]
---
```

eller for raskere oppgaver:

```yaml
---
mode: agent
description: "Fix small lint and type errors safely."
model: GPT-5 mini
tools: ["code-editor"]
---
```

---

## 🧰 Integrasjon med repoet

* **Filplassering:** `docs/architecture/MODEL_SELECTION_GUIDE.md`
* **Referanse i prompter:** alle `.prompt.md`-filer skal samsvare med denne guiden.
* **Oppdatering:** revider guiden ved nye modeller eller endret kostnadsprofil.

---

## ✅ Oppsummering

* **GPT-5** → standardmodell for kode, arkitektur, og læring
* **GPT-5 mini** → rask utførelse (autofix, tester, små endringer)
* **Claude Sonnet 4.5** → dokumentasjon og repoanalyse
* **Grok Code Fast 1** → ren refaktorering
* **GPT-4.1 / Gemini** → spesialtilfeller (CI/CD og ML)

---

> 🔒 **Mål:**
> Riktig modellvalg = høy kvalitet, lav kostnad og konsistente resultater i hele Norsain-agentbiblioteket.
