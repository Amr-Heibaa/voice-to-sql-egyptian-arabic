# Change Record D-37 — Registration Form Submitted; Proposal Sprint 0 Planning

| Field | Value |
|---|---|
| Decision | **D-37** |
| Date | 2026-10-25 |
| Authorized by | The project owner (`Amr-Heibaa`), in the Sprint 0 planning instruction of 25 Oct 2026. That instruction confirmed the form submission, asked for the Jira work breakdown in the existing project and asked for this documentation through a draft pull request |
| What this records | (1) The owner's confirmation of the registration-form submission on 25 Oct 2026. (2) The proposal Sprint 0 work breakdown created in Jira. (3) The planning documents added under `docs/proposal/` |
| Impact | Status and planning documentation only. The title, the registration Abstract, the specification, the architecture, the dataset strategy, the evaluation plan, the field text and the v6 diagram are unchanged. Implementation remains **NOT STARTED**; no dataset, recording or result exists; no literature search has been performed yet |

## 1. Registration status (owner-confirmed)

- The owner confirmed on 25 Oct 2026 that the student submitted the graduation-project registration form personally on that day.
- **Submission is not acceptance.** Formal committee acceptance of the expanded V3.1 scope is still **not confirmed** (open decision Q12).
- Historical records (D-26 to D-36) and the dated status lines inside the marked blocks (for example `docs/SPECIFICATION.md` §19 and the status line inside the `docs/REGISTRATION_FORM_FIELDS.md` block) are **not rewritten**. They were correct when written. [PROJECT_STATUS.md](../PROJECT_STATUS.md) is the live status.

## 2. Why a proposal sprint

The university's first Proposal Discussion period begins on **10 Nov 2026**. The proposal paper must be a structured Systematic Literature Review with five research questions, evidence-based research gaps and a detailed Proposed Solution ([proposal/PROPOSAL_REQUIREMENTS.md](proposal/PROPOSAL_REQUIREMENTS.md)). The work was split into owned, reviewed tasks so that every number and claim in the paper comes from real, traceable evidence.

## 3. Jira structure created (read back and verified on 25 Oct 2026)

| Item | Result |
|---|---|
| Site and project | Existing Jira project **ClearQuery**, key `SCRUM` (reused; not recreated, key unchanged) |
| Sprint | Existing **`SCRUM Sprint 0`**, active, 25 Oct – 8 Nov 2026: reused. It was not restarted, re-dated, completed or duplicated. `SCRUM Sprint 1` (future, empty) was not touched |
| Existing items | `SCRUM-1` to `SCRUM-4` (generic titles, empty descriptions; probably onboarding samples, not confirmed) were not modified |
| Epic | `SCRUM-5` — *ClearQuery Proposal — Systematic Literature Review & Proposed Solution*, owner Amr |
| Tasks | 18 tasks, `SCRUM-6` to `SCRUM-23` (planning IDs S0-01 to S0-18), all **To Do**, all in Sprint 0, all children of `SCRUM-5`, with priorities and due dates |
| QA subtasks | 5 subtasks under `SCRUM-22` (S0-17), `SCRUM-24` to `SCRUM-28`, one cross-reviewer per team member. Subtasks in this project have no Priority or Due date field, so the target date is in the description |
| Dependencies | 38 **Blocks** links between the tasks |
| Task content | Each task description contains the eight required sections: overview; background with repository paths; step-by-step instructions; a task-specific copy-and-paste AI execution prompt; deliverables; acceptance criteria; human review and hand-off; dependencies and deadline |
| Read-back | All 23 child items (18 tasks and 5 subtasks) were read back and checked automatically: issue type, status To Do, assignee, priority, due date, Epic parent, Sprint 0 membership, all eight section headings, Blocks links equal to the planned dependencies, no e-mail address in descriptions, and each AI prompt matching the generated prompt (18 unique prompts) |
| Assignees | All five members were resolved to unique, active, assignable project accounts. Identifiers are deliberately not recorded here |
| Reviewer field | The project has no native Reviewer field. Reviewers are named in each task description and in the QA subtasks; no custom field was invented |

The task index with links is in [proposal/SPRINT_0_PLAN.md](proposal/SPRINT_0_PLAN.md#4-jira-task-index).

## 4. Ownership

| Member | Owns |
|---|---|
| Amr | S0-01 RQ baseline, S0-09 RQ5 traceability, S0-14 Proposed Solution, S0-15 Introduction/Abstract/Conclusion, S0-18 readiness review |
| Sayed | S0-02 SLR protocol, S0-05 RQ1, S0-12 Discussion and conceptual framework |
| Abdelrahman | S0-04 extraction and quality assessment, S0-06 RQ2, S0-10 Table I, S0-17 QA coordination |
| George | S0-07 RQ3, S0-11 Tables II–III, S0-16 IEEE integration |
| Abdallah | S0-03 study selection and PRISMA, S0-08 RQ4, S0-13 Threats to Validity |

No task is reviewed by its owner. Workload risk: Amr (five tasks on the critical path) and Abdelrahman (four tasks plus QA coordination).

## 5. Repository changes

New files:

- `docs/CHANGE_RECORD_D-37.md` (this record).
- `docs/proposal/README.md`, `PROPOSAL_REQUIREMENTS.md`, `RESEARCH_QUESTIONS.md`, `SPRINT_0_PLAN.md`, `SLR_PROTOCOL_DRAFT.md`, `RQ_GAP_SOLUTION_MATRIX.md`.
- `docs/proposal/templates/EVIDENCE_TRACKER_TEMPLATE.csv`, `SCREENING_LOG_TEMPLATE.csv`, `QUALITY_ASSESSMENT_TEMPLATE.csv`. These are **header-only** templates: one header row and no data. They are a deliberate, narrow exception to the "no CSV/data files" repository check. Filled-in logs stay in the team's private folder unless the owner approves a pull request.

Status edits outside the marked blocks (applied by `_staging_tools/apply_d37.js`, outside the repository; each replacement matched exactly once):

| File | Change |
|---|---|
| `PROJECT_STATUS.md` | As-of date; registration row (submitted 25 Oct 2026, owner-confirmed, committee acceptance pending); new proposal Sprint 0 row; collaborator row (§6); next step 1 |
| `README.md` | Status date and registration row; new proposal Sprint 0 row; repository-map entries for D-37 and `docs/proposal/`; form-fields map wording |
| `docs/README.md` | Form-fields index wording; index entries for D-37 and `docs/proposal/` |
| `docs/REGISTRATION_FORM_FIELDS.md` | Heading and repository-note status line, **outside** the amended block (the block and the field boxes are byte-identical, so their hashes are unchanged) |
| `AGENTS.md` | §2 registration line; §5 next decision is D-38 |
| `CLAUDE.md` | Current-stage reminder |
| `CONTRIBUTING.md` | Current-stage note |
| `PROJECT_EVOLUTION.md` | Timeline row and decision-index row for D-37; next decision is D-38 |

`AGENTS.md`, `CLAUDE.md` and `CONTRIBUTING.md` are protected governance documents ([CONTRIBUTING.md §6](../CONTRIBUTING.md#6-code-review)). Only their stale status wording was changed, at the owner's request. The pull request is owner-authored and still needs another collaborator's approval.

## 6. Observed GitHub state (read 25 Oct 2026)

`main` is at `4012dac` (unchanged since D-36). Collaborators: owner `Amr-Heibaa` (admin) and `sayeddabdou`, `selimmmm7`, `abdallahjr111`, `GeorgeBassem-dev` (write). The `GeorgeBassem-dev` invitation recorded as pending in D-34 has been accepted, and there are no pending invitations. D-34 is kept unchanged as history. Nothing about collaborators or settings was changed by D-37.

## 7. Explicit exclusions

- No application code, database, dataset, recording, model selection or experiment.
- No change to the V3.1 scope, the title, the registration Abstract, the v6 diagram, the specification, the architecture, the dataset strategy or the evaluation plan.
- No literature search, screening, PRISMA count, quality score, table value or paper text was produced. The protocol and matrix files are drafts and templates.
- No university template, private Overleaf link, instructor transcript, downloaded paper, e-mail address or Jira account identifier was committed.
- No Jira sprint was created, started, re-dated or closed, and no existing Jira item was edited or deleted.

## 8. Remaining risks and open items

1. **Committee acceptance** of the expanded scope is still pending (Q12).
2. **Compressed schedule:** S0-14 to S0-18 fall between 6 and 8 Nov; the 9 Nov buffer is the only slack.
3. **Evidence scarcity:** peer-reviewed evidence on Egyptian-Arabic spoken database querying may be thin; it must be reported honestly.
4. **Database access** through MIU / the EKB must be confirmed before the protocol lists a source.
5. **GitHub handles** for Sayed and George are not yet independently verified; the owner should confirm them.
6. **Sample Jira items** `SCRUM-1` to `SCRUM-4` remain; the owner may delete them separately.
7. **Verification tool:** the D-36 suite expects "NOT SUBMITTED" in README, PROJECT_STATUS and AGENTS and forbids every CSV file. A D-37 copy of the suite (outside the repository) changes only those expectations; see the pull request for both results.
8. Carried over from D-36: the GitHub repository description still uses the earlier title; no branch-protection enforcement test has been performed; licensing is undecided.
