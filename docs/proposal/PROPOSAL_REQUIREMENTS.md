# Proposal Requirements and Paper Outline (Sprint 0)

**Source of these requirements.** Everything in §1–§4 was **provided by the project owner** on 25 Oct 2026 as a summary of the university's official e-mail about the Proposal Discussion, the university's proposal Document Template and an instructional session held on 24 Oct 2026 (about 69 minutes). The template PDF and the session transcript were **not** read for this document, so nothing here is independently verified against them. The template and the session material are private university material: they are not copied into this public repository, and the private Overleaf link is not shared.

## 1. Official requirements (owner-provided)

The paper must use the university Document Template and contain:

- a structured **Literature Review**;
- **five Research Questions**, RQ1–RQ5, each with a clear, separately identifiable answer;
- **research gaps** derived from the reviewed literature, and a logical link from those gaps to the Proposed Solution;
- a detailed, evidence-based **Proposed Solution** that is not a single paragraph and explains what will be built, why it is needed, what problems it solves, how it differs from existing work and how it addresses the gaps;
- a clear **system architecture** with an illustrative diagram;
- a **comparison with existing tools or methods**.

The first Proposal Discussion period begins on **10 November 2026**. This is the start of the period, not necessarily our group's submission or discussion date.

## 2. Method guidance from the instructional session (owner-provided)

- An SLR must **synthesise** studies (group, compare, contrast), not list disconnected summaries of individual papers.
- Use reputable peer-reviewed sources. Suggested platforms: Springer Nature, ScienceDirect, Web of Science, the Egyptian Knowledge Bank, IEEE Xplore and the ACM Digital Library. Google Scholar can support discovery, but the venue's credibility must be checked.
- A publication range of about **2021–2026** was suggested. It is guidance, not a confirmed university rule; the protocol may admit justified foundational earlier work ([SLR_PROTOCOL_DRAFT.md](SLR_PROTOCOL_DRAFT.md#5-publication-window-language-and-preprints)).
- The session's worked example (an unrelated "Automation of Meeting Minutes" topic) is **teaching material only**. Its findings and figures must never be used as evidence for ClearQuery, and neither may the illustrative studies and numbers in the template.

## 3. Required paper structure

| Part | Required content | Notes |
|---|---|---|
| Title and Authors | Official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* | Title unchanged (D-33) |
| Abstract | 150–250 words, one paragraph: purpose/problem, review method, actual findings, proposed solution, conclusion | A **new Proposal Abstract**. The submitted registration Abstract ([../../README.md](../../README.md#abstract)) is frozen and is not overwritten |
| Index Terms | Keywords | — |
| I. Introduction | Context, problem, motivation, **RQ1–RQ5** | — |
| II. Review Protocol and Methodology | Eligibility and exclusion criteria, search strategy, study selection, PRISMA-style flow diagram, quality assessment, data extraction | **Table I** (Data Extraction) and **Table II** (Review Methodology Summary) |
| III. Results | Separate answers to **RQ1, RQ2, RQ3, RQ4** | **Table III** (Descriptive Statistics) |
| IV. Discussion | Synthesis, converging and conflicting evidence, research gaps, conceptual framework | — |
| V. Threats to Validity | Internal, construct, conclusion and external validity; overall limitations | — |
| VI. Proposed Solution | **Explicit RQ5 subsection**; A. Problem Statement Refinement; B. Design Rationale and Evidence-Based Justification; C. Architecture and Diagram; D. Expected Contributions; E. Positioning Against Existing Tools | Approved v6 diagram used unchanged; traceability matrix ([RQ_GAP_SOLUTION_MATRIX.md](RQ_GAP_SOLUTION_MATRIX.md)) |
| VII. Conclusion | Actual findings and intended (not demonstrated) contribution | — |
| References | IEEE style, every reference verifiable | — |

**RQ placement.** The session placed RQ1–RQ4 in the Results and let RQ5 lead into the Proposed Solution; the official e-mail requires a clear, separate answer for all five. The paper does both: RQ1–RQ4 are answered in Section III, RQ5 has its own explicit subsection in Section VI, and cross-references plus the traceability matrix link findings and gaps to design choices.

## 4. Required tables and figures

Owners follow the current Jira project `CQP` (D-38). The owners in the superseded D-37 `SCRUM` plan no longer apply.

| Item | Minimum content | Owner (Jira) |
|---|---|---|
| Table I — Data Extraction | Paper ID, authors, year, venue, domain, AI technique/model, main task, dataset/evidence, evaluation metrics, quantitative findings as reported, limitations, DOI/source | Abdelrahman (`CQP-4` template, `CQP-13` completed table) |
| Table II — Review Methodology Summary | Research framework, search protocol, eligibility criteria, search strategy, screening approach, quality assessment, data extraction and synthesis | George (`CQP-14`) |
| Table III — Descriptive Statistics | Actual corpus by year, study type, venue, domain, AI technique and method category, with counts and percentages | George (`CQP-14`) |
| PRISMA-style flow diagram | Real counts from the screening log only | Abdallah (`CQP-6` protocol, `CQP-12` counts and diagram) |
| Quality assessment | Criteria such as clear objectives, method quality, transparent evaluation, reproducibility, valid conclusions; suggested scoring Yes = 1, Partial = 0.5, No = 0; only scores the team actually produced | Abdelrahman (`CQP-4` rubric, `CQP-13` applied) |
| Conceptual framework figure | Literature-grounded concepts and relations | Sayed (`CQP-15`) |
| Architecture figure | Approved `assets/System-Overview-3840x2160-v6.png`, unchanged | Amr (`CQP-16`) |

## 5. Section ownership

| Section | Writer (Jira) | Independent check |
|---|---|---|
| Title and Authors, Index Terms | George (`CQP-5`), Sayed (`CQP-15`) | Deck and title audit in `CQP-20` |
| Abstract (a new Proposal Abstract, about 150–250 words), I. Introduction, IV. Discussion, VII. Conclusion | Sayed (`CQP-15`) | Reviewer named in `CQP-15` |
| II. Review Protocol and Methodology | Sayed (`CQP-3`), Abdallah (`CQP-6`, `CQP-12`), Abdelrahman (`CQP-4`) | QA-05 Abdallah (`CQP-31`) |
| III-A RQ1 | Sayed (`CQP-7`) | QA-03 Abdelrahman (`CQP-29`) |
| III-B RQ2 | Abdelrahman (`CQP-8`) | QA-02 Sayed (`CQP-28`) |
| III-C RQ3 | George (`CQP-9`) | QA-01 Amr (`CQP-27`) |
| III-D RQ4 | Abdallah (`CQP-10`) | Gap evidence checked in QA-05 (`CQP-31`) |
| Tables I–III | Abdelrahman (`CQP-13`), George (`CQP-14`) | Spot-check and reconciliation named in those issues |
| V. Threats to Validity | Abdallah (`CQP-12`) | Reviewer named in `CQP-12` |
| VI. Proposed Solution with the explicit RQ5 answer | Amr (`CQP-11`, `CQP-16`) | QA-04 George (`CQP-30`); RQ5 traceability in QA-05 (`CQP-31`) |
| RQ baseline and objectives | Amr (`CQP-2`) | Team agreement recorded in `CQP-2` |
| IEEE formatting and references | George (`CQP-5`, `CQP-14`) | Citation reconciliation in `CQP-14` |

The full task map is in [../SPRINT_0.md](../SPRINT_0.md#4-task-map). The detailed acceptance criteria of each section are in its Jira issue.
