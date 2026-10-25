# Proposal Workspace — Sprint 0 (ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic)

This folder holds the **planning documents** for the MIU graduation **proposal paper**: a structured Systematic Literature Review (SLR), five Research Questions (RQ1–RQ5) and a detailed Proposed Solution. It is **Deliverable 1 of 3** for the Proposal Discussion ([../SPRINT_0.md](../SPRINT_0.md)). It was added by decision **D-37** ([../CHANGE_RECORD_D-37.md](../CHANGE_RECORD_D-37.md)) and re-pointed to the current Jira project `CQP` by **D-38** ([../CHANGE_RECORD_D-38.md](../CHANGE_RECORD_D-38.md)).

> **Status (25 Oct 2026):** planning only. No search has been run, no study has been screened or included, no PRISMA count, quality score or table value exists yet, and no section of the paper has been written. Implementation of ClearQuery is **NOT STARTED**. The **full** graduation-project implementation is outside this milestone, but a minimal working **10% Proof of Concept** is one of the three mandatory Sprint 0 deliverables ([../SPRINT_0.md](../SPRINT_0.md#1-the-three-university-deliverables), [../poc/POC_KICKOFF.md](../poc/POC_KICKOFF.md)).

## Milestones

| Date | Milestone |
|---|---|
| 25 Oct 2026 | Registration form submitted (owner-confirmed). Committee acceptance of the expanded scope is **not confirmed**. Sprint 0 planned in Jira project `CQP` (D-38; the D-37 `SCRUM Sprint 0` plan is superseded) |
| 26 Oct – 8 Nov 2026 | Sprint 0 execution window (internal targets in [../SPRINT_0.md](../SPRINT_0.md#2-milestones)) |
| 8 Nov 2026 | Internal completion target; final readiness review |
| 9 Nov 2026 | Rehearsal, contingency checks and review buffer |
| 10 Nov 2026 | The university's first **Proposal Discussion period** begins (the start of the period, not necessarily our group's slot) |

## Navigation

| Document | Purpose |
|---|---|
| [PROPOSAL_REQUIREMENTS.md](PROPOSAL_REQUIREMENTS.md) | The university's proposal requirements, the required paper structure and who owns each section |
| [RESEARCH_QUESTIONS.md](RESEARCH_QUESTIONS.md) | RQ1–RQ5 working baseline, expected evidence and mapping to the V3.1 scope |
| [../SPRINT_0.md](../SPRINT_0.md) | **Current** Sprint 0 index: deliverables, milestones, Jira `CQP` task map, owners, dependencies |
| [SPRINT_0_PLAN.md](SPRINT_0_PLAN.md) | **Superseded** D-37 plan in the old `SCRUM` project; kept as history only |
| [SLR_PROTOCOL_DRAFT.md](SLR_PROTOCOL_DRAFT.md) | Draft review protocol (sources, query blocks, criteria, screening, quality, extraction) — a plan, not a completed search |
| [RQ_GAP_SOLUTION_MATRIX.md](RQ_GAP_SOLUTION_MATRIX.md) | Template linking research questions → evidence-based gaps → ClearQuery components → planned evaluation |
| [templates/](templates/) | CSV templates: [evidence tracker](templates/EVIDENCE_TRACKER_TEMPLATE.csv), [screening log](templates/SCREENING_LOG_TEMPLATE.csv), [quality assessment](templates/QUALITY_ASSESSMENT_TEMPLATE.csv) |

## Where the work happens

- **Jira (primary):** every task has a self-contained description with step-by-step instructions and a task-specific **AI execution prompt** to copy into a new AI session. Find your tasks in the task map in [../SPRINT_0.md](../SPRINT_0.md#4-task-map). The detailed prompts live only in Jira, so they are not duplicated here.
- **Private team folder:** research outputs (search exports, screening logs, extraction sheets, drafts) go to the team's private **University Drive** (decided 25 Oct 2026; the folder and its access settings are still pending, Amr). Store a paper PDF in the University Drive **only when its access and sharing terms permit it** (for example an open-access licence, or publisher or MIU/EKB terms that allow sharing within the team). Otherwise store only the DOI or link, the bibliographic metadata, your extraction notes and permitted references. PDFs never go into this public repository. The university template and any other restricted material never go into this public repository either.
- **Private Overleaf project:** the final paper is integrated by the team in the university's private Overleaf template. The template and its link are never shared with AI tools or committed here.
- **This repository:** planning documents and, with the owner's approval through a pull request, agreed public-safe artefacts (for example the final protocol or the gap-to-solution matrix).

## Document workflow

| Step | What happens | Jira | Where it is described |
|---|---|---|---|
| 1 | Agree RQ1–RQ5 and objectives | `CQP-2` | [RESEARCH_QUESTIONS.md](RESEARCH_QUESTIONS.md) |
| 2 | Fix the review protocol: sources, reproducible search strings, eligibility and exclusion criteria, publication window | `CQP-3` | [SLR_PROTOCOL_DRAFT.md](SLR_PROTOCOL_DRAFT.md) |
| 3 | Fix the extraction sheet (Table I fields) and the quality rubric | `CQP-4` | [templates/](templates/), [SLR_PROTOCOL_DRAFT.md §7](SLR_PROTOCOL_DRAFT.md#7-quality-assessment-draft) |
| 4 | Fix the IEEE structure, formatting checklist and shared reference library | `CQP-5` | [PROPOSAL_REQUIREMENTS.md §3](PROPOSAL_REQUIREMENTS.md#3-required-paper-structure) |
| 5 | Fix the screening procedure and PRISMA tracking | `CQP-6` | [SLR_PROTOCOL_DRAFT.md §6](SLR_PROTOCOL_DRAFT.md#6-study-selection) |
| 6 | Run the logged searches; screen title/abstract and full text; record every decision | `CQP-12` (with the RQ owners) | [templates/SCREENING_LOG_TEMPLATE.csv](templates/SCREENING_LOG_TEMPLATE.csv) |
| 7 | Extract evidence and assess quality of included studies | `CQP-13` (with the RQ owners) | [templates/EVIDENCE_TRACKER_TEMPLATE.csv](templates/EVIDENCE_TRACKER_TEMPLATE.csv), [templates/QUALITY_ASSESSMENT_TEMPLATE.csv](templates/QUALITY_ASSESSMENT_TEMPLATE.csv) |
| 8 | Synthesise RQ1–RQ4 comparatively (group, compare, contrast; never one summary per paper) | `CQP-7`, `CQP-8`, `CQP-9`, `CQP-10` | [RESEARCH_QUESTIONS.md §2](RESEARCH_QUESTIONS.md#2-expected-evidence) |
| 9 | PRISMA diagram with real counts; Threats to Validity | `CQP-12` | [PROPOSAL_REQUIREMENTS.md §4](PROPOSAL_REQUIREMENTS.md#4-required-tables-and-figures) |
| 10 | Tables I, II and III from the real corpus; citation reconciliation | `CQP-13`, `CQP-14` | [PROPOSAL_REQUIREMENTS.md §4](PROPOSAL_REQUIREMENTS.md#4-required-tables-and-figures) |
| 11 | Gap-to-solution traceability and the explicit RQ5 answer | `CQP-11` | [RQ_GAP_SOLUTION_MATRIX.md](RQ_GAP_SOLUTION_MATRIX.md) |
| 12 | Proposed Solution (Section VI) with the unchanged v6 diagram and the planned P2-vs-P4 evaluation | `CQP-16` | [../SPECIFICATION.md](../SPECIFICATION.md) §8, §15 |
| 13 | Introduction, new Proposal Abstract, Discussion, Conclusion | `CQP-15` | [PROPOSAL_REQUIREMENTS.md §3](PROPOSAL_REQUIREMENTS.md#3-required-paper-structure) |
| 14 | Independent QA and human review | `CQP-27` … `CQP-31` | [../SPRINT_0.md §4.4](../SPRINT_0.md#44-independent-qa-cqp-27--cqp-31) |

**Evidence is collected by the team.** None of these files contains a finding, a count, a score or a reference yet. Every citation must be a real, checkable IEEE-style reference that a team member has actually read.

## Rules that apply to every Sprint 0 task

1. The V3.1 scope, the official title, the submitted registration Abstract and the v6 diagram are unchanged ([../SPECIFICATION.md](../SPECIFICATION.md) is the source of truth).
2. No fabricated references, findings, counts, scores, vendor capabilities or review actions ([../../AGENTS.md](../../AGENTS.md#3-non-negotiable-project-rules), rule 10).
3. ClearQuery has no results; intended outcomes are never written as demonstrated.
4. AI output is a draft. A task is complete only after the named human reviewer has checked it.
