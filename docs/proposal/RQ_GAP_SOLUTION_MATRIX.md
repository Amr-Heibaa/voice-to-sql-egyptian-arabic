# RQ → Gap → Solution → Evaluation Traceability Matrix (Template)

> **Optional working aid. No gap has been identified yet.** Since D-39 (27 Oct 2026) the Jira tasks do not require this matrix: `CQP-10` writes the gaps in Section III-D with citations, and `CQP-11` writes the short RQ5 answer (III-E) and the three VI-B lists (From RQ1 and RQ2 / From RQ3 / From RQ4) for `CQP-16`. The team may use the tables below as a scratch aid. The component and evaluation columns restate the fixed V3.1 design ([../SPECIFICATION.md](../SPECIFICATION.md)). They are not results and not novelty claims.

## 1. Gap register (optional)

| Gap ID | Gap statement | RQ4 theme | Type (literature / tool / evaluation / hypothesis) | Supporting sources | Counter-evidence | Evidence strength (Strong / Moderate / Hypothesis) |
|---|---|---|---|---|---|---|
| G1 | *to be derived from evidence* | | | | | |
| G2 | | | | | | |

**Starting hypotheses, not findings.** [../SPECIFICATION.md](../SPECIFICATION.md) §16.2 states provisional gap hypotheses: reliability of Egyptian-Arabic spoken business queries with material ambiguity and ASR uncertainty under controlled baselines; handling of incomplete requirements and reviewer effort in schema design; and an unverified market hypothesis. `CQP-10` must confirm, qualify or reject each one from the reviewed evidence.

## 2. Fixed V3.1 components and their planned evaluation

| Component (V3.1) | Contribution class | Planned evaluation (SPECIFICATION.md §15) | Gap IDs (`CQP-11`) |
|---|---|---|---|
| Arabic-anchored Business Intent Representation (BIR) with an approved semantic catalog | Primary | P4 vs P2: Business-Answer Accuracy, Silent Error Rate, Unsafe Direct Answer Rate | |
| Ambiguity detection on the original Arabic (catalog lexicon + resolvers) | Primary | Clarification precision/recall; Translation Ambiguity-Collapse Rate (diagnostic) | |
| Deterministic Answer / Clarify / Abstain policy before any SQL | Primary | Abstention correctness; selective accuracy and coverage; risk–coverage curves | |
| ASR with an editable, user-confirmed transcript | Supporting | WER/CER, named-entity error, voice-vs-text delta | |
| Ambiguity-preserving Arabic-to-English translation (derived, audited) | Supporting | Meaning and entity preservation; ambiguity preservation (diagnostic) | |
| English question-to-SQL constrained by the resolved BIR | Supporting | SQL Execution Accuracy on fixed snapshots; semantic vs SQL error split | |
| Guards: AST, allowlist, department authorization, BIR↔SQL consistency; read-only execution | Supporting | Security suite; guard tests | |
| Three separately authorized workspaces (Sales, Inventory, HR) | Supporting | Hub integration and deny-by-default tests (§15.4) | |
| AI-assisted schema design with Admin review (no DDL execution) | Secondary research track | S0 / S1 / S2 schema comparison (§15.3) | |
| Audit logging | Supporting | State and audit checks (§15.4) | |

## 3. Traceability chain (optional)

| RQ | Gap ID | Evidence (citations) | ClearQuery component(s) | Contribution class | Planned evaluation and metric |
|---|---|---|---|---|---|
| RQ4 → RQ5 | | | | | |

**Rules.** Every major component needs a gap-based rationale or must be labelled a supporting engineering requirement. Gaps that ClearQuery does not address are listed as honest limits. No row may claim novelty for Text-to-SQL, schema generation, semantic layers or clarification in general, or imply any measured result.
