# Systematic Literature Review Protocol — DRAFT

> **DRAFT. No search has been run.** This is the starting plan for Jira task **`CQP-3`** (owner Sayed; independent reproducibility check by Abdallah in QA-05, `CQP-31`; D-38. The superseded D-37 plan called this task S0-02 in the old `SCRUM` project). Sayed will finalise the databases, exact queries, criteria and window. Every count, decision and score must later come from real, logged searches and screening. Nothing in this file is a finding.

## 1. Review objective and questions

To identify, appraise and synthesise peer-reviewed evidence on natural-language and speech-based querying of relational databases, with emphasis on Arabic and Egyptian-Arabic interaction, ambiguity handling and selective answering, in order to answer RQ1–RQ4 and to ground the Proposed Solution (RQ5). The questions are in [RESEARCH_QUESTIONS.md](RESEARCH_QUESTIONS.md).

- **Literature RQs** (answered by this protocol): RQ1, RQ2 and RQ4.
- **RQ3** uses official product documentation (with access dates) plus any peer-reviewed tool evaluations found by the protocol. Vendor claims are kept separate from research findings.
- **RQ5** is answered by design reasoning from RQ1–RQ4 ([RQ_GAP_SOLUTION_MATRIX.md](RQ_GAP_SOLUTION_MATRIX.md)).

## 2. Information sources (to confirm against actual MIU / EKB access)

| Source | Role | Note |
|---|---|---|
| IEEE Xplore | Primary | Instructor-recommended |
| ACM Digital Library | Primary | Instructor-recommended |
| ScienceDirect | Primary | Instructor-recommended |
| SpringerLink (Springer Nature) | Primary | Instructor-recommended |
| Web of Science | Primary, if accessible | Instructor-recommended; access through the EKB to be confirmed |
| Egyptian Knowledge Bank (EKB) | Access route / primary | Instructor-recommended |
| ACL Anthology | Primary (proposed) | Main peer-reviewed venue family for Text-to-SQL and Arabic NLP; team to confirm |
| Google Scholar, arXiv | Discovery only | Venue credibility must be checked; the preprint rule is in §5 |
| [../SPECIFICATION.md](../SPECIFICATION.md) §24.2 references | Leads only ("other sources" in PRISMA) | Each one is screened with the same criteria; none is pre-included |

## 3. Search strategy (concept blocks — to be adapted per database)

| Block | Purpose | Candidate terms |
|---|---|---|
| A | Database querying | "text-to-SQL" OR "text to SQL" OR NL2SQL OR "natural language interface* to database*" OR NLIDB OR "conversational business intelligence" OR "natural language query*" AND (database OR SQL) |
| B | Language and modality | Arabic OR "Egyptian Arabic" OR dialect* OR "code-switch*" OR speech OR spoken OR voice OR ASR OR "speech recognition" |
| C | Reliability | ambigu* OR clarif* OR "clarification question*" OR unanswerable OR abstain* OR abstention OR "selective prediction" OR "semantic error*" OR uncertainty |
| D | Secondary: schema design | "schema design" OR "database schema generation" OR "requirements to schema" OR "conceptual model* generation" |

Indicative master queries (to be refined after a pilot):

- **RQ1:** A AND (B OR "business analytics" OR "business intelligence")
- **RQ2:** (A AND (C OR "schema linking" OR "schema grounding")) OR (B AND ("speech recognition" OR translation) AND Arabic)
- **RQ4:** A AND C, plus a targeted search on evaluation (benchmark* AND (ambigu* OR unanswerable))
- **Secondary:** D AND ("large language model*" OR LLM OR "natural language")

Each database search is logged with the exact string, date, field restrictions, filters, result count and export file, using [templates/SCREENING_LOG_TEMPLATE.csv](templates/SCREENING_LOG_TEMPLATE.csv). Every query refinement after the pilot is logged too.

## 4. Eligibility and exclusion criteria (draft codes)

| Code | Inclusion criterion |
|---|---|
| I1 | Addresses at least one review topic: NL/speech querying of relational databases, Text-to-SQL, schema grounding, ambiguity/clarification/abstention in NL querying, Arabic/dialectal NLP or ASR relevant to querying, or NL-to-schema generation |
| I2 | Peer-reviewed journal or conference paper, or a peer-reviewed benchmark/dataset paper |
| I3 | Within the agreed publication window (§5), or a justified foundational exception |
| I4 | Written in English |
| I5 | Full text accessible for full-text screening |
| I6 | Reports a method, system, benchmark, evaluation or systematic review with technical evidence |

| Code | Exclusion reason |
|---|---|
| E1 | Off-topic |
| E2 | Duplicate or superseded version of an included study |
| E3 | Not peer-reviewed (preprint only, thesis, blog, white paper) and not admitted by §5 |
| E4 | Outside the publication window without a recorded justification |
| E5 | Not in English |
| E6 | Full text not available |
| E7 | Insufficient technical evidence (no method, evaluation or data) |
| E8 | Below the agreed quality threshold (from `CQP-4`, applied in `CQP-13`) |

## 5. Publication window, language and preprints

- **Window:** the instructor suggested about 2021–2026. This is guidance, not a confirmed university rule. The protocol owner sets the window and records why.
- **Foundational exceptions:** earlier works (for example widely used benchmarks) may be admitted only with a written justification per study, and they are reported as such.
- **Language:** English full texts. Arabic-language studies may be noted as a limitation if they are excluded.
- **Preprints:** proposed rule: include only when a peer-reviewed version exists (cite that version); otherwise exclude with E3, or report it separately as grey literature if the team agrees. The final rule is decided in `CQP-3`.

## 6. Study selection

1. **Identification:** run the logged searches; add "other sources" separately.
2. **Deduplication:** by DOI first, then normalised title + first author + year; record the number removed.
3. **Title/abstract screening:** two screeners where possible; record both decisions, the final decision and the exclusion code.
4. **Full-text screening:** obtain texts legally (MIU/EKB, open access, author copies); record E6 when a text is unavailable. Store a paper PDF in the University Drive **only when its access and sharing terms permit it** (for example an open-access licence, or publisher or MIU/EKB terms that allow sharing within the team). Otherwise store only the DOI or link, the bibliographic metadata, your extraction notes and permitted references. PDFs never go into this public repository.
5. **Quality assessment:** with the [quality template](templates/QUALITY_ASSESSMENT_TEMPLATE.csv) (`CQP-4` rubric, applied in `CQP-13`); record any E8 exclusion.
6. **PRISMA 2020-style diagram:** computed only from the log (`CQP-12`, following the `CQP-6` protocol).

Disagreements are resolved by discussion, with the screening owner (Abdallah, `CQP-6` and `CQP-12`) deciding; unresolved cases go to Amr. Each resolution is recorded.

## 7. Quality assessment (draft)

| Criterion | Question |
|---|---|
| QA1 | Are the objectives clearly stated? |
| QA2 | Is the method sound and appropriate? |
| QA3 | Is the evaluation transparent (data, metrics, baselines)? |
| QA4 | Is the work reproducible (data, code or settings available)? |
| QA5 | Are the conclusions supported by the evidence? |

Scoring: Yes = 1, Partial = 0.5, No = 0. The threshold and its use (exclude, or include with a caveat) are decided in `CQP-4` and recorded. Only scores the team actually assigned are reported.

## 8. Data extraction and synthesis

Extraction uses [templates/EVIDENCE_TRACKER_TEMPLATE.csv](templates/EVIDENCE_TRACKER_TEMPLATE.csv); it feeds Table I and the RQ syntheses. Synthesis is thematic and comparative per RQ. Numbers from different benchmarks or settings are never ranked against each other.

## 9. Reproducibility record

The final protocol, the search log and the export files are kept in the team's private University Drive; paper PDFs are kept there only when their access and sharing terms permit it, otherwise as DOI links, bibliographic metadata and extraction notes. The final protocol (no copyrighted full texts) may be proposed for this repository through a pull request.
