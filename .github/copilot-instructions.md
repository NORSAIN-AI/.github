# Copilot Instructions – NORSAIN-AI/.github
Du jobber i NORSAINs organisasjonsnivå `.github`-repo, som inneholder felles policy og automasjon for alle prosjekter.

---
**Formål:**
Gi Copilot klare rammer for hvordan den kan hjelpe vedlikeholdere å forbedre dette org-nivå `.github`-repoet.
Copilot skal som standard foreslå **små, sikre og begrunnede endringer** (patch/diff), men kan utføre commits eller PR-er når det blir **eksplisitt bedt om** og er innenfor NORSAIN-policy.

---

## 1 Omfang (hva dette repoet er)

Dette repoet inneholder **felles politikk og automasjon** for hele NORSAIN-organisasjonen:

- Reusable workflows i `.github/workflows/` (f.eks. `ci-reusable.yml`)
- PR-mal: `PULL_REQUEST_TEMPLATE.md`
- Issue-maler: `.github/ISSUE_TEMPLATE/{bug_report.yml, feature_request.yml, config.yml}`
- Bidragsregler: `CONTRIBUTING.md`
- Offentlig README: `README.md` (policy/bruk)
- Designnotater: `docs/README-DESIGN.md` (ikke forside)
- Lisens: `LICENSE`

- Copilot-governance: `copilot-instructions.md` (dette dokumentet)
---

## 2 Mål for Copilot

- Foreslå **små, atomiske** forbedringer (≤ 5 filer, ≤ 150 linjer totalt)
- Gi **patch/diff** og en kort begrunnelse (*Hva* + *Hvorfor*)
- Oppdage og rette **tvetydigheter** i maler og workflow-inputs
- Forbedre **lesbarhet, konsistens og sikkerhet** (least privilege, ingen hemmeligheter)
- Holde dokumentasjon i **synk** (`README.md`, `CONTRIBUTING.md`, maler, docs)

**Ikke-mål:**
- Lage nye biblioteker eller kode for produktprosjekter
- Lage repo-spesifikke CI/CD-workflows (det skjer i prosjekt-repoene)

---

## 3 Handlingsgrenser

- **Som standard:** Copilot skal ikke opprette branches, commits eller PR-er automatisk.
  Den skal alltid levere **Unified diff** først.
- **Unntak:** Når en menneskelig vedlikeholder eksplisitt ber om det
  (f.eks. “Lag commit” eller “Åpne PR mot main”),
  kan Copilot utføre handlingen, men:
  - Endringen må være gjennomgått eller forklart først.
  - PR må følge sjekklisten og naming conventions (`chore/`, `fix/`, `docs/` osv).
- Ikke endre `LICENSE` (annet enn årstall ved behov, med begrunnelse).
- Ikke introduser hemmeligheter eller be om brede GitHub-tillatelser.
- Ikke fjern validering (labels/milestone) uten migrasjonsplan.
- Ikke bryt bakoverkompatibilitet i reusable workflows uten semver-notat.

---

## 4 Trygge oppgaver

Copilot kan foreslå patcher for:

- **Workflows:** bedre navn, input-validering, minst mulig `permissions`, tydelige feilmeldinger og logger
- **PR/Issue-maler:** mer presise sjekklister, hjelpetekster, lenker til docs, konsistente emojis
- **README/CONTRIBUTING:** oppdatere eksempler, TOC, badges, tydeliggjøring av bruksinstruks
- **docs/README-DESIGN.md:** synkronisering ved endringer i README
- **Formattering:** YAML-anbefalinger, whitespace, konsistent quoting (uten funksjonelle endringer)

---

## 5 Oppgaver som krever eksplisitt godkjenning

- Endre **valideringslogikk** i `ci-reusable.yml`
- Legge til **nye reusable workflows** som påvirker mange repos
- Endre **standard permissions** (f.eks. `contents: write`)
- Endre **PR-policy** (malens krav, commit-regler, valideringspunkter)
- Flytte/fjerne filer som påvirker **organisasjonsstandard**



---

## 6 Filgrenser og konvensjoner

### **Workflows (`.github/workflows/*.yml`)**
- Bruk `permissions` **per jobb/steg** (least privilege)
- Behold input-flaggene: `check-milestone`, `check-labels` med default `true`
- Kommenter hvorfor en sjekk feiler (bruk `actions/github-script`)
- Ikke bruk `pull_request_target` med skrive-tilgang uten sterk begrunnelse

### **PR-mal (`PULL_REQUEST_TEMPLATE.md`)**
- Behold type-seksjon og sjekkliste
- Krav om “Fixes #” eller “Relates to #”
- Klare testpunkter

### **Issue-maler**
- Behold auto-labels for triage
- Unngå åpne tekstfelt uten veiledning

### **README.md**
- Badges skal fungere for `main`
- Quick-start må reflektere faktisk bruk av `ci-reusable.yml`
- Ingen interne notater (bruk `docs/README-DESIGN.md`)

### **docs/README-DESIGN.md**
- Oppdater ved README-endringer
- Forklar *hvorfor* endringen ble gjort

---

## 7 Format for forslag

Når du foreslår endringer:

1. **Kort begrunnelse (2–5 setninger):** Hva + Hvorfor
2. **Unified diff** per fil, med riktige stier:
   ```diff
   diff --git a/.github/workflows/ci-reusable.yml b/.github/workflows/ci-reusable.yml
   --- a/.github/workflows/ci-reusable.yml
   +++ b/.github/workflows/ci-reusable.yml
    @@ -10,6 +10,8 @@ jobs:
      build:
      runs-on: ubuntu-latest
   - permissions:
   -   contents: read
   + permissions:
   +   contents: read
   +   checks: write  # nødvendig for å opprette sjekk-konklusjoner
   ```

3. **Test/verifikasjon:** Beskriv hvordan endringen kan valideres (PR, workflow_dispatch, test-branch)

---

## 8 Commit- og PR-policy (for mennesker)

* Følg **Conventional Commits**:
  `ci(reusable): ...`, `docs(readme): ...`, `fix(template): ...`
* Små PR-er (≤ 5 filer)
* PR-beskrivelse må forklare:

  * Hva endres
  * Hvorfor
  * Risiko
  * Hvordan teste
* Knytt issues med `Fixes #` eller `Relates to #`

---

## 9 Sikkerhet og personvern

* Ingen hemmeligheter i repoet (bruk GitHub Secrets i prosjekter, ikke her)
* Ikke be om eller lagre tokens i kode
* Alle permissions må være nødvendige og begrunnede
* Klare feilmeldinger ved feil — aldri lek metadata eller konfidensiell info

---

## 10 Eksempel-prompter

* “Foreslå *patch/diff* som gjør `ci-reusable.yml` mer robust ved å feile tydelig når `check-labels: true` og PR mangler labels.”
* “Lag patch som utvider `PULL_REQUEST_TEMPLATE.md` med del for Risiko/mitigering.”
* “Oppdater `README.md` badges slik at de peker til `main`-workflow.”
* “Synkroniser `docs/README-DESIGN.md` med endringer i README, og forklar hvorfor badge-stilen er flat-square.”

---

## 11 Hva Copilot skal **avvise**

* Forslag som introduserer hemmeligheter eller brede permissions
* Forslag som fjerner sikkerhets-/valideringskrav uten migrasjonsnotat
* Store refaktoreringer uten gevinst for alle konsument-repos
* Endringer uten dokumentert hensikt eller testplan

---

## 12 Definisjon av ferdig (DoD)

* Endringen er **liten, tydelig og reproduserbar**
* README/Docs oppdatert der det er relevant
* Ingen brudd på bakoverkompatibilitet uten versjonsnotat
* Verifikasjonstrinn beskrevet i PR-beskrivelsen

---

© 2025 NORSAIN-AI — Offentlig repo • trygg automasjon og Copilot governance

```