# Research Questions — Working Baseline (Sprint 0)

**Status:** working baseline proposed by the project owner on 25 Oct 2026. The team reviews and agrees the final wording in Jira task **`CQP-2`** (owner Amr; D-38. The superseded D-37 plan called this task S0-01 in the old `SCRUM` project). The wording below is not final until that review is recorded. Any refinement may narrow wording or remove overlap, but must not change the V3.1 scope ([../SPECIFICATION.md](../SPECIFICATION.md) §5).

## 1. The five questions

| ID | Focus | Working question | Answered in |
|---|---|---|---|
| RQ1 | State of the art | What is the current state of research on natural-language and speech-based querying of relational databases, particularly for Arabic-language interaction and business analytics? | Section III-A |
| RQ2 | AI methods | Which AI techniques and architectures have been investigated for speech recognition, Arabic language processing, Text-to-SQL, schema grounding, ambiguity detection, and controlled clarification? | Section III-B |
| RQ3 | Existing tools | What commercial and open-source conversational database analytics tools exist, and what capabilities, limitations, and deployment characteristics do they offer? | Section III-C |
| RQ4 | Research gaps | What unresolved limitations remain in semantic correctness, ambiguity handling, Egyptian-Arabic speech, missing business data, authorization, and evaluation? | Section III-D (and Section IV) |
| RQ5 | Proposed directions | How can an ambiguity-aware Egyptian-Arabic Voice-to-SQL architecture address the identified gaps while enabling safe, controlled, multi-department business analytics? | Section III-E (short) and Section VI (full) |

## 2. Expected evidence

| RQ | Evidence type | Typical sources | Must not rely on |
|---|---|---|---|
| RQ1 | Peer-reviewed studies and benchmarks found by the SLR protocol | IEEE Xplore, ACM DL, ACL Anthology, ScienceDirect, SpringerLink, EKB | Single summaries per paper; unverified preprints presented as peer-reviewed |
| RQ2 | Peer-reviewed method studies with reported evaluation settings | Same as RQ1 | Cross-benchmark numeric rankings |
| RQ3 | Official product documentation (with access dates) and independent or peer-reviewed tool evaluations, kept separate | Vendor docs, open-source repositories, published evaluations | Marketing claims as findings; "not supported" without an explicit statement |
| RQ4 | Limitations and open problems reported in RQ1–RQ3 evidence; every gap supported by citations | Included studies, tool evidence | Absence of search results presented as a proven gap |
| RQ5 | Design reasoning grounded in RQ1–RQ4, mapped to the fixed V3.1 architecture and its planned evaluation | [../SPECIFICATION.md](../SPECIFICATION.md) §8, §11, §12, §15; [RQ_GAP_SOLUTION_MATRIX.md](RQ_GAP_SOLUTION_MATRIX.md) | ClearQuery results (none exist); novelty claims for Text-to-SQL, schema generation, semantic layers or clarification in general |

## 3. Scope mapping (initial; `CQP-2` refines it)

**P** = primary research contribution, **S** = supporting or secondary capability, **–** = not a focus of that RQ.

| V3.1 capability | Contribution type | RQ1 | RQ2 | RQ3 | RQ4 | RQ5 |
|---|---|---|---|---|---|---|
| Arabic-anchored Business Intent Representation (BIR) | Primary | S | P | S | P | P |
| Ambiguity detection on the original Arabic with an approved catalog | Primary | S | P | S | P | P |
| Deterministic Answer / Clarify / Abstain (selective answering) | Primary | – | P | S | P | P |
| P2-vs-P4 evaluation of silent semantic errors and risk–coverage | Primary (planned evaluation) | S | S | – | P | P |
| Egyptian-Arabic speech (ASR) with an editable transcript | Supporting | P | P | S | P | S |
| Ambiguity-preserving Arabic-to-English translation (derived, audited) | Supporting | S | P | – | S | S |
| English question-to-SQL constrained by the resolved BIR | Supporting | P | P | S | S | S |
| Read-only SQL guards (AST, allowlist, BIR↔SQL consistency) | Supporting | – | S | S | S | S |
| Server-side authorization across Sales, Inventory and HR | Supporting | – | – | S | S | S |
| AI-assisted schema design with Admin approval (no DDL execution) | Secondary research track (S0–S2) | – | S | S | S | S |

The primary research focus follows [../SPECIFICATION.md](../SPECIFICATION.md) §3.2 (hypothesis H-A): reducing silent semantic errors in Egyptian-Arabic Voice-to-SQL through ambiguity-aware business-intent interpretation and selective answering. The schema-design track follows the provisional hypothesis H-S (§3.3).

## 4. Coherence checks for `CQP-2`

- RQ1 maps the landscape, RQ2 the methods, RQ3 the tools, RQ4 the gaps and RQ5 the proposed direction; no two questions should ask the same thing.
- No RQ may need ClearQuery experimental results to be answered.
- AI-assisted schema design is covered as a secondary capability without displacing the primary focus.
- Final wording, sub-questions and the agreed matrix are recorded in Jira (`CQP-2`). A later pull request may update this file.
