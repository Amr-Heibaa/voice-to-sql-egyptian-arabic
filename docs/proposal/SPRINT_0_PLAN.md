# Sprint 0 Plan — Academic Proposal Research and Documentation

> **SUPERSEDED by D-38 (25 Oct 2026). Historical record only.** This D-37 plan used the old Jira project `SCRUM`, which is **no longer authoritative**. Current Sprint 0 coordination (three deliverables, Jira project `CQP`, Workstream `CQP-1`) is in [../SPRINT_0.md](../SPRINT_0.md) and [../CHANGE_RECORD_D-38.md](../CHANGE_RECORD_D-38.md). Do not use the task IDs, links, owners or dates below for current work. The text below is unchanged from D-37.

| Item | Value |
|---|---|
| Jira project | **ClearQuery** (key `SCRUM`), team Scrum board |
| Sprint | `SCRUM Sprint 0`, **active** since 25 Oct 2026, ends 8 Nov 2026 (dates unchanged) |
| Epic | [SCRUM-5](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-5) — ClearQuery Proposal — Systematic Literature Review & Proposed Solution |
| Execution window | 26 Oct – 8 Nov 2026; 9 Nov is the internal buffer; the Proposal Discussion period starts 10 Nov 2026 |
| Out of scope | Implementing ClearQuery, generating datasets, recording speech, running experiments, starting Sprint 1 |
| Recorded by | Decision D-37 ([../CHANGE_RECORD_D-37.md](../CHANGE_RECORD_D-37.md)) |

> Jira is private to the team: the links below need a signed-in team account. Each Jira task holds the full execution package (overview, references, step-by-step instructions, a copy-and-paste AI prompt, deliverables, acceptance criteria, reviewer and dependencies). The prompts are kept only in Jira.

## 1. Sprint goal

Produce an evidence-based, academically defensible ClearQuery graduation proposal through a structured Systematic Literature Review, five Research Questions, verified research gaps, and a detailed Proposed Solution aligned with the university's official requirements.

## 2. Team

| Member | Main responsibility | GitHub handle |
|---|---|---|
| Amr | Project Lead; RQ5, Proposed Solution, architecture, final integration and readiness | `Amr-Heibaa` (repository owner) |
| Sayed | RQ1, SLR search protocol, state-of-the-art synthesis, Discussion | Pending owner confirmation |
| Abdelrahman | RQ2, AI methods, data extraction, quality assessment, QA coordination | `selimmmm7` |
| George | RQ3, existing tools, IEEE formatting and integration, Tables II–III | Pending owner confirmation |
| Abdallah | RQ4, study selection and PRISMA, research gaps, Threats to Validity | `abdallahjr111` |

Every Jira assignee was resolved to a unique, active project member account before assignment. Private identifiers (e-mail addresses, Jira account IDs) are deliberately not recorded in this public repository. GitHub handles are listed only where they were independently verified; the others wait for the owner's confirmation.

## 3. Status of existing Jira items

`SCRUM-1`, `SCRUM-2`, `SCRUM-3` and `SCRUM-4` existed before this plan. They have generic titles and empty descriptions and look like onboarding samples, but that was not confirmed. They were **left untouched**; the owner may remove them separately. `SCRUM Sprint 1` (future, empty) was also left untouched.

## 4. Jira task index

All tasks were created as **To Do** in `SCRUM Sprint 0`, as children of the Epic [SCRUM-5](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-5).

| ID | Jira | Task | Owner | Reviewer | Priority | Target | RQ / section |
|---|---|---|---|---|---|---|---|
| S0-01 | [SCRUM-6](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-6) | Finalize Research Questions and Scope Traceability | Amr | Sayed | Highest | 26 Oct | RQ1–RQ5 |
| S0-02 | [SCRUM-7](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-7) | Define Systematic Literature Review Protocol | Sayed | Abdallah | Highest | 27 Oct | II |
| S0-03 | [SCRUM-8](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-8) | Conduct Study Selection and Prepare PRISMA Evidence | Abdallah | Abdelrahman | Highest | 2 Nov | II, PRISMA |
| S0-04 | [SCRUM-9](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-9) | Establish Data Extraction and Quality Assessment | Abdelrahman | Abdallah | Highest | 2 Nov | II |
| S0-05 | [SCRUM-10](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-10) | Research and Synthesize RQ1: State of the Art | Sayed | Abdelrahman | High | 3 Nov | RQ1, III-A |
| S0-06 | [SCRUM-11](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-11) | Research and Synthesize RQ2: AI Methods | Abdelrahman | Sayed | High | 3 Nov | RQ2, III-B |
| S0-07 | [SCRUM-12](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-12) | Research RQ3: Existing Tools and Market Landscape | George | Amr | High | 3 Nov | RQ3, III-C, VI-E |
| S0-08 | [SCRUM-13](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-13) | Research RQ4: Gaps and Challenges | Abdallah | Amr | Highest | 4 Nov | RQ4, III-D |
| S0-09 | [SCRUM-14](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-14) | RQ5: Map Research Gaps to Proposed Design | Amr | Abdallah | Highest | 5 Nov | RQ5 |
| S0-10 | [SCRUM-15](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-15) | Complete Table I: Data Extraction | Abdelrahman | George | High | 4 Nov | Table I |
| S0-11 | [SCRUM-16](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-16) | Complete Tables II and III | George | Abdallah | High | 4 Nov | Tables II–III |
| S0-12 | [SCRUM-17](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-17) | Write Discussion and Conceptual Framework | Sayed | Abdelrahman | Medium | 5 Nov | IV |
| S0-13 | [SCRUM-18](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-18) | Document Threats to Validity | Abdallah | Sayed | Medium | 5 Nov | V |
| S0-14 | [SCRUM-19](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-19) | Develop Detailed Proposed Solution | Amr | Abdelrahman | Highest | 6 Nov | RQ5, VI |
| S0-15 | [SCRUM-20](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-20) | Write Introduction, Abstract and Conclusion | Amr | Sayed | High | 7 Nov | Abstract, I, VII |
| S0-16 | [SCRUM-21](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-21) | IEEE Formatting and Document Integration | George | Amr | High | 7 Nov | Whole paper |
| S0-17 | [SCRUM-22](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-22) | Independent Cross-Review and Academic QA | Abdelrahman (coordinator) | Amr accepts the QA report | High | 8 Nov | Whole paper |
| S0-18 | [SCRUM-23](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-23) | Final Proposal Readiness Review | Amr | George (independent check) + team sign-off | Highest | 8 Nov | Whole paper |

**QA review subtasks under S0-17.** Each member reviews sections they did not write. Subtasks in this project have no Priority or Due date field, so their target date (8 Nov) is stated in the description.

| ID | Jira | Reviewer | Sections reviewed |
|---|---|---|---|
| S0-17a | [SCRUM-24](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-24) | Amr | RQ3, RQ4, Discussion and conceptual framework |
| S0-17b | [SCRUM-25](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-25) | Sayed | Proposed Solution with RQ5; Threats to Validity |
| S0-17c | [SCRUM-26](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-26) | Abdelrahman | Protocol and PRISMA; RQ1; architecture fidelity of VI-C |
| S0-17d | [SCRUM-27](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-27) | George | Abstract, Introduction, Conclusion; number and terminology consistency |
| S0-17e | [SCRUM-28](https://miuegypt-team-e0iuh5ol.atlassian.net/browse/SCRUM-28) | Abdallah | RQ2; Tables I–III |

**Reviewer field.** The project has no native Reviewer field, so each reviewer is named in the task description (header and §7) and, for the final QA, in the subtasks above.

## 5. Dependencies

Recorded in Jira as **Blocks** links (38 links). They are logical dependencies, so research and writing may overlap.

**Critical path:** S0-01 → S0-02 → S0-03 → S0-04 → S0-05 / S0-06 → S0-08 → S0-09 → S0-14 → S0-15 → S0-16 → S0-17 → S0-18.

| Task | Blocked by |
|---|---|
| S0-02 | S0-01 |
| S0-03 | S0-02 |
| S0-04 | S0-02, S0-03 |
| S0-05, S0-06 | S0-03, S0-04 |
| S0-07 | S0-01 |
| S0-08 | S0-04, S0-05, S0-06, S0-07 |
| S0-09 | S0-06, S0-07, S0-08 |
| S0-10, S0-13 | S0-03, S0-04 |
| S0-11 | S0-02, S0-03, S0-04 |
| S0-12 | S0-05, S0-06, S0-07, S0-08 |
| S0-14 | S0-07, S0-09 |
| S0-15 | S0-01, S0-12, S0-14 |
| S0-16 | S0-10, S0-11, S0-14, S0-15 |
| S0-17 | S0-16 |
| S0-18 | S0-17 |

S0-03 and S0-04 also run in parallel: extraction starts as studies are included, and any quality-based exclusion feeds back into the PRISMA diagram.

## 6. Workload and risks

| Member | Owns | Reviews | Note |
|---|---|---|---|
| Amr | 5 tasks (S0-01, S0-09, S0-14, S0-15, S0-18) | S0-07, S0-08, S0-16, S0-17 report, S0-17a | **Heaviest load** and on the critical path (S0-09 → S0-14 → S0-15 → S0-18). Start the architecture text from the spec before the gap matrix is final |
| Abdelrahman | 4 tasks (S0-04, S0-06, S0-10, S0-17) | S0-03, S0-05, S0-12, S0-14, S0-17c | **Heavy load**. Each RQ owner extracts their own papers; Abdelrahman sets the standard and checks consistency |
| Sayed | 3 tasks (S0-02, S0-05, S0-12) | S0-01, S0-06, S0-13, S0-15, S0-17b | S0-02 is due first (27 Oct) and gates all searching |
| Abdallah | 3 tasks (S0-03, S0-08, S0-13) | S0-02, S0-04, S0-09, S0-11, S0-17e | S0-03 has a large, uncertain screening effort |
| George | 3 tasks (S0-07, S0-11, S0-16) | S0-10, S0-18, S0-17d | S0-16 has a one-day integration window (7 Nov) |

Other risks:

- **Compressed tail.** S0-14 to S0-18 fall between 6 and 8 Nov. Integrate sections as soon as each is reviewed.
- **Database access.** The protocol must list only databases the team can actually reach through MIU or the EKB.
- **Scarce Egyptian-Arabic evidence.** Report scarcity honestly; never stretch MSA or English evidence.
- **Tool documentation changes.** Record access dates for RQ3 sources.
- **Committee acceptance.** Acceptance of the expanded scope is still not confirmed; present it honestly in the discussion.

No story points or velocity were estimated.

## 7. Definition of Done

The proposal effort is ready only when:

- [ ] The RQs are reviewed and agreed.
- [ ] The research search protocol is documented.
- [ ] Actual searches and inclusion/exclusion decisions are recorded.
- [ ] Included studies are genuine and traceable.
- [ ] PRISMA counts are accurate.
- [ ] Quality assessments are justified.
- [ ] All three required tables are completed.
- [ ] RQ1–RQ5 are clearly addressed.
- [ ] Research gaps are supported by evidence.
- [ ] The Proposed Solution responds to those gaps.
- [ ] The architecture is consistent with approved V3.1.
- [ ] IEEE references are verifiable.
- [ ] The document is integrated and reviewed.
- [ ] No research findings or experiments are fabricated.
- [ ] The project owner approves the final document.

None of these items is complete. Creating the Jira tasks and this plan does not complete any of them.
