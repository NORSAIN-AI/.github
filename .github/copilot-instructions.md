

# Copilot Instructions – NORSAIN-AI/.github

**Formål:**
Hjelp vedlikeholdere å forbedre dette org-nivå `.github`-repoet uten å skape støy i prosjektene som bruker det. Copilot skal foreslå små, sikre og begrunnede endringer – som **patch/diff** – aldri utføre git-handlinger.

---

## 1) Omfang (hva dette repoet er)

Dette repoet inneholder **felles politikk og automasjon** for hele organisasjonen:

* Reusable workflows i `.github/workflows/` (f.eks. `ci-reusable.yml`)
* PR-mal: `PULL_REQUEST_TEMPLATE.md`
* Issue-maler: `.github/ISSUE_TEMPLATE/{bug_report.yml, feature_request.yml, config.yml}`
* Bidragsregler: `CONTRIBUTING.md`
* Offentlig README: `README.md` (policy/bruk)
* **Ikke-forside** designnotater: `docs/README-DESIGN.md`
* Lisens: `LICENSE`

> Endringer her kan påvirke **alle repos** som refererer workflowene.

---

## 2) Mål for Copilot

* Foreslå **små, atomiske** forbedringer (≤ 5 endrede filer, ≤ 150 linjer totalt).
* Gi **patch/diff** og en kort begrunnelse (*Hva* + *Hvorfor*).
* Oppdage og rette **tvetydigheter** i maler og workflow-inputs.
* Forbedre **lesbarhet, konsistens og sikkerhet** (least privilege, ingen hemmeligheter).
* Holde dokumentasjon i **synk** (README, CONTRIBUTING, maler).

**Ikke-mål:** lage nye biblioteker, produktkode eller repo-spesifikke workflows for enkeltprosjekter (det hører hjemme i prosjekt-repoene).

---

## 3) Absolutte begrensninger

* ❌ **Aldri** opprett branches/commits/PR-er.
  Lever kun **Unified diff** i tekst.
* ❌ Ikke endre `LICENSE` (annet enn årstall ved behov, med begrunnelse).
* ❌ Ikke introduser hemmeligheter/credentials eller be om brede GitHub-tillatelser.
* ❌ Ikke fjern eksisterende validering (labels/milestone) uten klar grunn og mig-plan.
* ❌ Ikke bryt bakoverkompatibilitet i reusable workflows uten semver-notat.

---

## 4) Trygge oppgaver (go)

Copilot kan foreslå patch for:

* **Workflows**: klarere navn, beskrivelser, input-validering, least-privilege `permissions`, tydeligere feil-beskjeder, logger.
* **PR/Issue-maler**: bedre sjekklister, hjelpetekster, lenker til docs, konsekvent emoji/type-liste.
* **README/CONTRIBUTING**: oppdatere eksempler, TOC, badges, kodeblokker, rettelser, tydeliggjøring av bruk.
* **docs/README-DESIGN.md**: oppdatering ifm. README-endringer (synk-krav).
* **Konsekvent stil**: YAML-folding/ankere (kun hvis det øker lesbarhet), trailing spaces, quote-bruk, osv.

---

## 5) Oppgaver som krever eksplisitt godkjenning (ask first)

* Endre **valideringslogikk** i `ci-reusable.yml` (f.eks. slå av/om labels/milestones)
* Legge til **nye reusable workflows** som påvirker mange repos
* Endre **standard permissions** (f.eks. fra `contents: read` til `write`)
* Endre **PR-policy** (malens sjekkpunkter eller brudd på Conventional Commits)
* Flytte/fjerne filer som påvirker **organisasjonens standard**.

> For slike endringer: foreslå *alternativer* og *risiko/mitigering* i patch-kommentaren.

---

## 6) Filgrenser og konvensjoner

* **Workflows (`.github/workflows/*.yml`)**

  * Bruk `permissions` **per jobb/steg** (least privilege).
  * Hold på **input-flaggene**: `check-milestone`, `check-labels` m/ default `true`.
  * Kommenter *hvorfor* en sjekk feiler (bruk `actions/github-script` for tydelig melding).
  * Ikke bruk `pull_request_target` her med skrive-tilganger uten god grunn.

* **PR-mal (`PULL_REQUEST_TEMPLATE.md`)**

  * Behold type-seksjonen og sjekklisten.
  * Vær tydelig på **“Fixes #”** og testkrav.

* **Issue-maler**

  * Hold auto-labels for **triage**.
  * Unngå åpne tekstfelt uten veiledning (minimer støy).

* **README.md**

  * Topp-badges (CI, license) skal fungere for `main`.
  * Quick-start må speile faktisk `ci-reusable.yml`-bruk.
  * Ingen interne notater (de ligger i `docs/README-DESIGN.md`).

* **docs/README-DESIGN.md**

  * Oppdater når README endres; forklar *hvorfor*.

---

## 7) Format på forslag (påkrevd)

Når du foreslår endringer:

1. **Kort begrunnelse** (2–5 setninger): *Hva* + *Hvorfor*.
2. **Unified diff** per fil (riktige stier):

   ```diff
   diff --git a/.github/workflows/ci-reusable.yml b/.github/workflows/ci-reusable.yml
   --- a/.github/workflows/ci-reusable.yml
   +++ b/.github/workflows/ci-reusable.yml
   @@
   - permissions:
   -   contents: read
   + permissions:
   +   contents: read
   +   checks: write  # trengs for å opprette sjekk-konklusjoner
   ```
3. **Test/Verifikasjon**: Beskriv hvordan vedlikeholder kan verifisere (f.eks. åpne PR i sandbox-repo eller `workflow_dispatch` med inputs).

---

## 8) Commit- og PR-policy (for mennesker)

* **Conventional Commits** (type(scope): subject) – `ci(reusable): ...`, `docs(readme): ...`
* Små PR-er (≤ 5 filer).
* PR-beskrivelse: *Hva/ Hvorfor/ Risiko/ Hvordan teste*.
* Knytt issues (`Fixes #123`) ved endringer som påvirker konsument-repos.

---

## 9) Sikkerhet og personvern

* Ingen hemmeligheter i repoet (bruk GitHub Secrets der prosjekter trenger det – **ikke** her).
* Ikke be om tilganger utover behov; begrunn alle unntak.
* Bruk klar feilmelding når sjekker feiler (ikke lekke metadata).

---

## 10) Eksempel-prompter (bruk disse formuleringene)

* «Foreslå *patch/diff* som gjør `ci-reusable.yml` mer robust ved å feile med tydelig melding når `check-labels: true` og PR mangler labels. Ingen git-kommandoer.»
* «Lag *diff* som forbedrer `PULL_REQUEST_TEMPLATE.md`: legg til del for “Risiko/mitigering” og gjør sjekklisten tydeligere.»
* «Oppdater `README.md` badges og Quick-start slik at lenker peker korrekt til `main`-workflow. Kun nødvendige linjer.»
* «Synk `docs/README-DESIGN.md` med nye badge-valg; forklar hvorfor vi bruker `style=flat-square`.»

---

## 11) Hva Copilot skal **avvise**

* Forslag som introduserer hemmeligheter, brede permissions, eller uklare endringer.
* Forslag som endrer lisens eller fjerner krav i PR-validering uten sterk begrunnelse.
* Store refaktoreringer uten gevinst for **alle** konsument-repos.

---

## 12) Definisjon av ferdig (DoD)

* Patch er **liten**, **tydelig** og **reproduserbar**.
* README/Docs er oppdatert ved behov.
* Endringen er **bakoverkompatibel** eller merket som **breaking** med migrasjonsnotat.
* Verifikasjonstrinn er beskrevet.

---

© NORSAIN-AI • Offentlig repo – trygg automasjon og governance.
