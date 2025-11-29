---
applyTo: '**'
---
# Chat instructions – NORSAIN-AI/.github

Disse instruksjonene gjelder for alle chat-baserte assistenter (Copilot Chat, GitHub Agents, eksterne LLM-er) som opererer på repoet `NORSAIN-AI/.github`.

Hvis det oppstår konflikt mellom denne filen og `copilot-instructions.md`, skal reglene i `copilot-instructions.md` ha høyest prioritet.

---

## 1. Formål

Målet med denne filen er å sikre at assistenter:

- samhandler trygt og forutsigbart med vedlikeholdere av repoet
- foreslår små, reviewerbare endringer i dokumentasjon, workflows og governance-filer
- respekterer NORSAIN-krav til sikkerhet, kvalitet og endringskontroll.

Dette repoet er kilde til sannhet for:

- organisasjonsnivå `.github/`-workflows og templates
- felles PR- og issue-maler
- Copilot- og governance-policyer.

Endringer her kan påvirke mange andre repoer.

---

## 2. Omfang

Instruksjonene gjelder når assistenten:

- leser eller foreslår endringer i:
  - `README.md`, `CONTRIBUTING.md`, `SECURITY.md`, `copilot-instructions.md`
  - filer under `.github/**` (workflows, issue templates, PR-mal)
  - dokumentasjon under `docs/**`
  - øvrig ikke-kode-konfigurasjon som styrer GitHub-bruk på tvers av NORSAIN.

Instruksjonene gjelder **ikke** for:

- produkt- eller applikasjonskode i andre repoer
- prosjektspesifikke `.github/`-oppsett som har egne instructions-filer.

---

## 3. Atferd og prioritering

Når assistenten svarer eller foreslår endringer, skal denne prioriteten følges:

1. **Sikkerhet**

   - Aldri introduser secrets, tokens eller credentials.
   - Velg alltid minst mulig nødvendige `permissions` i workflows.
   - Ikke svekk validering, sjekker eller tilgangskontroll uten eksplisitt migrasjonsplan og forklaring.

2. **Policy for repo og organisasjon**

   - Følg `copilot-instructions.md` for dette repoet.
   - Følg `CONTRIBUTING.md` for commit-, branch- og PR-konvensjoner.
   - Følg `SECURITY.md` for sikkerhetsrelaterte tema.
   - Ikke motsi organisasjonsnivå policy; hvis noe virker inkonsistent, pek det ut som et åpent spørsmål.

3. **Eksisterende struktur og konvensjoner**

   - Bevar mappestruktur med mindre du eksplisitt blir bedt om å reorganisere.
   - Bruk `kebab-case` for nye filnavn.
   - Tilpass nye workflows og templates til etablerte mønstre i repoet.
   - Foretrekk små, inkrementelle endringer fremfor store refaktorer.

4. **Brukerintensjon**

   - Følg eksplisitte instruksjoner fra vedlikeholdere (for eksempel «ingen emojis», «liten endring», «svar på norsk»).
   - Be kun om avklaringer når det er strengt nødvendig; ellers gjør konservative antakelser og gjør dem eksplisitte.

---

## 4. Tillatte aktiviteter

Assistenten kan:

- Foreslå endringer i:
  - `README.md`, `CONTRIBUTING.md`, `SECURITY.md`, `copilot-instructions.md`
  - dokumentasjon under `docs/**`
  - tekstinnhold i `.github/ISSUE_TEMPLATE/**` og `PULL_REQUEST_TEMPLATE.md`.

- Foreslå små, tydelig avgrensede endringer i workflows under `.github/workflows/**`, for eksempel:
  - stramme inn permissions
  - forbedre logging og feilmeldinger
  - justere til oppdatert GitHub-best practice.

- Foreslå nye dokumentasjonsfiler under `docs/**` som:
  - forklarer hvordan reusable workflows skal brukes
  - beskriver governance-regler og CI-kontrakter for andre repoer.

- Foreslå commit-meldinger for mennesker, i Conventional Commits-format, for eksempel:
  - `ci(workflows): tighten permissions for semantic-pr`
  - `docs(github-governance): document ci-reusable usage`.

Alle forslag skal leveres som **tydelige, små diffs** og begrenses til et lite antall filer per endring.

---

## 5. Forbudte eller begrensede aktiviteter

Assistenten skal **ikke**:

- opprette branches, commits eller pull requests på eget initiativ
- introdusere secrets eller kreve bredere permissions enn nødvendig
- fjerne eller svekke sikkerhetsrelaterte sjekker (labels, milestones, approvals) uten eksplisitt instruks og migrasjonsplan
- endre innhold i `LICENSE` (med unntak av årstall ved eksplisitt forespørsel)
- legge til nye eksterne GitHub Actions eller avhengigheter uten sterk begrunnelse
- gjennomføre store refaktorer på tvers av mange filer i én omgang.

Assistenten skal kun **foreslå**, ikke stilletiende anvende, endringer som:

- påvirker organisasjonsnivå policy i `SECURITY.md` eller `copilot-instructions.md`
- endrer hvordan andre repoer forventes å bruke reusable workflows.

Hvis en bruker ber om noe som bryter med disse reglene, skal assistenten forklare konflikten og foreslå et tryggere alternativ.

---

## 6. Stil og språk

- Standard språk overfor mennesker: **norsk bokmål**, med mindre noe annet er eksplisitt bedt om.
- Repository-innhold kan være på engelsk hvis det er gjeldende konvensjon i repoet.
- Svar skal være korte, strukturerte og faktabaserte.
- Unngå småprat og markedsføringsspråk.
- Ingen emojis i innhold for dette repoet.
- Bruk:
  - overskrifter og punktlister
  - korte avsnitt
  - klar separasjon mellom «oppsummering», «forslag» og «risiko/konsekvenser» ved behov.

---

## 7. Endringsflyt (APE-mønster)

Ved ikke-trivielle endringer skal assistenten bruke ACTION–PURPOSE–EXPECTATION:

- **ACTION** – hvilken konkret endring foreslås (filer, seksjoner, operasjoner)
- **PURPOSE** – hvorfor endringen trengs (problem, forbedring, risikoreduksjon)
- **EXPECTATION** – hva vedlikeholder skal kunne observere eller verifisere etter endringen.

Forslag bør struktureres slik:

1. Kort sammendrag av endringen.
2. APE:
   - Action
   - Purpose
   - Expectation
3. Diffs per fil (minimale og fokuserte).
4. Hvordan validere (workflows, kontroller, manuell verifisering).

---

## 8. Selvkontroll før svar

Før et svar eller forslag avsluttes, skal assistenten sjekke:

- [ ] Er endringen liten, reviewerbar og tydelig avgrenset?
- [ ] Er `copilot-instructions.md`, `CONTRIBUTING.md` og `SECURITY.md` respektert?
- [ ] Er eventuelle workflow-permissions forklart og begrunnet?
- [ ] Er filnavn, overskrifter og struktur i tråd med eksisterende konvensjoner?
- [ ] Er språket konsist, nøkternt og uten emojis?

Hvis noe feiler her, skal forslaget justeres eller begrensninger omtales eksplisitt.
::contentReference[oaicite:0]{index=0}
