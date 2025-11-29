# README Design Notes – NORSAIN-AI/.github

> Internt dokument for vedlikeholdere og dokumentasjonsansvarlige.
> Beskriver designrasjonale bak den offentlige `README.md`-filen i dette repoet.

---

## 🎯 Formål

Dette dokumentet forklarer **hvorfor** hoved-README ser ut som den gjør, slik at fremtidige vedlikeholdere og Copilot-agenter kan videreføre samme stil og kvalitet.

---

## 💡 Designmål for offentlig README

| Mål | Forklaring |
|-----|-------------|
| **Profesjonell førsteinntrykk** | Skal vise NORSAIN-AI som en moden DevOps-organisasjon med governance-fokus. |
| **Klar informasjonsarkitektur** | Bruk av emoji-ankere og tydelig hierarki (H2/H3) gir rask oversikt. |
| **Minimalt internt språk** | Teksten skal være forståelig også for eksterne som bruker workflowene. |
| **Kort, men komplett** | README skal forklare *hva repoet gjør*, *hvordan det brukes*, og *hvilke policyer det håndhever*. |
| **Universell i 2025-standard** | Bruker badges, tabeller og quick-start-seksjon — dagens standard på GitHub. |

---

## 🧱 Struktur og innhold

### 1. Badges øverst

Viser status, lisens og organisasjonspolicy for å bygge tillit og synlighet i GitHub-søk.

```md
[![Org Policy](https://img.shields.io/badge/org--policy-enforced-blue?style=flat-square)](...)
[![CI Status](https://github.com/NORSAIN-AI/.github/actions/workflows/ci-reusable.yml/badge.svg)](...)
[![License](https://img.shields.io/github/license/NORSAIN-AI/.github?style=flat-square)](...)
```

> **Tips:** Bytt ut eller utvid badges etter hvert som dere får:
>
> * Coverage (Codecov, SonarCloud)
> * Security scan (Dependabot, Trivy)
> * Discussion/forum-link hvis dere åpner community-støtte

---

### 2. Innholdsfortegnelse (TOC)

Gir enkel navigasjon og brukes av GitHub til å generere “On this page”-meny automatisk.

* Bruk H2-seksjoner (`##`) med emoji-prefiks for lesbarhet.
* TOC oppdateres manuelt hvis du legger til/fjerner hovedseksjoner.

---

### 3. Quick-start-seksjon

Kritisk for **andre repoer** som bruker `.github` som kilde.
Eksemplet viser hvordan man kobler sitt prosjekt til reusable CI-workflow.

* Kort og kopierbar kodeblokk (YAML + CLI)
* Viser faktisk arbeidsflyt (git commit → push → CI-validation)

---

### 4. Copilot-instruksjoner

README lenker direkte til `copilot-instructions.md`, men gjentar ikke hele innholdet.
Dette følger prinsippet om **single source of truth** — policyen skal vedlikeholdes ett sted.

---

### 5. Policy & Governance

Egen seksjon som minner eksterne (og interne) om at `.github` ikke er et "åpent sandbox-repo" — men et styringsrepo.
Dette er viktig for DevSecOps-rollen og gir tydelig autoritet.

---

## 🧭 Kommentarer til designvalg

| Punkt                      | Begrunnelse                                                                                  |
| -------------------------- | -------------------------------------------------------------------------------------------- |
| **Badges**                 | Viser status og lisens på et øyeblikk – en moderne standard i 2025.                          |
| **TOC med emoji-anker**    | Kombinerer navigasjon og lesbarhet. Brukes i mange topp-prosjekter (Next.js, Supabase, etc). |
| **Quick-start-kodeblokk**  | Reduserer onboarding-tid og minimerer feil ved integrasjon.                                  |
| **Kortversjoner i tabell** | Tabell gir rask oversikt over repoets filer og funksjon.                                     |
| **Policy-seksjon**         | Reflekterer DevSecOps-ansvar og tydeliggjør at endringer må godkjennes.                      |

---

## 🛠 Vedlikehold og revisjon

| Oppgave                                       | Hyppighet                     | Ansvarlig      |
| --------------------------------------------- | ----------------------------- | -------------- |
| Verifiser lenker og badges                    | Kvartalsvis                   | Platform-team  |
| Oppdater eksempler og Quick-start             | Når CI endres                 | DevOps         |
| Revider Copilot-policy-lenke                  | Ved større AI-policyendringer | AI/ML-team     |
| Synkroniser README mellom org og interne docs | Årlig                         | Docs-ansvarlig |

---

## 🔒 Intern bruk og bidrag

Dette dokumentet skal **ikke** vises i offentlig README, men bevares som referanse i repoet:

```text
docs/README-DESIGN.md
```

Endringer i denne filen bør følge commit-typen:

```text
docs(readme-design): oppdatert begrunnelse for badges og policy
```

---

### 📜 Lisens og opphavsrett

Dette dokumentet inngår under samme lisens som repoet ([LICENSE](../LICENSE)).

© 2025 NORSAIN-AI — Internal Documentation for Maintainers.
