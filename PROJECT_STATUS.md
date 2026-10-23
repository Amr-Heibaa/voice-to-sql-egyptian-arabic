# Project Status — Voice-to-SQL in Egyptian Arabic

**As of:** 23 October 2026 · **Baseline:** V3.1 team-approved planning baseline · **Source package:** `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip` (manifest SHA-256 `a5976cd1e639a2cff3a1e1a45c3e9208b275a411485bf2c0da9cb65d9d858684`; 33/33 files verified)

This is the **live status file**. Status lines inside the document blocks of `docs/` are dated snapshots from 22–23 October 2026; when this file and a snapshot differ, this file is current for **status**, and `docs/SPECIFICATION.md` stays the source of truth for **scope and design**. Repository amendment **D-31** (23 Oct 2026) corrected stale references and status wording in those blocks without changing scope or design ([docs/CHANGE_RECORD_D-31.md](docs/CHANGE_RECORD_D-31.md)).

## 1. Status summary

| Area | Status | Notes |
|---|---|---|
| Official title: *Voice-to-SQL in Egyptian Arabic* | **TA APPROVED** | D-29; exact wording, no suffix unless the university requires one |
| Abstract | **STUDENT-CONFIRMED FINAL** | 213 words; D-26/D-27; never rewrite it |
| Six registration form fields | **FINALIZED** | All six fields are final (§2) |
| University registration | **NOT SUBMITTED** | The student fills and submits the form personally |
| Formal committee approval of the expanded V3.1 scope | **NOT OBTAINED** | Open decision Q12; TA, professor and supervisor support is not committee registration |
| Implementation (code, database, UI, models) | **NOT STARTED** | No codebase, no deployment, no stack or model selected (Q09) |
| Custom datasets (synthetic company, benchmark, annotations, gold SQL) | **PLANNED, NOT COLLECTED** | Dataset generation has not started |
| Voice recordings | **PLANNED, NOT COLLECTED** | Consent protocol and any required ethics review must come first |
| Evaluation | **NOT STARTED** | No results of any kind exist |
| User interviews / validation studies | **NOT STARTED** | Market need is an unverified hypothesis (H-M) |
| GitHub repository | **LOCAL STAGING ONLY (Phase 1.5)** | Name `voice-to-sql-egyptian-arabic`; intended visibility **private**; no Git repository initialized, no commit, no remote, no push; Phase 2 needs explicit authorization |
| License | **NONE** | No LICENSE file; licensing and ownership undecided; no rights granted |

**Fixed V3.1 scope (unchanged):** one AI Central Hub with **three mandatory workspaces: Sales, Inventory and HR**; ambiguity-aware selective answering (BIR, Answer / Clarify / Abstain); **Egyptian-Arabic Voice → Arabic Text → English Text → English-to-SQL, with Arabic-anchored ambiguity checking**; safe read-only SQL; **AI Schema Design with Admin review** (approval publishes metadata only, never DDL).

## 2. Registration form fields

| Field | Status | Approval and limits |
|---|---|---|
| 1. Project Title: *Voice-to-SQL in Egyptian Arabic* | Final | **TA approved** (23 Oct 2026, confirmed by the student; D-29). No "(Company Ideas – IBM)" suffix unless the university separately requires it. The short title does not narrow the V3.1 scope |
| 2. Project Description (Abstract) | Final | 213 words; TA approved the revised short Abstract (as reported by the student); exact text **confirmed final by the student** (D-26/D-27). Never rewrite it |
| 3. Project Scope | Final | Team-approved wording |
| 4. AI Application | Final | Student-confirmed (D-30); 357 words / 2,563 characters |
| 5. Dataset | Final | Student-confirmed after the AraSpider licensing correction (D-30); 581 words / 4,452 characters |
| 6. System Overview Diagram | Final | `assets/System-Overview-3840x2160-v6.png`, **team- and academic-supervisor-approved**; not committee-approved |

Exact text: [docs/REGISTRATION_FORM_FIELDS.md](docs/REGISTRATION_FORM_FIELDS.md).

**Practical checks left for the student when filling the live form:** actual input limits (Field 5 is the longest; any shortening needs the student's approval first), Arabic-script support, where the title and category are entered, and re-opening the dataset links once.

## 3. What is approved, and what each approval does not mean

| Item | Approved by | Not |
|---|---|---|
| V3.1 scope (one hub; Sales, Inventory and HR mandatory; Schema Design with Admin approval; read-only SQL; no automatic DDL) | Project team (22 Oct 2026); TA and professor supportive in conversation | Not formal committee approval |
| System Overview v6 | Project team (22 Oct) + academic supervisor (recorded 23 Oct) | Not committee approval of the expanded scope |
| Title *Voice-to-SQL in Egyptian Arabic* | TA (23 Oct, as confirmed by the student) | Not committee approval of the scope |
| Short Abstract | TA (as reported by the student) + student confirmation of the exact text | — |
| Fields 4–5 wording | Student (23 Oct) | The TA's positive reply on the dataset evidence is support for the evidence, not approval of the exact wording |
| TA-clarified pipeline (translation + English-to-SQL) | TA clarification (23 Oct) | The contribution-preserving processing order (SPECIFICATION.md §8.1) is the team's documentation of it |
| Dataset strategy DS-1–DS-8 (DS-11 synchronized) | Project team | Planning decisions only; nothing collected |

## 4. Open decisions (from SPECIFICATION.md §22)

| ID | Open item | Current position |
|---|---|---|
| Q06 | Does Schema Design mode need voice? | Text mandatory; voice optional, pending |
| Q07 | Meaning of the TA's earlier "SQL aspect" remark | May be covered by the English-to-SQL clarification; not confirmed; no new feature added |
| Q08 | Exact Inventory/HR/schema evaluation counts | Targets only (≈60 typed + 24 recordings per workspace; 30–60 briefs) |
| Q09 | Models, libraries, hosting, API contracts | Not selected; choose after a small spike and security design |
| Q10 | Final business metrics and data-generation scheme | Needs domain review |
| Q11 | Admin vs developer permissions; audit retention | Freeze the threat model before coding |
| Q12 | Formal committee approval of the expanded scope | Pending |
| Q14 | P3 redefined as an English-only translation ablation | Optional; team confirmation pending |
| Q15 | Should translation appear in the diagram? | Only if the TA or supervisor asks; never edit v6 without new supervisor approval |

Other pending items: ethics/consent review for recordings; optional permission requests (MGB-3, ArzEn, RSchema authors); AceMB unconfirmed until its gated content is inspected.

## 5. Next steps

1. **Student:** fill and personally submit the official MIU registration form using [docs/REGISTRATION_FORM_FIELDS.md](docs/REGISTRATION_FORM_FIELDS.md) and the v6 image.
2. **Repository Phase 2 (needs explicit authorization):** after the independent review of this staging, initialize Git, make the first commit, create the **private** GitHub repository `voice-to-sql-egyptian-arabic` and push this staged content.
3. **Implementation:** does not start until separately authorized. The planned sequence is SPECIFICATION.md §20 (Phase 1: repo architecture, PostgreSQL demo schema, read-only privilege tests before any LLM is connected).

## 6. Update rule

When a status changes (for example, the form is submitted), update this file with the date, the change and who confirmed it, and add a dated entry to [PROJECT_EVOLUTION.md](PROJECT_EVOLUTION.md#5-decision-index). Never mark anything submitted, approved, implemented, collected or measured without the user's explicit confirmation.
