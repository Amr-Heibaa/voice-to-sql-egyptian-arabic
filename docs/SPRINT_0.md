# Sprint 0 — Proposal Discussion Readiness (Jira CQP)

**Current plan since D-38 (25 Oct 2026), revised by D-39 (27 Oct 2026).** This file is the repository's **index** to Sprint 0. The detailed steps of each task live **only in Jira**, inside each issue. Since D-39 the Proposal Document tasks follow the university template and the lecture guide section by section, and no issue contains a ready-made AI prompt. When this file and a Jira issue disagree on the details of a task, the Jira issue wins; report the difference so this index can be corrected.

| Item | Value |
|---|---|
| Jira project | **ClearQuery - Graduation Project**, key **`CQP`** (Business / Project Management project on the team's Jira site) |
| Workstream | **`CQP-1` — Sprint 0: Proposal Discussion Readiness** |
| What "Sprint 0" means here | A label for the `CQP-1` Workstream. It is **not** a native Scrum sprint, and the task titles are the team's internal work breakdown, not official university task names |
| Work items | 25 main Tasks (`CQP-2` to `CQP-26`), 5 independent QA Sub-tasks (`CQP-27` to `CQP-31`), 18 hard **Blocks** dependency links |
| Status | All 31 issues **To Do** (27 Oct 2026) |
| Superseded plan | The D-37 plan in the old `SCRUM` project ([proposal/SPRINT_0_PLAN.md](proposal/SPRINT_0_PLAN.md)) is **historical only** |

> **Access.** Jira is private to the team. Sign in with your team account and open the project with key `CQP`; search an issue by its key (for example `CQP-12`). The site address is shared privately by Amr and is deliberately not published in this public repository.

## 1. The three university deliverables

Owner-provided summary of the university's requirements for the first Proposal Discussion (official e-mails received 25 Oct 2026, the university proposal template and the instructional session; the university material itself is private and not in this repository).

| # | Deliverable | Jira | Guide in this repository |
|---|---|---|---|
| 1 | **Proposal Document**: an IEEE-style Systematic Literature Review (SLR) with RQ1–RQ5 that leads to an evidence-based Proposed Solution | `CQP-2` … `CQP-16` | [proposal/README.md](proposal/README.md) |
| 2 | **Presentation**: exactly **15 prescribed slides in English**, followed by the live demo | `CQP-17` … `CQP-21` | [presentation/README.md](presentation/README.md) |
| 3 | **10% Implementation / Proof of Concept (PoC)**: a minimal **working** prototype that demonstrates the core idea | `CQP-22` … `CQP-26` | [poc/POC_KICKOFF.md](poc/POC_KICKOFF.md) |

Independent QA for all three: `CQP-27` … `CQP-31`. The presentation and the whole discussion are in **English**, and **formal attire** is required.

The university gave **no feature checklist and no formula for "10%"**. The PoC boundary in [poc/POC_KICKOFF.md](poc/POC_KICKOFF.md) is the team's engineering proposal, pending supervisor confirmation.

## 2. Milestones

The Proposal Discussion **period** begins on **10 Nov 2026** (the start of the period, not necessarily our group's slot). Every other date below is an **internal target**, not a university deadline.

| Date | Internal checkpoint |
|---|---|
| 26–28 Oct | The five RQs (`CQP-2`, 27 Oct); criteria, databases and search strings, shown to the supervisor before searching (`CQP-3`); recording sheet and screening rules (`CQP-6`); extraction columns and quality checklist (`CQP-4`); Overleaf setup (`CQP-5`); PoC scope and **Interface Contract** (`CQP-22` Phase A). Amr creates the University Drive folder |
| **28 Oct** | **Gate G-A**: PoC Interface Contract v1.0 frozen when all four component owners comment "Contract v1.0 agreed" on `CQP-22` |
| 29 Oct – 1 Nov | Searches and screening (titles, abstracts, full texts) with quality scores (`CQP-12`); PoC components built against the contract; early slides |
| **1 Nov** | **Corpus freeze**: the list of included papers is fixed and PRISMA is final (`CQP-12`); Section III is written only from this list. **Checkpoint C1**: text-only walking skeleton through real components (typed Arabic → minimal BIR/policy → guard → seeded DB → rows) |
| 2–4 Nov | Table I (`CQP-13`, 2 Nov); Tables II and III (`CQP-14`, 3 Nov); Results RQ1–RQ4 (`CQP-7` … `CQP-10`) and Section V (`CQP-12`), 4 Nov; Introduction draft (`CQP-15`, 4 Nov) |
| 4–7 Nov | Short RQ5 answer and VI-B inputs (`CQP-11`, 5 Nov); Proposed Solution (`CQP-16`, 6 Nov); Discussion, Conclusion and Abstract (`CQP-15`); PoC Phase B integration (4–7 Nov); slide drafting |
| **8 Nov** | **Internal completion target**: integrated document with its final review (`CQP-15`), complete deck, integrated PoC, independent QA done |
| 9 Nov | Full English rehearsal, live-demo and venue-network test, contingency checks, formal-attire confirmation |
| **10 Nov** | University Proposal Discussion period begins |

## 3. Team and where each member starts

Assignments as read from Jira on 25 Oct 2026 (first names only; no e-mail addresses or account IDs are recorded here).

| Member | Role | Document | Presentation | PoC | QA reviewer of |
|---|---|---|---|---|---|
| **Amr** | Project Lead | `CQP-2`, `CQP-11`, `CQP-16` | `CQP-17` | `CQP-22` | `CQP-27` |
| **Sayed** | SLR protocol, RQ1, academic writing | `CQP-3`, `CQP-7`, `CQP-15` | `CQP-18` | `CQP-23` | `CQP-28` |
| **Abdelrahman** | RQ2, AI methods, data extraction | `CQP-4`, `CQP-8`, `CQP-13` | `CQP-19` | `CQP-24` | `CQP-29` |
| **George** | RQ3, tools/market, IEEE formatting, deck integration | `CQP-5`, `CQP-9`, `CQP-14` | `CQP-20` | `CQP-25` | `CQP-30` |
| **Abdallah** | RQ4, screening/PRISMA, Threats to Validity | `CQP-6`, `CQP-10`, `CQP-12` | `CQP-21` | `CQP-26` | `CQP-31` |

**First task for each member** (the earliest due item that nothing blocks): Amr `CQP-2` and `CQP-22` Phase A; Sayed `CQP-3`; Abdelrahman `CQP-4`; George `CQP-5`; Abdallah `CQP-6`. All component owners (Sayed, Abdelrahman, George, Abdallah) must also review the draft PoC contract before Gate G-A.

## 4. Task map

Titles and targets as in Jira on 27 Oct 2026 (D-39). Planning IDs (`S0-DOC-01` …) are the prefixes used in the Jira titles. The order of work for the document is the order in §2 and in `CQP-1`, which is also the order of the Jira list.

### 4.1 Proposal Document (`CQP-2` … `CQP-16`)

| Jira | Planning ID | Task | Owner | Template part it produces | Internal target |
|---|---|---|---|---|---|
| `CQP-2` | S0-DOC-01 | Research Questions, Scope and Research Objectives | Amr | The five RQs with the template labels, and the objectives (Section I) | 27 Oct |
| `CQP-3` | S0-DOC-02 | Systematic Literature Review Protocol | Sayed | Criteria, databases and search strings, shown to the supervisor; Sections II (opening), II-A, II-B | 28 Oct |
| `CQP-4` | S0-DOC-03 | Data Extraction and Study Quality Framework | Abdelrahman | Extraction columns and the template quality checklist; Sections II-D, II-E | 28 Oct |
| `CQP-5` | S0-DOC-04 | IEEE Proposal Structure and Reference Framework | George | Cover, header, numbering, Acknowledgments and the shared .bib file in Overleaf | 28 Oct |
| `CQP-6` | S0-DOC-05 | Screening and PRISMA Protocol | Abdallah | Recording sheet (search log and papers), screening rules, PRISMA boxes (II-C, Fig. 1) | 28 Oct |
| `CQP-7` | S0-DOC-06 | RQ1: State-of-the-Art Literature Synthesis | Sayed | Section III-A | 4 Nov |
| `CQP-8` | S0-DOC-07 | RQ2: AI Methods and Technical Approaches | Abdelrahman | Section III-B | 4 Nov |
| `CQP-9` | S0-DOC-08 | RQ3: Commercial and Open-Source Tools | George | Section III-C | 4 Nov |
| `CQP-10` | S0-DOC-09 | RQ4: Research Gaps and Biases | Abdallah | Section III-D | 4 Nov |
| `CQP-11` | S0-DOC-10 | RQ5: Short Answer (III-E) and Inputs for VI-B | Amr | Section III-E and the three VI-B lists | 5 Nov |
| `CQP-12` | S0-DOC-11 | Study Selection, PRISMA and Threats to Validity | Abdallah | Searches and screening, Fig. 1 PRISMA (final 1 Nov), Section V | 4 Nov |
| `CQP-13` | S0-DOC-12 | Complete Data Extraction Table I and Quality Assessment | Abdelrahman | Quality scores and Table I (II-F) | 2 Nov |
| `CQP-14` | S0-DOC-13 | Tables II and III | George | Tables II and III (II-G, II-H) | 3 Nov |
| `CQP-15` | S0-DOC-14 | Introduction, Discussion, Conclusion, Abstract and Final Review | Sayed (George: Abstract draft and final review) | Abstract, Index Terms, Sections I, IV and VII, and the final review of the whole document | 8 Nov |
| `CQP-16` | S0-DOC-15 | Proposed Solution (Section VI) | Amr | Section VI with the template headings A–E; Fig. 2 is the approved System Overview v6 | 6 Nov |

### 4.2 Presentation (`CQP-17` … `CQP-21`)

| Jira | Planning ID | Slides | Owner | Expected deliverable | Internal target |
|---|---|---|---|---|---|
| `CQP-17` | S0-PRES-01 | 3, 4, 12, 14 | Amr | Problem, Objectives, Architecture and Contributions slides with English notes | 7 Nov |
| `CQP-18` | S0-PRES-02 | 2, 5, 7, 15 | Sayed | Motivation, Research Questions, State of the Art and Conclusion slides | 7 Nov |
| `CQP-19` | S0-PRES-03 | 6, 8, 13 | Abdelrahman | Evidence synthesis, AI Methods and Evaluation slides | 7 Nov |
| `CQP-20` | S0-PRES-04 | 1, 9 + integration | George | Title and Market slides; the integrated 15-slide deck | 8 Nov |
| `CQP-21` | S0-PRES-05 | 10, 11 + defense | Abdallah | Gaps and Proposed Directions slides; Q&A and readiness preparation | 8 Nov |

### 4.3 Proof of Concept (`CQP-22` … `CQP-26`)

| Jira | Planning ID | Component | Owner | Expected deliverable | Internal target |
|---|---|---|---|---|---|
| `CQP-22` | S0-POC-01 | Architecture, Interface Contract, integration and demo readiness | Amr | Phase A: PoC scope + Interface Contract v1.0 (Gate G-A, 28 Oct); C1 skeleton (1 Nov); Phase B: integrated demo, runbook, test matrix, limitations | 7 Nov |
| `CQP-23` | S0-POC-02 | Voice input, ASR, editable transcript and Arabic-to-English translation | Sayed | Working voice/transcript/translation component and its tests | 4 Nov |
| `CQP-24` | S0-POC-03 | Business Intent Representation, ambiguity and selective answering | Abdelrahman | Minimal BIR, mini Sales catalog, Answer/Clarify/Abstain policy and tests | 5 Nov |
| `CQP-25` | S0-POC-04 | Lightweight interactive interface | George | Demo UI over the real backend | 6 Nov |
| `CQP-26` | S0-POC-05 | Synthetic Sales data, SQL guard and read-only execution | Abdallah | Seeded synthetic Sales DB, guard, read-only execution and safety tests | 4 Nov |

### 4.4 Independent QA (`CQP-27` … `CQP-31`)

No one reviews their own work.

| Jira | Planning ID | Reviewer | Reviews | Parent |
|---|---|---|---|---|
| `CQP-27` | S0-QA-01 | Amr | Tool sources in III-C and Slide 9 (George); SQL-guard tests (Abdallah) | `CQP-9` |
| `CQP-28` | S0-QA-02 | Sayed | III-B and Slide 8: speech, Arabic language and translation claims (Abdelrahman) | `CQP-8` |
| `CQP-29` | S0-QA-03 | Abdelrahman | III-A and Slide 7: references and numbers (Sayed) | `CQP-7` |
| `CQP-30` | S0-QA-04 | George | Section VI, Slides 12 and 14, clean-start demo re-run (Amr) | `CQP-16` |
| `CQP-31` | S0-QA-05 | Abdallah | Sections II, II-A, II-B reproducibility (Sayed); III-E and VI-B link back to Section III (Amr) | `CQP-3` |

## 5. Dependencies and gates

**18 Blocks links** (read back 25 Oct 2026):

| Blocked task | Blocked by |
|---|---|
| `CQP-11` RQ5 short answer and VI-B inputs | `CQP-10` |
| `CQP-12` Selection, PRISMA, Threats | `CQP-3`, `CQP-6` |
| `CQP-13` Table I | `CQP-4` |
| `CQP-14` Tables II/III | `CQP-12` |
| `CQP-15` Intro, Abstract, Discussion, Conclusion | `CQP-7`, `CQP-8`, `CQP-9`, `CQP-10` |
| `CQP-16` Proposed Solution | `CQP-11` |
| `CQP-20` Deck integration | `CQP-17`, `CQP-18`, `CQP-19`, `CQP-21` |
| `CQP-22` **Phase B only** | `CQP-23`, `CQP-24`, `CQP-25`, `CQP-26` |

**Gates that are not Jira links** (a link would create a cycle):

- **G-A (28 Oct):** Interface Contract v1.0 frozen in `CQP-22` Phase A. Component implementation in `CQP-23` … `CQP-26` follows the frozen contract. Exploratory spikes (for example, trying ASR models) may start earlier.
- **C1 (1 Nov):** text-only walking skeleton.
- **Corpus freeze (1 Nov):** the list of included papers is fixed in `CQP-12`; Section III cites only papers on this list.

## 6. How to use your Jira issue

1. Open your issue by key. Read **all** of it: the part of the template it produces, the steps and "Done when".
2. Read the same part of the university template and of the lecture guide. Use the sample document as an example of form and length only; the guide lists what not to copy from it. The team's private Proposal map page explains every part of the template and links it to its task (link shared privately).
3. Check the **Blocks** links and gates. If an input you need is not ready, comment on the producing issue instead of guessing.
4. No issue contains a ready-made AI prompt. If you use an AI tool, brief it yourself from your issue and the template, and correct it when you find a mistake. Never paste secrets, private university material links, personal data or restricted datasets into an AI tool. Treat AI output as a draft: check every claim, citation and number yourself.
5. Put the artifact where the issue says (University Drive folder, private Overleaf project or a pull request to this repository; see [TEAM_START_HERE.md](TEAM_START_HERE.md#6-where-things-go-public-vs-private)).
6. Post a comment on your issue with the link, version and date, and @mention the people who consume it. Then move the issue status yourself.
