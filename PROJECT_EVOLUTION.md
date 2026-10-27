# Project Evolution — ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic

This file explains **how the project reached V3.1** so that a teammate or AI agent understands why the current design looks the way it does. The historical V2 and V3-draft documents are deliberately **not** copied into this repository. They remain unchanged, with SHA-256 checksums, in the registration package (§6).

**Rule:** history explains the current design; it never overrides it. The current authority is [docs/SPECIFICATION.md](docs/SPECIFICATION.md).

## 1. Timeline

| Stage | Date | What happened | Outcome |
|---|---|---|---|
| Original university concept | before Oct 2026 | Egyptian-Arabic Voice-to-SQL for business analytics over a realistic retail database: ASR, schema-aware LLM, SQL guard, charts and evaluation | Voice, real query execution and evaluation are permanent requirements |
| **V2** research refinement | 20–21 Oct 2026 | Natural-language querying already exists in competing products, so the team focused on **silent semantic errors** in business questions. Three improvements were defined: **Business Intent Representation (BIR)**, **ambiguity detection with clarification**, and **selective answering (Answer / Clarify / Abstain)**. Retail-only MVP with modules M1–M8 and the primary **P2-vs-P4** comparison | The research core that V3.1 still carries. Committee feedback said the original V2 idea was suitable to submit |
| **V3 draft** | 22 Oct 2026 | The TA accepted a **multi-department Central Hub** direction and requested **AI-assisted schema design from incomplete requirements under Admin supervision**. Added M9 (Schema Design + Admin Review) and M10 (department-aware registry), the SRR contract, the S0/S1/S2 schema track and authorization tests. Proposed a two-department demo (Sales + Inventory) | Platform vision broadened without dropping BIR, voice or read-only safety |
| **V3.1 team scope freeze** | 22 Oct 2026 | A professor advised building feasible extensions instead of leaving them as future work. The team made **Sales, Inventory and HR** all **mandatory functioning workspaces** (HR on synthetic-only data, a real third domain, not a full HR system). The user supplied a style reference for the high-level overview; a Figma Make prompt was written | Current scope baseline (D-01–D-13) |
| Diagram and dataset approvals | 22 Oct 2026 | Team approved **System Overview v6** (D-14). Dataset strategy **DS-1–DS-8** approved: one seeded synthetic three-department company is primary; 400-item Sales benchmark (375 semantic + 25 security); 192 core recordings; 30–60 schema briefs; corrected metric definitions with a separate Security suite (D-15–D-17) | Data and evaluation plan fixed as targets |
| Supervisor approval and dataset links | 23 Oct 2026 | Academic supervisor approved v6; Field 5 got verified dataset links and licenses (D-18); final wording of Fields 1–4 approved (D-19) | — |
| **Final registration synchronization** | 23 Oct 2026 | The TA clarified the pipeline: voice → speech-to-text → Arabic transcript → **Arabic-to-English translation → English-to-SQL** → guarded execution. The team kept BIR, ambiguity detection and the decision **on the original Arabic, before any SQL**; translation became derived, ambiguity-preserving and audited (D-22). Public Text-to-SQL references by stage (DS-11: Spider, BIRD Mini-Dev, Gretel, AraSpider; Casablanca for ASR) (D-23). P2/P4 receive identical ASR and cached translations; P3 redefined as an optional English-only ablation; translation and semantic-vs-SQL error metrics added (D-24) | Pipeline, dataset roles and evaluation synchronized |
| Abstract, title and Fields 4–5 finalized | 23 Oct 2026 | TA-approved short Abstract inserted verbatim and confirmed final by the student (D-26, D-27). Title: the student kept *Voice-to-SQL in Egyptian Arabic* (D-28) and the **TA approved it** (D-29). Fields 4–5 confirmed after the AraSpider licensing correction (D-30) | **All six registration fields final; form NOT submitted** |
| Final export and independent audit | 23 Oct 2026 | Final registration ZIP exported (33 tracked files + manifest, all verified) together with `FINAL_FORM_COPY_PASTE.md`; independent final package audit completed | Basis of this repository |
| Clean V3.1 repository (this repo) | 23 Oct 2026 | Phase 1: local staging of a V3.1-only repository whose canonical documents embed the approved package text with SHA-256 provenance | No Git repository, commit, remote or push |
| Repository corrections (D-31) | 23 Oct 2026 | Phase 1.5: stale status wording and references to files outside the repository corrected in the repository copies (marked as amended derivatives; original hashes kept); the registration package itself is unchanged | No change to scope, title, Abstract, v6, architecture or evaluation methodology |
| Private GitHub repository (D-32) | 23 Oct 2026 | Phase 2: after an independent review approved the D-31 staging ZIP, Git was initialized on `main`, the approved files were committed and pushed to the new **private** repository `Amr-Heibaa/voice-to-sql-egyptian-arabic`; visibility and file tree verified | No change to project content; registration NOT SUBMITTED |
| Official title update (D-33) | 24 Oct 2026 | The TA explicitly approved the new official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* (as reported by the student); Form Field 1 and all current documents updated; earlier titles kept as history | Abstract, Fields 2–6, scope, datasets, evaluation and v6 unchanged; repository name unchanged; registration NOT SUBMITTED |
| Collaborator status recorded (D-34) | 24 Oct 2026 | Live GitHub state documented: 3 active write collaborators and 1 pending invitation, all invited from the owner account after the D-32 verification; D-32 kept as history | No GitHub changes made by Claude; registration NOT SUBMITTED |
| Branch protection and team workflow (D-35) | 24 Oct 2026 | Protection configured on `main` (pull request with 1 approval by someone other than the author, stale approvals dismissed, conversations resolved, no force push or deletion, no admin bypass) and read back through the GitHub API; team workflow and pull request template added | Enforcement not yet tested; no collaborator changes; registration NOT SUBMITTED |
| Public repository (D-36) | 24 Oct 2026 | After a public-release audit of all files and the full history, the existing repository was changed from **private** to **public** with the owner's authorization; Git history preserved; branch protection re-read and unchanged | No content, history or collaborator changes; D-32, D-34 and D-35 kept as history; registration NOT SUBMITTED |
| Proposal Sprint 0 planning (D-37) | 25 Oct 2026 | The owner confirmed submission of the registration form (committee acceptance not confirmed). In the existing Jira project ClearQuery (`SCRUM`), the active `SCRUM Sprint 0` was organised for the proposal paper: one Epic, 18 tasks with self-contained execution packages, 5 QA review subtasks and 38 dependency links. Planning documents were added under `docs/proposal/` | No scope, design, title, Abstract or v6 change; implementation NOT STARTED; no literature search performed yet |
| Sprint 0 re-planned in Jira `CQP` (D-38) | 25 Oct 2026 | The owner replaced the D-37 `SCRUM` plan with a Business / Project Management Jira project `CQP`: Workstream `CQP-1` covering the three Proposal Discussion deliverables (Proposal Document, 15-slide English Presentation, 10% PoC), 25 tasks, 5 independent QA sub-tasks and 18 hard dependencies. The repository gained a team onboarding path, a Sprint 0 index, presentation and PoC guides and a draft PoC interface contract | No scope, title, Abstract, v6 or specification change; nothing implemented; D-37 kept as history |
| Jira tasks aligned with the university template (D-39) | 27 Oct 2026 | At a team member's instruction, the Jira `CQP` descriptions were rewritten so that every Proposal Document task follows the university template and the lecture guide section by section, in the lecture's order of work, with a corpus freeze on 1 Nov. All ready-made AI prompts and estimates in the descriptions were removed from all 31 issues. The repository's Sprint 0 index, onboarding and proposal guides were aligned with Jira | No scope, title, Abstract, v6 or specification change; no issue deleted; owners unchanged; nothing implemented |

## 2. Title history

| Stage | Title | Fate |
|---|---|---|
| V2 | *Voice-to-SQL in Egyptian Arabic with Ambiguity-Aware Selective Answering* | Historical |
| V3 draft (candidate) | *Governed AI Data Hub: Egyptian-Arabic Voice-to-SQL and AI-Assisted Database Schema Design* | Not adopted |
| V3.1 long title (D-19) | *Voice-to-SQL in Egyptian Arabic with Ambiguity-Aware Selective Answering: A Multi-Department AI Data Hub with Admin-Reviewed Schema Design* | The TA asked for a shorter title (D-20); kept in the spec only as the working name |
| Short options A/B (D-20) | *Ambiguity-Aware Egyptian-Arabic Voice-to-SQL for Multi-Department Business Analytics* / *Egyptian-Arabic Voice-to-SQL with Ambiguity-Aware Selective Answering* | Not selected (D-28) |
| D-29 (23 Oct 2026) | *Voice-to-SQL in Egyptian Arabic* | TA approved; the official title until 24 Oct 2026; **superseded by D-33** |
| **Current (D-33, 24 Oct 2026)** | ***ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*** | **TA approved** (as reported by the student). The title does not change the scope |

## 3. Architecture evolution

```text
V2 (retail only):
  voice/text -> ASR -> BIR -> Answer/Clarify/Abstain -> guarded SELECT -> retail results
                        ^ approved retail catalog / schema

V3 draft:
  user -> department-aware Central Hub -> [Analytics (V2 pipeline) | Schema Proposal workflow]
                                               \                 /
                                        governed metadata registry + Admin approval
                                                       |
                                              authorized data context

V3.1 (current):
  one hub, three mandatory workspaces (Sales, Inventory, HR), two modes
  Analytics: voice/text -> confirmed Arabic transcript -> BIR + ambiguity on the Arabic
             -> Answer/Clarify/Abstain -> (Answer only) Arabic->English translation + resolved BIR
             -> English-to-SQL -> guards -> read-only execution
  Schema Design: incomplete brief -> SRR -> proposed schema + assumptions/questions
             -> validators -> Admin approve/revise/reject -> versioned metadata (never DDL)
```

## 4. What changed, and what never changed

**Never changed since V2:** mandatory Egyptian-Arabic **voice** (plus text); BIR; ambiguity detection with one focused clarification; Answer / Clarify / Abstain; read-only, guarded SQL with results computed by the database; the strong context-matched **P2** baseline against the proposed **P4**; research honesty (no invented results, interviews, approvals or novelty claims).

**Added or changed:**

| From | To | Why |
|---|---|---|
| Retail-only single workspace | One Central Hub with **Sales, Inventory and HR** workspaces | TA-approved hub direction; professor advice; team decision (D-01–D-05) |
| No design mode | **AI Schema Design** with versioned **Admin approval**; approval publishes metadata only, never DDL | TA request (C03/C04, D-06) |
| Two-department proposal (V3 draft) | Three mandatory functioning workspaces, HR synthetic-only | Team decision (D-04) |
| Candidate public retail data (Online Retail II, Contoso) as main sources | One **seeded synthetic** three-department company is primary; public data separate and optional | Provenance and consistency (D-08, D-15) |
| Translation only as ablation P3 | Translation is part of every pipeline; derived, audited, never authoritative; P3 redefined | TA-clarified pipeline (D-22, D-24) |
| Generic metric definitions | Semantic-eligible denominators, Unsafe Direct Answer Rate, separate Security suite, translation and semantic-vs-SQL error metrics | Methodological corrections (D-16, D-24) |
| 253-word Abstract | 213-word TA-approved short Abstract, final | TA feedback, student confirmation (D-21, D-26, D-27) |
| Diagram pending a professor reference | v6 approved by team and supervisor | D-11, D-14, D-18 |
| Short title *Voice-to-SQL in Egyptian Arabic* (D-29) | *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* (D-33) | TA approval of a new official title, 24 Oct 2026 |

**Superseded and not carried forward:** the V2 retail-only form text, the V3-draft form and its candidate title, the 253-word Abstract, title options A/B, the Figma Make prompt and the user-supplied style-reference image (historical inputs that produced v6; the reference depicts a different, older project and is never a content source), and the pre-sync package ZIP.

## 5. Decision index

Condensed from `02_CURRENT_SPECIFICATION/V3_TO_V3_1_DECISION_CHANGELOG.md` in the registration package (full text and file-level change records stay there). All are team or academic-advisor decisions recorded as reported by the student; none is a university committee approval.

| ID | Date | Decision |
|---|---|---|
| D-01 | 22 Oct | Sales + Inventory + HR are mandatory functioning MVP workspaces |
| D-02 | 22 Oct | Sales remains the main research domain (P2 vs P4, voice mandatory) |
| D-03 | 22 Oct | Inventory analytics plus the Schema Design → Admin → operator provisioning/load → analytics demo |
| D-04 | 22 Oct | HR is the third mandatory workspace: synthetic headcount/leave data, own metrics, voice/text, isolated permissions; not a full HR system |
| D-05 | 22 Oct | One shared orchestration/BIR/SQL engine with three departmental schemas/catalogs and server-enforced roles |
| D-06 | 22 Oct | Schema Design retained: SRR, suggestions, Admin review, versioning, optional DDL preview; no autonomous production DDL |
| D-07 | 22 Oct | SQL security unchanged: read-only role, AST/allowlist, server authorization; separate operator credentials |
| D-08 | 22 Oct | One explicitly synthetic company for the integrated demo; real retail data, if used, kept separate |
| D-09 | 22 Oct | Evaluation adds HR voice/text acceptance, Inventory/HR ambiguity cases and cross-department denial tests |
| D-10 | 22 Oct | Professor's advice to implement feasible expansion recorded as rationale |
| D-11 | 22 Oct | Style reference supplied; Figma Make prompt delivered (superseded by D-14) |
| D-12 | 22 Oct | Candidate long title; official title pending (superseded by D-29) |
| D-13 | 22 Oct | V2 and V3-draft snapshots preserved unchanged; V3.1 is current |
| D-14 | 22 Oct | Team approved `System-Overview-3840x2160-v6.png` (SHA-256 `62d3743e297e5eba7c0ea0e062643c7f756291777911942b73e1e2bddd280653`) |
| D-15 | 22 Oct | Dataset strategy DS-1–DS-8 approved (synthetic primary company; 400-item benchmark; 192 recordings; 30–60 briefs) |
| D-16 | 22 Oct | Metric corrections: semantic-eligible denominators, separate Security suite, clarification FP rules, unsafe direct answers |
| D-17 | 22 Oct | Documentation synchronization DS-9/DS-10 executed |
| D-18 | 23 Oct | Academic supervisor approved v6; Field 5 restructured with verified links and licenses |
| D-19 | 23 Oct | Final English wording of Fields 1–4 approved |
| D-20 | 23 Oct | TA requested a shorter title; options A/B proposed (superseded by D-28/D-29) |
| D-21 | 23 Oct | TA approved the revised short Abstract; exact text awaited (resolved by D-26) |
| D-22 | 23 Oct | TA-clarified pipeline with translation + English-to-SQL; BIR, ambiguity and decision stay on the Arabic, before SQL |
| D-23 | 23 Oct | DS-11: public Text-to-SQL references by pipeline stage; custom benchmark stays primary |
| D-24 | 23 Oct | Matched ASR/translation inputs for P2/P4; P3 redefined (Q14); translation and semantic-vs-SQL metrics |
| D-25 | 23 Oct | v6 unchanged; translation not drawn by design (compatibility note; Q15) |
| D-26 | 23 Oct | Exact TA-approved Abstract inserted verbatim (213 words) |
| D-27 | 23 Oct | Student confirmed the Abstract as final; never rewrite it |
| D-28 | 23 Oct | Student kept the short title *Voice-to-SQL in Egyptian Arabic* |
| D-29 | 23 Oct | TA approved *Voice-to-SQL in Egyptian Arabic*; no suffix unless required |
| D-30 | 23 Oct | Fields 4–5 confirmed; AraSpider licensing: HF repository MIT, underlying Spider CC BY-SA 4.0, redistribution uncertain, reference only |
| D-31 | 23 Oct | **Repository only:** clean-repository documentation corrections (stale DS-11 status, V2 form filename, status wording, references to excluded files); 35 exact edits, recorded in [docs/CHANGE_RECORD_D-31.md](docs/CHANGE_RECORD_D-31.md) |

| D-32 | 23 Oct | **Repository only:** private GitHub repository created and initial commit pushed after independent review; recorded in [docs/CHANGE_RECORD_D-32.md](docs/CHANGE_RECORD_D-32.md) |
| D-33 | 24 Oct | TA approved the new official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*; Field 1 and current documents updated; recorded in [docs/CHANGE_RECORD_D-33.md](docs/CHANGE_RECORD_D-33.md) |
| D-34 | 24 Oct | **Repository only:** current GitHub collaborator status recorded (3 active write collaborators, 1 pending invitation); D-32 unchanged as history; [docs/CHANGE_RECORD_D-34.md](docs/CHANGE_RECORD_D-34.md) |
| D-35 | 24 Oct | **Repository only:** branch protection on `main` configured and API-verified (real enforcement test not yet performed); team workflow approved ([CONTRIBUTING.md](CONTRIBUTING.md), pull request template); [docs/CHANGE_RECORD_D-35.md](docs/CHANGE_RECORD_D-35.md) |
| D-36 | 24 Oct | **Repository only:** visibility changed from private to public after a public-release audit, authorized by the owner; history preserved; protection unchanged; [docs/CHANGE_RECORD_D-36.md](docs/CHANGE_RECORD_D-36.md) |
| D-37 | 25 Oct | Registration-form submission confirmed by the owner (status only; committee acceptance pending, Q12). **Repository and Jira:** proposal Sprint 0 planning (Epic `SCRUM-5`, tasks `SCRUM-6`–`SCRUM-23`, QA subtasks `SCRUM-24`–`SCRUM-28`) and `docs/proposal/`; [docs/CHANGE_RECORD_D-37.md](docs/CHANGE_RECORD_D-37.md) |

| D-38 | 25 Oct | **Repository and planning:** the Jira Business project `CQP` (Workstream `CQP-1`, tasks `CQP-2`–`CQP-26`, QA sub-tasks `CQP-27`–`CQP-31`) replaces the D-37 `SCRUM` plan for current Sprint 0 coordination; the three Proposal Discussion deliverables, team onboarding, presentation and PoC guides and a draft PoC interface contract added; [docs/CHANGE_RECORD_D-38.md](docs/CHANGE_RECORD_D-38.md) |
| D-39 | 27 Oct | **Jira and repository:** Jira `CQP` task descriptions aligned with the university template and the lecture guide (order of work, corpus freeze on 1 Nov, new targets); AI prompts removed from all 31 issues; Sprint 0 index, onboarding and proposal guides aligned; [docs/CHANGE_RECORD_D-39.md](docs/CHANGE_RECORD_D-39.md) |

New decisions continue from **D-40** (see [AGENTS.md](AGENTS.md#5-change-protocol)).

## 6. Where the history lives (not in this repository)

| Archive | Location in the registration package | Status |
|---|---|---|
| V2 frozen baseline (handover, form, starter prompt) | `01_READ_ONLY_V2_BASELINE/` | Read-only, hash-verified |
| V3 draft frozen baseline (spec, form, change log, guides) | `01B_READ_ONLY_V3_DRAFT_BASELINE/` | Read-only, hash-verified |
| Full V3 → V3.1 decision change log | `02_CURRENT_SPECIFICATION/V3_TO_V3_1_DECISION_CHANGELOG.md` | Current, not copied |
| Dataset research and verification logs | `06_RESEARCH_AND_DATA/` | Current research records, not copied |
| Pre-sync backups | outside the package (`MIU_VoiceToSQL_V3_1_Backups/`) | Not part of any repository |

Package: `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip`, manifest SHA-256 `a5976cd1e639a2cff3a1e1a45c3e9208b275a411485bf2c0da9cb65d9d858684`.
