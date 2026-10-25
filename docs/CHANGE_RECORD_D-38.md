# Change Record D-38 — Align ClearQuery Repository with Current CQP Sprint 0 and Proposal Discussion Requirements

| Field | Value |
|---|---|
| Decision | **D-38** |
| Date | 2026-10-25 |
| Authorized by | The project owner (`Amr-Heibaa`), in the "GitHub team readiness and project onboarding" instruction of 25 Oct 2026. It asked for this documentation on a feature branch through a **draft** pull request, with no merge, no Jira change and no repository-setting change |
| Supersedes | **D-37 for current Sprint 0 coordination only.** D-37 stays an accurate historical record and is not edited ([CHANGE_RECORD_D-37.md](CHANGE_RECORD_D-37.md)) |
| Impact | Planning, status and onboarding documentation only. The title, the registration Abstract and the other submitted field text, the specification, the architecture, the dataset strategy, the evaluation plan (including the P2 and P4 definitions) and the v6 diagram are unchanged. Nothing is implemented |

## 1. Why D-37 is superseded for current planning

D-37 organised the proposal paper in the old Jira project `SCRUM` (Epic `SCRUM-5`, 18 tasks, 5 QA subtasks, 38 links). After D-37 was merged (pull request #3, merge commit `bff21b4`), the owner moved Sprint 0 to a new Business / Project Management Jira project and widened it from the paper alone to **all three** university deliverables for the first Proposal Discussion. The `SCRUM` plan is therefore **not authoritative** for current work. Its documents are kept and labelled as history.

## 2. Current Jira structure (read-only check, 25 Oct 2026)

| Item | Observed |
|---|---|
| Project | **ClearQuery - Graduation Project**, key `CQP`, Business / Project Management type |
| Workstream | `CQP-1` — Sprint 0: Proposal Discussion Readiness (a Workstream label, not a native Scrum sprint) |
| Tasks | 25: `CQP-2`–`CQP-16` Document, `CQP-17`–`CQP-21` Presentation, `CQP-22`–`CQP-26` Proof of Concept; all children of `CQP-1` |
| QA sub-tasks | 5: `CQP-27`–`CQP-31` (parents `CQP-9`, `CQP-8`, `CQP-7`, `CQP-16`, `CQP-3`), one reviewer each, no self-review |
| Dependencies | 18 **Blocks** links, matching the owner's plan; gates G-A (28 Oct) and C1 (1 Nov) recorded in `CQP-22` as gates, not links |
| Status | All 31 issues **To Do** |
| Assignees | Match the ownership in the owner's instruction (first names in [SPRINT_0.md](SPRINT_0.md#3-team-and-where-each-member-starts)) |

The check was **read-only**: no Jira issue, link, field, comment or status was created or changed. No older Jira site was queried. Site address, e-mail addresses and account IDs are deliberately not recorded in this public repository; issues are referenced by key only.

## 3. Three mandatory university deliverables

Owner-provided summary of the university's requirements for the first Proposal Discussion (period begins **10 Nov 2026**): (1) the Proposal Document (IEEE-style SLR with RQ1–RQ5 leading to a Proposed Solution); (2) a mandatory **15-slide** presentation in **English**, followed by the live demo, with formal attire; (3) a minimal **working** 10% implementation / Proof of Concept. The university gave no feature checklist or formula for "10%"; the PoC boundary in [poc/POC_KICKOFF.md](poc/POC_KICKOFF.md) is the team's engineering proposal pending supervisor confirmation.

## 4. Team responsibilities

| Member | Responsibilities | GitHub |
|---|---|---|
| Amr | Project Lead: RQ and scope coordination, RQ5 and Proposed Solution, architecture consistency, PoC integration, final approval | `Amr-Heibaa` (owner) |
| Sayed | SLR protocol, RQ1, academic writing, voice/ASR/translation component | Pending owner confirmation (`sayeddabdou` is an active collaborator) |
| Abdelrahman | RQ2, AI methods, data extraction, BIR, ambiguity detection and Answer/Clarify/Abstain | `selimmmm7` |
| George | RQ3, tools and market, academic formatting, deck integration, PoC user interface | Pending owner confirmation (`GeorgeBassem-dev` is an active collaborator) |
| Abdallah | RQ4, research gaps, PRISMA, Threats to Validity, synthetic Sales database, SQL validation and read-only query layer | `abdallahjr111` |

Collaborators re-read on 25 Oct 2026: owner `Amr-Heibaa` (admin); `sayeddabdou`, `selimmmm7`, `GeorgeBassem-dev`, `abdallahjr111` (write); no pending invitations. Unchanged since D-37; no permission was changed.

## 5. Status and approval distinctions

| Category | Item |
|---|---|
| Confirmed by the owner | Registration form submitted 25 Oct 2026; University Drive chosen as the private workspace |
| Approved earlier | Title (TA, D-33); v6 diagram (team and supervisor); V3.1 scope (team) |
| Pending | Committee approval of the expanded scope (Q12); supervisor confirmation of the PoC scope; Interface Contract v1.0 (Gate G-A); University Drive folder and access; GitHub handles of Sayed and George; PoC code location |
| Not started / not completed | Proposal research and writing, slides, PoC implementation, datasets, recordings, evaluation |
| Internal targets, not university deadlines | 28 Oct G-A, 1 Nov C1, 8 Nov completion, 9 Nov rehearsal |

## 6. PoC readiness boundary and public/private separation

- The PoC is **planned, not implemented**. The kickoff guide and the interface contract are planning documents; the contract is a **draft v0.1** that becomes v1.0 only at Gate G-A on `CQP-22`.
- Where PoC code lives is an **open owner decision** (S0-D1 in [PROJECT_STATUS.md](../PROJECT_STATUS.md#4-open-decisions-from-specificationmd-22)). `CQP-1` currently plans a private code repository; no repository was created by this decision.
- Public repository: approved documentation, onboarding, status, public-safe contracts. Private: Jira `CQP` (tasks and AI prompts), University Drive (research artifacts, decks, PoC evidence), private Overleaf (template and manuscript). The detailed AI prompts were **not** copied here.

## 7. Repository changes

New files:

| File | Purpose |
|---|---|
| `docs/TEAM_START_HERE.md` | Onboarding: project summary, approved vs pending, reading order, where each member starts, task loop, handoff examples, public vs private, AI agent handoff prompt, next actions |
| `docs/SPRINT_0.md` | Current Sprint 0 index: deliverables, milestones, team, task map for all 30 work items, dependencies, gates, how to use a Jira issue |
| `docs/presentation/README.md` | The 15 prescribed slides, owners, production steps, review checklist |
| `docs/poc/POC_KICKOFF.md` | Proposed PoC scope (MoSCoW), scenarios A/B/C, safety layers, integrity rules, component owners, timeline, decisions to make |
| `docs/poc/INTERFACE_CONTRACT_DRAFT.md` | Draft interface contract v0.1 for Gate G-A |
| `docs/CHANGE_RECORD_D-38.md` | This record |

Edited files (exact replacements outside the marked blocks, applied by `_staging_tools/apply_d38.js` with the edit list `_staging_tools/d38_edits.js`, both outside the repository; each old string matched exactly once):

| File | Change |
|---|---|
| `README.md` | Status rows for Sprint 0 and the three deliverables; new "Start here" section (milestone, deliverables, Jira, workflow); public-repository notice; repository-map rows |
| `PROJECT_STATUS.md` | Sprint 0 row (CQP), superseded D-37 row, University Drive row, PoC note in the implementation row, collaborator re-read note, Sprint 0 open decisions S0-D1–S0-D7, milestones in next steps |
| `PROJECT_EVOLUTION.md` | Timeline row and decision-index row for D-38; next decision D-39 |
| `AGENTS.md` | Reading order (instructions, status, onboarding, spec, architecture, Jira task, contribution rules); current-milestone line; next decision D-39; rules on identities and on reporting changed files and checks |
| `CLAUDE.md` | Current-stage reminder; pointer to the onboarding page |
| `CONTRIBUTING.md` | Current-stage note; workflow steps (read the Jira issue first, safe update of `main`, owner merge authorization); Jira key in branch names; Jira key and real check output in PR descriptions |
| `.github/pull_request_template.md` | Jira issue field; changed files and deliverables; known limitations; owner merge authorization section (no checkbox) |
| `docs/README.md` | Index rows for the new documents and D-38 |
| `docs/proposal/README.md` | Deliverable 1 framing; milestones and navigation point to `docs/SPRINT_0.md`; University Drive; new document workflow table |
| `docs/proposal/PROPOSAL_REQUIREMENTS.md` | §4 and §5 owners re-mapped to CQP keys |
| `docs/proposal/RESEARCH_QUESTIONS.md`, `RQ_GAP_SOLUTION_MATRIX.md`, `SLR_PROTOCOL_DRAFT.md` | Task references re-mapped from S0-xx / old Jira `SCRUM` links (D-37) to CQP keys |
| `docs/proposal/SPRINT_0_PLAN.md` | "Superseded by D-38" banner only; the D-37 body is unchanged |

`AGENTS.md`, `CLAUDE.md`, `CONTRIBUTING.md` and `.github/` are protected governance documents ([CONTRIBUTING.md §6](../CONTRIBUTING.md#6-code-review)); they were changed at the owner's explicit request. The pull request is owner-authored and still needs another collaborator's approval.

Not changed: `docs/SPECIFICATION.md`, `docs/ARCHITECTURE.md`, `docs/DATASET_STRATEGY.md`, `docs/EVALUATION_PLAN.md`, `docs/REGISTRATION_FORM_FIELDS.md`, every earlier change record (D-31 to D-37), the v6 PNG, `.gitignore`, `.gitattributes`. No LICENSE, CODEOWNERS, workflow, code, data or CSV file was added.

## 8. Verification

GitHub state before the change (read 25 Oct 2026): remote `Amr-Heibaa/voice-to-sql-egyptian-arabic`, public, default branch `main`; `main` at `bff21b4b3e56f9b16e772380b8dafdcaa399f5ad`, the merge commit of pull request #3 (D-37, merged 25 Oct 2026 14:34 UTC after approval by another collaborator); local working tree clean; branch protection on `main` unchanged (one approval, administrators included, no required status checks); no GitHub Actions workflows.

The repository's verification suite lives outside the repository (it needs the private registration package) and was run on a copy of the tree without `.git`:

| Suite | Tree | Result |
|---|---|---|
| `verify_staging_d37.sh` (unchanged D-37 suite) | `main` at `bff21b4`, before any edit | 103 PASS, 0 FAIL |
| `verify_staging_d37.sh` (unchanged D-37 suite) | this branch | 103 PASS, 0 FAIL (270 internal links and anchors, 152 backticked paths checked) |
| `verify_staging_d38.sh` (D-37 suite plus sections 10–12) | this branch | 149 PASS, 0 FAIL |

The D-37 suite needed no change. The D-38 copy adds only new checks and weakens none:

- **Section 10:** the specification, architecture, dataset strategy, evaluation plan, registration fields, change records D-31 to D-37, the v6 PNG, `.gitignore` and `.gitattributes` are byte-identical to `main`.
- **Section 11:** the new documents exist; every key `CQP-1` to `CQP-31` appears in the task map; the slide and PoC owners match; all 15 official slide titles appear, with exactly 15 slide rows.
- **Section 12:** every `SCRUM` mention outside the D-37 history is labelled as superseded; old Jira links appear only in the D-37 history files; there are no links to the current Jira site, no Jira account IDs and no Drive or Overleaf links; the PoC is labelled not implemented and the contract a draft; the PoC code location is recorded as an open decision; the next decision is D-39.

No CI ran: none exists.

## 9. Outstanding decisions and recommendations

1. **PoC code location** (S0-D1): public repository or a private one. Owner decision.
2. **Supervisor confirmation** of the PoC scope (S0-D2).
3. **GitHub handles** of Sayed and George (S0-D5).
4. **University Drive** folder and access (S0-D6).
5. **Merge method:** `CONTRIBUTING.md` prescribes *Squash and merge*, but pull requests #1–#3 were merged with merge commits. Not changed here; the owner should pick one and, if wanted, restrict the allowed merge methods in the repository settings.
6. **CODEOWNERS** (not added): a single owner for every file would block owner-authored pull requests under the current one-approval rule. If wanted later, route only `docs/poc/` and future code paths to their component owners, without making code-owner review required until the team has tried it.
7. **CI** (not added): the existing verification suite needs the private registration package and therefore cannot run on GitHub Actions as is. A link-check-only workflow could be added later with read-only permissions; no required status check should be configured until a workflow has run successfully.
8. Carried over: committee acceptance (Q12); branch-protection enforcement test not performed; the GitHub repository description still shows the earlier title; licensing undecided.
