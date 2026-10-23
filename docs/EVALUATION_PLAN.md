# V3.1 Evaluation Plan — Voice-to-SQL in Egyptian Arabic

> **Repository note (staging, 23 Oct 2026).** This file has two parts.
>
> - **Part A — Evaluation at a glance** is a navigation summary written for this repository. It adds **no new decisions**: every count and definition is taken from the documents it cites, and **those documents win** if anything here ever disagrees.
> - **Part B** is the registration package's evaluation notes on the translation pipeline, P2/P4 fairness and error separation, copied byte-for-byte between `BEGIN VERBATIM` / `END VERBATIM` markers.
>
> **Normative definitions** live in [SPECIFICATION.md](SPECIFICATION.md) §15.1–§15.5 and [DATASET_STRATEGY.md](DATASET_STRATEGY.md) §6–§8. **Nothing has been run, collected or measured.** All counts are planned targets. Numeric pass/fail thresholds from V2 are not approved for V3.1 (SPECIFICATION.md §15.2, last paragraph).

## Part A — Evaluation at a glance

### A.1 Hypotheses and tracks

| Track | Hypothesis | Role | Normative source |
|---|---|---|---|
| Analytics reliability: P2 vs P4 on Sales | **H-A**: Arabic-anchored BIR + deterministic Answer/Clarify/Abstain (P4) reduces materially incorrect direct business answers relative to a strong clarification-enabled LLM baseline (P2) while keeping usable coverage | **Primary** | SPEC §3.2, §15.1–§15.2; DATA §7 |
| Voice condition | (part of H-A) voice-vs-text delta, ASR-induced decision changes | Descriptive, with clustered CIs | SPEC §14.2; DATA §6 |
| Translation stage | (diagnostic) does the Arabic-to-English step preserve ambiguity and entities? | Diagnostic only; never changes a P4 decision | SPEC §8.1, §15.2; DATA §7.6; Part B |
| Security suite | (part of **H-H**) no cross-department exposure; DENY before any LLM call | Mandatory verification, **excluded** from semantic metrics | SPEC §15.4; DATA §7.4 |
| Inventory and HR acceptance | (part of **H-H**) the same engine works in three distinct workspaces | Mandatory functional acceptance | SPEC §14.3, §15.4 |
| AI Schema Design: S0 / S1 / S2 | **H-S**: SRR + clarifications + validation + Admin review give more requirement-faithful proposals than direct prompting | **Secondary** | SPEC §3.3, §15.3; DATA §8 |
| Hub integration and approval integrity | **H-H** (engineering) | Mandatory verification | SPEC §15.4; ARCHITECTURE Part B (R1–R5) |
| Market need | **H-M** (unverified) | Validation only; no results claimed | SPEC §3.3, §15.5, §16 |

### A.2 Planned evaluation data (targets, nothing collected)

| Asset | Planned size | Key rules |
|---|---|---|
| Sales Egyptian-Arabic benchmark | **400 items** = **375 semantic** (≈180 Answer · 110 Clarify · 85 Abstain) + **25 security** | Dev ≈25% / test ≈75% by **template family**; two independent annotators (Cohen's κ before adjudication); question-specific gold SQL for every answerable interpretation, executed on snapshots S1 and S2; human-reviewed English equivalent per item (evaluation-only) |
| Inventory acceptance set | ≈60 typed items + 24 recordings (20 test) | Test-only except a 10-item dev slice |
| HR acceptance set | ≈60 typed items + 24 recordings (20 test) | Synthetic-only data; test-only except a 10-item dev slice |
| Voice recordings | **192 core** (Sales 144 · Inventory 24 · HR 24; optional ≈260) | ≥10 consenting native speakers (target 12: 4 dev + 8 test); speaker- **and** template-family-disjoint; consent protocol first |
| ASR background benchmark | Casablanca (Egypt subset) | Validation split for model selection; test split run **once** after the configuration freeze |
| Schema-design briefs | **30–60** incomplete briefs (start at 30), ≥5 domains | Degradation protocol; condition-blind independent reviewers; scored **before** human revision |
| Public Text-to-SQL datasets | Spider, BIRD Mini-Dev, Gretel, AraSpider | Reference or optional sanity checks only; **never** test items, never translated into the test set, never used for training |

### A.3 Pipelines compared (analytics)

| ID | Short definition (SPEC §15.1) |
|---|---|
| P0 | `q_ar` + cached `q_en` + schema → LLM SQL directly (weak transparency baseline) |
| P1 | P0 + full sanctioned glossary, aliases, time policy and schema context |
| **P2** | P1 + explicit clarify/abstain instructions, same one-turn limit — **strong primary baseline** |
| P3 | *Optional, redefined 23 Oct 2026, team confirmation pending (Q14):* P2 given only `q_en` |
| **P4** | Arabic-anchored BIR/resolvers + deterministic policy + English-to-SQL from `q_en` and resolved BIR + BIR↔SQL consistency guard — **proposed method** |

**Matched inputs:** every pipeline receives byte-identical frozen inputs: the same confirmed Arabic text (or the same frozen ASR transcript), the same cached translation, catalog, views, as-of date, snapshot, LLM and settings, clarification budget and simulated user. The authorization gate and SQL guard are shared infrastructure credited to neither method.

### A.4 Metrics (definitions: SPEC §15.2 and DATA §7.4)

- **Semantic metrics, on semantic-eligible items only:** end-to-end and policy-compliant Business-Answer Accuracy (BAA); Unsafe Direct Answer Rate; SER_direct and SER_final; selective accuracy/risk with coverage and risk–coverage curves; clarification precision and recall (an unnecessary or wrong-target clarification is a false positive); abstention precision, recall and mistaken-abstention rate.
- **Supporting:** SQL execution accuracy on S1/S2 (does not certify intent); ASR WER, CER and entity error rate; voice-vs-text decision-change and answer-change rates; latency p50/p95; interaction count; model cost.
- **Translation diagnostics:** meaning preservation against the human English references (human-judged sample + chrF as secondary); entity preservation; Ambiguity-Preservation Rate and Translation Ambiguity-Collapse Rate.
- **Error separation:** semantic (business-meaning) errors are reported separately from SQL/result errors, with one primary stage attribution per failure (ASR → translation → BIR/resolver → policy → SQL generation → guard).
- **Security suite:** gate-DENY correctness, pre-deny LLM invocations (must be 0), restricted-metadata exposures (0), unauthorized SQL executed (0). DENY is a gate outcome, **not** a fourth model decision.
- **Schema track:** requirement coverage, entity/attribute F1 with semantic matching, PK/FK and cardinality correctness, unsupported-assumption rate, MUST_ASK recall, DDL validity in a throwaway sandbox, reviewer effort, inter-reviewer agreement.
- **Statistics:** paired analysis with confidence intervals; McNemar and bootstrap clustered by template family where appropriate. The benchmark is too small for subgroup claims.

### A.5 Leakage and freeze rules (summary)

1. Generator parameters, catalog, as-of date and test split are frozen and hashed before any P2/P4 test run; prompts iterate on **dev** only, with the same logged budget for P2 and P4.
2. ASR, normalization, biasing, translation prompt/glossary and few-shot exemplars are chosen on dev data (or public datasets) only, then frozen and hashed.
3. Human English equivalents, gold SQL and gold results **never** enter a prompt.
4. No model is trained or fine-tuned.

---

## Part B — Evaluation notes: translation pipeline, P2/P4 fairness and error separation

<!-- BEGIN VERBATIM source="06_RESEARCH_AND_DATA/V3_1_EVALUATION_NOTES_TRANSLATION_PIPELINE.md" sha256="08cf6917d1331227b2c21cec34dffe90f436f05fd8297c18901c0520a4621b9c" -->
# V3.1 Evaluation Notes — Translation Pipeline, P2/P4 Fairness and Error Separation

**Date:** 23 October 2026 · **Status:** evaluation **plan** synchronized with the TA-clarified pipeline; nothing has been run, collected or measured. The normative definitions stay in spec §15.1–§15.2 and dataset strategy §7.4–§7.6. This note explains them in one place and does not override them.

## 1. Why this note exists

The TA clarified that the intended pipeline is **Egyptian-Arabic voice → speech-to-text → Arabic transcript → Arabic-to-English translation → English question → English-to-SQL → guarded execution**. The research contribution (preventing silent business-semantic errors) depends on ambiguity being detected **before** any SQL. A translation can silently resolve an ambiguity: "مين أكتر فرع كسبان الشهر اللي فات؟" may come out as "Which branch was the most profitable last month?", which fixes gross profit when the user may have meant net sales. The evaluation must therefore show where such errors arise and keep the P2-vs-P4 comparison fair.

## 2. Processing order evaluated (spec §8.1)

| # | Stage | Input | Output | Authority |
|---|---|---|---|---|
| 1 | Authorization gate | identity, selected workspace | allow / DENY (no model call on DENY) | server |
| 2 | ASR (voice only) + user confirmation | audio | confirmed Arabic `q_ar` | `q_ar` is authoritative |
| 3 | Context loading | workspace | approved catalog, views, aliases, as-of date | server |
| 4 | BIR + ambiguity detection | `q_ar` + catalog (**not** `q_en`) | BIR, ambiguity flags | **decides meaning** |
| 5 | Translation (parallel, derived) | `q_ar` | `q_en` (ambiguity-preserving), translation audit flags | diagnostic only; never changes the decision |
| 6 | Policy | BIR, resolvers, authorization context | Answer / Clarify / Abstain | deterministic |
| 7 | Clarify loop (max 1) | user reply | resolved BIR | no SQL while pending |
| 8 | Abstain | — | reason | no SQL |
| 9 | English-to-SQL (Answer only) | `q_en` + **resolved BIR** + authorized schema | one SELECT | BIR overrides `q_en` on conflict |
| 10 | Guards + execution | SQL | AST, allowlist, authorization, BIR↔SQL consistency → read-only run | rejected SQL → Abstain (unsafe/inconsistent) |

## 3. P2 versus P4 fairness: matched inputs

| Held identical for every pipeline (P0–P4) | How |
|---|---|
| Arabic input | Text condition: the benchmark `question_ar`. Voice condition: **the same frozen ASR transcript** per utterance, generated once |
| English translation | `q_en` generated **once per frozen Arabic input** by the same frozen translation model, prompt and glossary, cached and reused by all pipelines |
| Context | Same catalog text, authorized views, as-of date, DB snapshot (S1/S2) |
| Model settings | Same LLM and version, temperature and decoding; same logged prompt-iteration budget on dev only |
| Interaction | Same one-clarification budget; same deterministic simulated user (`scripted_user_reply`; any other clarification gets "مش فاهم قصدك" and counts as a false positive) |
| Safety infrastructure | Same authorization gate and AST/allowlist/read-only guard (not credited to either method) |

**Method-specific (what is being tested):** P4's Arabic-anchored BIR, deterministic resolvers and policy, and the BIR↔SQL consistency guard. P2 is a single strong LLM prompt that sees **both** `q_ar` and `q_en`, the full glossary and explicit clarify/abstain instructions.

**Optional ablations (do not replace the primary comparison):**
- **P3 (redefined; team confirmation pending, spec Q14):** P2 given only `q_en`. It measures how much ambiguity handling degrades when the Arabic original is discarded.
- **Oracle translation:** P2/P4 given the human-reviewed English reference instead of `q_en`. This is an upper-bound diagnostic only.
- **ASR oracle:** the voice condition with manual transcripts. It separates ASR from downstream errors (this was already implied by the voice-vs-text delta).

## 4. Leakage controls

1. Human-reviewed English equivalents, gold SQL and gold results never appear in any prompt or few-shot example.
2. ASR, normalization, vocabulary biasing, translation prompt/glossary and few-shot exemplars are chosen on **dev** items (or public datasets) only, identically for P2 and P4. The configurations are hashed and frozen before any test run.
3. Splits are by template family; voice recordings are also speaker-disjoint (DS-6).
4. Public Text-to-SQL datasets (Spider, BIRD Mini-Dev, Gretel, AraSpider) may provide generic exemplars or optional sanity checks. They never provide test items, are never translated into the test set, and are never used for training or fine-tuning.
5. The test split is hashed and frozen before final runs; Casablanca-Egypt test is run once after the ASR freeze.

## 5. Keeping semantic errors separate from numerical/SQL errors

Every delivered answer on a semantic-eligible item is classified:

| Class | Definition | Counted in |
|---|---|---|
| **Correct** | Interpretation matches the intended (or clarified) BIR **and** the result equals the gold result on the snapshot | BAA, selective accuracy |
| **Semantic error** | The answer was delivered under an interpretation different from the intended/clarified one, **or** it is an unsafe direct answer to a clarification-required item, whatever the number | Unsafe Direct Answer Rate; semantic-error count; policy-compliant BAA failure |
| **SQL/result error** | Interpretation correct, but the SQL result differs from gold (wrong join, filter, aggregation, date bound) | SER (numerical); SQL error count |
| **Answer on unanswerable** | Any delivered answer on an Abstain item | Selective risk; abstention recall failure |

SER_direct and SER_final stay **numerical** definitions (spec §15.2). The semantic/SQL split is reported **alongside** them, so a coincidentally correct number under a guessed interpretation is never credited as correct ambiguity handling.

**Stage attribution** (each failure gets exactly one primary cause, assigned by an annotator using the logged artifacts): ASR → translation (`q_en` lost or changed meaning or an entity) → BIR/resolver → policy → SQL generation → guard rejection. For P4, a translation collapse that did **not** change the decision is logged as "collapse contained", which is direct evidence for the contribution.

## 6. Translation-stage metrics (diagnostic)

- **Meaning preservation:** human judgment (adequate / partially adequate / inadequate) on a stratified sample against `question_en_reference`, plus an automatic score such as chrF as a secondary signal.
- **Entity preservation rate:** catalog entities in `q_ar` correctly rendered as their `name_en` in `q_en`.
- **Ambiguity-Preservation Rate** = clarification-required items whose `q_en` still keeps the ambiguity / |C*|. **Translation Ambiguity-Collapse Rate** = 1 − that rate.
- **Collapse impact:** among collapsed items, the share where P2 (and P3) answered directly (unsafe) versus the share where P4 still clarified.
- Reported separately for the text and voice conditions.

## 7. What stays unchanged

The counts (375 semantic + 25 security Sales items; Inventory and HR ≈60 typed + 24 voice each; 192 recordings; 30–60 schema briefs), the DS-7 metric definitions, the separate Security suite (DENY is a gate outcome, not a fourth decision), the S0/S1/S2 schema track, and the rule that no model is trained or fine-tuned.

## 8. Open items

- Q14: confirm the P3 redefinition (optional).
- Choice of translation model or prompt is made on dev data during implementation (not now).
- No public Egyptian-Arabic→English business-question corpus was verified; ArzEn access remains unverified and is not required.
<!-- END VERBATIM source="06_RESEARCH_AND_DATA/V3_1_EVALUATION_NOTES_TRANSLATION_PIPELINE.md" -->
