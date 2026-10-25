# Project Status — ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic

**As of:** 25 October 2026 · **Baseline:** V3.1 team-approved planning baseline · **Source package:** `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip` (manifest SHA-256 `a5976cd1e639a2cff3a1e1a45c3e9208b275a411485bf2c0da9cb65d9d858684`; 33/33 files verified)

This is the **live status file**. Status lines inside the document blocks of `docs/` are dated snapshots from 22–24 October 2026; when this file and a snapshot differ, this file is current for **status**, and `docs/SPECIFICATION.md` stays the source of truth for **scope and design**. Repository amendment **D-31** (23 Oct 2026) corrected stale references and status wording in those blocks without changing scope or design ([docs/CHANGE_RECORD_D-31.md](docs/CHANGE_RECORD_D-31.md)), and amendment **D-33** (24 Oct 2026) recorded the TA-approved official title ([docs/CHANGE_RECORD_D-33.md](docs/CHANGE_RECORD_D-33.md)).

## 1. Status summary

| Area | Status | Notes |
|---|---|---|
| Official title: *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* | **TA APPROVED** | D-33 (recorded 24 Oct 2026, as reported by the student); exact wording, no suffix unless the university requires one; replaces *Voice-to-SQL in Egyptian Arabic* (D-29, 23 Oct 2026), kept as history |
| Abstract | **STUDENT-CONFIRMED FINAL** | 213 words; D-26/D-27; never rewrite it |
| Six registration form fields | **FINALIZED** | All six fields are final (§2) |
| University registration form | **SUBMITTED (25 Oct 2026)** | Submitted personally by the student; confirmed by the owner on 25 Oct 2026 (D-37). Submission is not acceptance: formal committee acceptance of the expanded scope is still pending (Q12) |
| Formal committee approval of the expanded V3.1 scope | **NOT OBTAINED** | Open decision Q12; TA, professor and supervisor support is not committee registration |
| Implementation (code, database, UI, models) | **NOT STARTED** | No codebase, no deployment, no stack or model selected (Q09). A minimal Proof of Concept is **planned** in Sprint 0 (`CQP-22`–`CQP-26`); it is **not implemented** and its scope is an internal proposal pending supervisor confirmation ([docs/poc/POC_KICKOFF.md](docs/poc/POC_KICKOFF.md)) |
| Custom datasets (synthetic company, benchmark, annotations, gold SQL) | **PLANNED, NOT COLLECTED** | Dataset generation has not started |
| Voice recordings | **PLANNED, NOT COLLECTED** | Consent protocol and any required ethics review must come first |
| Evaluation | **NOT STARTED** | No results of any kind exist |
| User interviews / validation studies | **NOT STARTED** | Market need is an unverified hypothesis (H-M) |
| Sprint 0 — Proposal Discussion readiness | **PLANNED IN JIRA `CQP`; NOT STARTED** (D-38, 25 Oct 2026) | Current and authoritative: Jira project **ClearQuery - Graduation Project** (`CQP`, Business / Project Management), Workstream `CQP-1`, 25 tasks (`CQP-2`–`CQP-26`), 5 QA sub-tasks (`CQP-27`–`CQP-31`), 18 Blocks links, all To Do (read-only check, 25 Oct 2026). Three required deliverables: Proposal Document, 15-slide English Presentation, 10% PoC; none completed. The Proposal Discussion period starts on 10 Nov 2026. Index: [docs/SPRINT_0.md](docs/SPRINT_0.md) |
| Previous proposal plan (D-37) | **SUPERSEDED** (D-38) | The old Jira project `SCRUM` (Epic `SCRUM-5`, 18 tasks, 5 QA subtasks, 38 links) is no longer authoritative for current planning; [docs/CHANGE_RECORD_D-37.md](docs/CHANGE_RECORD_D-37.md) stays as history |
| Shared private workspace | **DECIDED: University Drive; SETUP PENDING** | Decided by the owner on 25 Oct 2026. The folder and its access settings are not yet created; no link is published here |
| GitHub repository | **PUBLIC (D-36, 24 Oct 2026)** | https://github.com/Amr-Heibaa/voice-to-sql-egyptian-arabic; visibility `PUBLIC` since 24 Oct 2026 (about 16:48 UTC), changed by the owner's authorization after a public-release audit, Git history preserved ([docs/CHANGE_RECORD_D-36.md](docs/CHANGE_RECORD_D-36.md)). Created **private** on 23 Oct 2026 (D-32); branch `main`; initial commit `c05bd5a` ([docs/CHANGE_RECORD_D-32.md](docs/CHANGE_RECORD_D-32.md)); repository name unchanged by the D-33 title update |
| GitHub collaborators | **4 ACTIVE (write)** (read 25 Oct 2026, D-37; re-read unchanged for D-38) | Owner `Amr-Heibaa` (admin). Active with write access: `sayeddabdou`, `selimmmm7`, `abdallahjr111`, `GeorgeBassem-dev`. The invitation to `GeorgeBassem-dev` recorded as pending in D-34 has since been accepted; there are no pending invitations. All invitations were sent from the owner account ([docs/CHANGE_RECORD_D-34.md](docs/CHANGE_RECORD_D-34.md)) |
| Branch protection on `main` | **CONFIGURED, API-VERIFIED (D-35, 24 Oct 2026); enforcement NOT YET TESTED** | Pull request required; 1 approval from someone other than the author; stale approvals dismissed; conversations must be resolved; force pushes and deletion blocked; applies to administrators while configured (no bypass allowances; an administrator can still change the settings); no CI checks required yet. Settings read back through the GitHub REST and GraphQL APIs; no push to `main` has been attempted, so a real enforcement test has **not** been performed ([docs/CHANGE_RECORD_D-35.md](docs/CHANGE_RECORD_D-35.md)). Re-read after the change to public on 24 Oct 2026: unchanged ([docs/CHANGE_RECORD_D-36.md](docs/CHANGE_RECORD_D-36.md)) |
| Team workflow | **APPROVED (D-35, 24 Oct 2026)** | Feature branch → pull request → human code review → merge; rules for AI coding agents ([CONTRIBUTING.md](CONTRIBUTING.md)) |
| License | **NONE** | No LICENSE file; no open-source or other separate license adopted; licensing and ownership undecided. Public visibility (D-36) is not a license: GitHub's Terms of Service give GitHub users limited permissions through the service (for example, viewing and forking on GitHub), but the project grants no additional right to reuse, copy, modify or redistribute the materials |

**Fixed V3.1 scope (unchanged):** one AI Central Hub with **three mandatory workspaces: Sales, Inventory and HR**; ambiguity-aware selective answering (BIR, Answer / Clarify / Abstain); **Egyptian-Arabic Voice → Arabic Text → English Text → English-to-SQL, with Arabic-anchored ambiguity checking**; safe read-only SQL; **AI Schema Design with Admin review** (approval publishes metadata only, never DDL).

## 2. Registration form fields

| Field | Status | Approval and limits |
|---|---|---|
| 1. Project Title: *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* | Final | **TA approved** (recorded 24 Oct 2026, as reported by the student; D-33). Replaces the title TA-approved on 23 Oct 2026, *Voice-to-SQL in Egyptian Arabic* (D-29). No category suffix unless the university separately requires it. The title does not change the V3.1 scope |
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
| Title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* | TA (recorded 24 Oct 2026, as reported by the student; D-33) | Not committee approval of the scope. The earlier title *Voice-to-SQL in Egyptian Arabic* (TA-approved 23 Oct, D-29) is superseded |
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

**Sprint 0 open decisions (D-38)**

| ID | Open item | Current position |
|---|---|---|
| S0-D1 | Where PoC source code lives: this public repository or a separate private repository | **Open, owner decision.** `CQP-1` plans a private code repository; no repository has been created. Code is published here only with the owner's explicit approval |
| S0-D2 | Supervisor confirmation of the proposed PoC scope (the university gives no "10%" checklist) | Pending (`CQP-22` Phase A) |
| S0-D3 | PoC Interface Contract v1.0 | Draft only; frozen at Gate G-A (28 Oct 2026) by four owner comments on `CQP-22` |
| S0-D4 | PoC stack, ASR, translation and LLM choices | Not selected (Q09); decided at or after Gate G-A |
| S0-D5 | GitHub handles of Sayed and George | `sayeddabdou` and `GeorgeBassem-dev` are active collaborators, but their mapping to the members is not yet confirmed by the owner |
| S0-D6 | University Drive folder and access settings | Pending (Amr) |
| S0-D7 | Publishing direct Jira links in this public repository | Not approved; issue keys only |

Other pending items: ethics/consent review for recordings; optional permission requests (MGB-3, ArzEn, RSchema authors); AceMB unconfirmed until its gated content is inspected.

## 5. Next steps

1. **Registration form:** done; submitted on 25 Oct 2026 (owner-confirmed, D-37). Committee acceptance of the expanded scope is awaited. **Sprint 0:** deliver the Proposal Document, the 15-slide English Presentation and the minimal PoC before the Proposal Discussion period that starts on 10 Nov 2026 ([docs/SPRINT_0.md](docs/SPRINT_0.md)). Internal checkpoints (targets, not university deadlines):
   - 26–28 Oct: RQs, SLR protocol, extraction/quality and screening frameworks, PoC scope and Interface Contract.
   - **28 Oct:** proposed PoC contract Gate G-A.
   - **1 Nov:** text-only walking skeleton (Checkpoint C1).
   - 4–7 Nov: PoC component integration and academic drafting.
   - **8 Nov:** internal completion target.
   - 9 Nov: rehearsal and contingency checks.
   - **10 Nov:** the university Proposal Discussion period begins.
2. **Repository:** done. The GitHub repository was created as private and pushed after independent review (D-32), and made public on 24 Oct 2026 after a public-release audit (D-36). Collaborators are managed by the owner; the current state is recorded in D-34. Since D-35, `main` is protected: every change goes through a pull request approved by someone other than its author ([CONTRIBUTING.md](CONTRIBUTING.md)). A controlled enforcement test is still open, and the GitHub repository description still uses the earlier title (D-36 open items).
3. **Implementation:** the full application does not start until separately authorized. The Sprint 0 PoC components (`CQP-23`–`CQP-26`) follow Gate G-A and the owner's decision on where the code lives (S0-D1). The planned sequence is SPECIFICATION.md §20 (Phase 1: repo architecture, PostgreSQL demo schema, read-only privilege tests before any LLM is connected).

## 6. Update rule

When a status changes (for example, the form is submitted), update this file with the date, the change and who confirmed it, and add a dated entry to [PROJECT_EVOLUTION.md](PROJECT_EVOLUTION.md#5-decision-index). Never mark anything submitted, approved, implemented, collected or measured without the user's explicit confirmation.
