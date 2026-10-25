# Proof of Concept Kickoff — Sprint 0 (10% Implementation)

Deliverable 3 of 3 ([../SPRINT_0.md](../SPRINT_0.md)). Jira: `CQP-22` … `CQP-26`.

> **Status (25 Oct 2026): NOT IMPLEMENTED.** No PoC code, database, model integration or test exists. This page is planning documentation.
>
> **Scope status: internal engineering proposal, pending supervisor confirmation.** The university requires "a minimal working prototype demonstrating the core idea" but gives no feature checklist and no formula for "10%". The boundary below is the team's recommendation (RTM item R-01 in `CQP-1`), not an official university checklist.

## 1. Goal

Show the committee, live and honestly, the core ClearQuery idea on a small **synthetic Sales** database: an Egyptian-Arabic question is understood as a business intent, the system decides **Answer / Clarify / Abstain** before any SQL, and only an Answer runs guarded, read-only SQL whose numbers come from the database.

## 2. Proposed flow (Sales only, synthetic data)

```text
Egyptian-Arabic voice or typed text
  -> ASR (voice only) -> editable Arabic transcript, confirmed by the user  (q_ar, authoritative)
  -> Arabic-to-English translation (q_en, derived; q_ar is kept unchanged)
  -> minimal BIR from q_ar + mini Sales semantic catalog
  -> deterministic decision: ANSWER | CLARIFY (one turn, no SQL) | ABSTAIN (no SQL)
  -> ANSWER only: English Text-to-SQL from q_en + resolved BIR (BIR wins on conflict)
  -> SQL guard: single SELECT, allow-listed views, no DDL/DML, no multi-statements
  -> execution with a read-only database role on the seeded synthetic Sales DB
  -> database-grounded answer: real rows, the executed SQL, the interpreted intent
```

This is a thin slice of the canonical pipeline in [../SPECIFICATION.md](../SPECIFICATION.md) §8.1. It does not change that design. In particular, the BIR and the decision are computed from the **Arabic** (`q_ar`), never from the translation.

## 3. Minimum intended capabilities (proposed MoSCoW)

| Level | Capability |
|---|---|
| MUST | Typed Egyptian-Arabic input for scenarios A, B and C through real BIR and policy processing |
| MUST | Voice input with **actual ASR** and an **editable** transcript, at least for scenarios A and B; typed input is the fallback |
| MUST | An Arabic-to-English translation stage in the pipeline, with the original Arabic preserved for the BIR |
| MUST | Minimal BIR and a mini Sales semantic catalog |
| MUST | One-turn clarification that continues to a database-grounded answer (scenario B) |
| MUST | Truthful abstention with no figure produced (scenario C) |
| MUST | Read-only SQL validation and execution on a small seeded synthetic Sales database; the executed SQL and the real rows are visible |
| MUST | Safety in two layers (§5) |
| SHOULD | Web UI (`CQP-25`); if it is late, a command-line or notebook driver of the **same real backend** |
| SHOULD | Voice for scenario C; a trace panel showing intermediate outputs |
| COULD | Arabic-language answer text; extra paraphrases; an HR access-denied demonstration beyond the negative test |
| WON'T (Sprint 0) | Full Inventory or HR analytics, the AI Schema Design module, benchmark evaluation (P2 vs P4), fine-tuning, deployment |

Inventory, HR and AI Schema Design stay **mandatory parts of the V3.1 graduation scope**; they are only outside this PoC milestone.

## 4. Demonstration scenarios (proposed)

| ID | Input (Egyptian Arabic, typed; voice for A and B) | Expected decision | Expected database effect |
|---|---|---|---|
| A | A clear question such as total sales in September 2026 | **ANSWER** | One validated SELECT; real rows shown |
| B | An ambiguous question such as "مين أحسن فرع؟" ("Which is the best branch?"), where "best" could mean revenue or transaction count | **CLARIFY**, then ANSWER after the user chooses | No SQL until the choice; then one validated SELECT |
| C | An unanswerable question such as "صافي الربح كام؟" ("What is the net profit?"), when the synthetic data has no cost or expense data | **ABSTAIN** with a specific reason | No SQL executed; no figure produced |

The exact wording, catalog entries and expected rows are fixed in the PoC scope document in `CQP-22` Phase A. Expected values must be computed from the seeded database, never written by hand.

## 5. Safety and fail-closed behavior

1. **Before SQL (intent policy):** a write-oriented request such as "امسح مبيعات سبتمبر" ("delete September's sales") is refused by the policy. No SQL is generated.
2. **In the execution guard:** crafted write or DDL SQL (for example `DELETE`, `UPDATE`, `DROP`, multi-statement input) sent directly to the guard is rejected before execution, and table row counts are unchanged.
3. **Read-only role:** the database user used for execution has no write privileges, so the database itself refuses a write even if the guard were bypassed.
4. **Fail closed:** any component error, timeout, schema-validation failure or guard rejection ends in ABSTAIN or a visible error. It never produces a guessed answer.
5. **Order of trust:** the guard and the read-only role are tested **before** any model is connected to the database ([../ARCHITECTURE.md](../ARCHITECTURE.md) rule R5).

## 6. Integrity rules

- No fake demonstrations: no hard-coded answers, no simulated AI decisions presented as model output, no invented database results.
- Stubs are allowed only during development and are never part of the final demo.
- No automatic DDL. The PoC never creates or alters tables from model output; the seed database is created by a reviewed script run by a human.
- Synthetic data only. No real personal data and no recordings in Git. Keys and passwords only in environment variables, never in code, slides or documents.
- A backup recording, if used, is a recording of an **actual** run and is always labelled as a recording.

## 7. Component responsibilities

| Jira | Owner | Component | Owns these contract objects |
|---|---|---|---|
| `CQP-22` | Amr | Architecture, Interface Contract, integration, demo readiness (test matrix, runbook, demo script, limitations) | Contract versioning, `trace_id` rules, run configuration, the end-to-end driver |
| `CQP-23` | Sayed | Voice capture, ASR, transcript editing support, Arabic-to-English translation | `AsrResult`, `TranslationResult` |
| `CQP-24` | Abdelrahman | Minimal BIR, mini Sales semantic catalog, ambiguity detection, Answer/Clarify/Abstain policy, clarification state | `Bir`, `Decision`, `ClarificationResponse`, the catalog file |
| `CQP-25` | George | Lightweight interactive interface (input, transcript editing, clarification options, answer and trace display) | UI only; consumes the other objects |
| `CQP-26` | Abdallah | Synthetic Sales schema and seed data, SQL guard, read-only execution, safety tests; SQL expressions for catalog metrics | `SqlRequest`, `SqlResult` |

Draft object definitions: [INTERFACE_CONTRACT_DRAFT.md](INTERFACE_CONTRACT_DRAFT.md).

## 8. Timeline and gates

| Date | Gate or step |
|---|---|
| 26–28 Oct | `CQP-22` Phase A: PoC scope v1 (sent to the supervisor) and Interface Contract v1.0 |
| **28 Oct** | **Gate G-A:** contract frozen when Sayed, Abdelrahman, George and Abdallah each comment "Contract v1.0 agreed" on `CQP-22`. Later changes are versioned notes (v1.1, …) announced to affected owners |
| 29 Oct – 1 Nov | Components built against the contract; exploratory spikes may start before G-A |
| **1 Nov** | **Checkpoint C1:** text-only walking skeleton, CLI or notebook, real components: typed Arabic → minimal BIR/policy → guard → seeded DB → rows for scenario A |
| 4–7 Nov | `CQP-22` Phase B: data/guard + BIR first, then voice/translation, then UI; full test matrix on the presentation laptop; runbook, demo script, contingency |
| 6–8 Nov | Independent clean-start re-run by George (`CQP-30`); SQL-guard safety evidence reviewed by Amr (`CQP-27`) |
| 9 Nov | Rehearsal, venue network test, typed fallback check |

## 9. Decisions to make before implementation

None of these is decided. Record each decision as a comment on `CQP-22`.

| # | Decision | Owner | Note |
|---|---|---|---|
| 1 | Where PoC code lives: this public repository or a separate private repository | Amr | **Open.** `CQP-1` currently plans a private code repository; publishing code here needs the owner's explicit approval |
| 2 | Programming language and frameworks for backend and UI | Team, at G-A | [../SPECIFICATION.md](../SPECIFICATION.md) §17 lists candidates only; none is selected |
| 3 | Database engine and read-only role setup | Abdallah, Amr | PostgreSQL is the specification's candidate; any demo-only substitute must be listed as a limitation |
| 4 | ASR engine (cloud or local) and translation engine | Sayed | Offline capability matters for venue risk |
| 5 | LLM for BIR extraction and Text-to-SQL; deterministic settings | Abdelrahman, Amr | Cost, keys, latency, Arabic support |
| 6 | Transport between components (function calls or local HTTP) | Amr, at G-A | Must carry `trace_id` end to end |
| 7 | Catalog file format and location | Abdelrahman, Abdallah | One file, one owner (`CQP-24`), SQL expressions from `CQP-26` |
| 8 | Confirmation of this PoC scope by the supervisor | Amr | Until confirmed, label it as the team's proposal |
| 9 | Handling of presenters' voice samples used for testing | Sayed, Amr | Consent first; never in Git |

## 10. What "done" means for the PoC

Final acceptance (from `CQP-22`): every MUST item passes with **real** processing on the presentation laptop; every answer comes from an actual database query; neither safety layer lets a write reach the database; the runbook reproduces the demo from a clean start; missing SHOULD/COULD items are listed honestly as limitations. Until that is recorded in Jira, the PoC is **not implemented**.
