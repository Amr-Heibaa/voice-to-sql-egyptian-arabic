# Team Start Here — ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic

Welcome. This page is the onboarding path for the five team members and for any AI agent working with them. It links to the canonical files instead of repeating them.

## 1. ClearQuery in one minute

- **What it is:** an ambiguity-aware Voice-to-SQL system for **Egyptian Arabic**. It is an **AI Central Hub** for **one synthetic demonstration company** with three separately authorized workspaces: **Sales** (primary evaluation domain), **Inventory** and **HR**.
- **The problem:** managers ask business questions in Egyptian Arabic that can mean more than one thing. A technically valid SQL query can then return a confident but wrong business answer (a **silent semantic error**).
- **The idea:** turn each question into a **Business Intent Representation (BIR)** grounded in an approved business catalog, detect material ambiguity on the **original Arabic**, and choose **Answer / Clarify / Abstain** **before** any SQL is generated. Only an Answer produces guarded, **read-only** SQL, and every number comes from the database.
- **The pipeline** (canonical order: [SPECIFICATION.md §8.1](SPECIFICATION.md)): Egyptian-Arabic voice or text → speech recognition (voice only) → editable, user-confirmed Arabic transcript (`q_ar`, authoritative) → **BIR and ambiguity detection on the original Arabic** with the approved catalog → deterministic **Answer / Clarify / Abstain** → **only after ANSWER:** English Text-to-SQL from the Arabic-to-English translation (`q_en`) together with the resolved BIR (the BIR wins on conflict) → guarded, read-only execution. The translation runs in parallel, is derived and audited, and never resolves an ambiguity. Clarify and Abstain generate and execute no SQL.
- **A second mode:** **AI Schema Design**: the AI proposes relational schemas from incomplete requirements, with assumptions and open questions, for **Admin review**. DDL is preview only and is never executed automatically.
- **The research claim under test:** the ambiguity-aware BIR approach (**P4**) versus a strong clarification-enabled LLM baseline (**P2**). The exact definitions are in [SPECIFICATION.md §15.1](SPECIFICATION.md); **no results exist yet**.

## 2. What is approved and what is pending

| Item | State |
|---|---|
| Official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* | TA approved (D-33) |
| V3.1 scope and specification | Team-approved planning baseline |
| System Overview v6 diagram | Approved by the team and the academic supervisor; frozen |
| University registration form | Submitted 25 Oct 2026 (owner-confirmed) |
| Committee approval of the expanded scope | **Pending** |
| Proposal Document, Presentation, PoC | **Not completed**; Sprint 0 work is To Do |
| Full application implementation, custom datasets, recordings, evaluation | **Not started** |

The live status is always [PROJECT_STATUS.md](../PROJECT_STATUS.md).

## 3. Read these files in order

| # | File | Why | Time |
|---|---|---|---|
| 1 | This page | Orientation | 10 min |
| 2 | [PROJECT_STATUS.md](../PROJECT_STATUS.md) | What is done, approved and pending today | 10 min |
| 3 | [SPRINT_0.md](SPRINT_0.md) | The three deliverables, milestones, your Jira tasks | 10 min |
| 4 | [SPECIFICATION.md](SPECIFICATION.md) §1, §3, §5, §8, §10, §15 | The canonical scope and design (read it completely before proposing design changes) | 45 min |
| 5 | [ARCHITECTURE.md](ARCHITECTURE.md) | Architecture and the read-only / Admin governance rules R1–R5 | 15 min |
| 6 | The guide for your track: [proposal/README.md](proposal/README.md), [presentation/README.md](presentation/README.md) or [poc/POC_KICKOFF.md](poc/POC_KICKOFF.md) | How your deliverable is built | 15 min |
| 7 | [CONTRIBUTING.md](../CONTRIBUTING.md) and [AGENTS.md](../AGENTS.md) | GitHub workflow and the rules every human and AI agent follows | 15 min |

## 4. Where each member begins

| Member | Start with | Then | Also before 28 Oct |
|---|---|---|---|
| **Amr** | `CQP-2` RQ baseline (due 27 Oct) | `CQP-22` Phase A: PoC scope + Interface Contract v1.0 | Create the University Drive folder and post its link as a comment on `CQP-1`; send the PoC scope to the supervisor |
| **Sayed** | `CQP-3` SLR protocol (due 28 Oct) | `CQP-7` RQ1 | Review the draft PoC contract for voice/ASR/translation (`CQP-23`) |
| **Abdelrahman** | `CQP-4` extraction and quality framework (due 28 Oct) | `CQP-8` RQ2 | Review the draft PoC contract for BIR and the decision policy (`CQP-24`) |
| **George** | `CQP-5` IEEE structure and references (due 28 Oct) | `CQP-9` RQ3 | Review the draft PoC contract for the UI (`CQP-25`) |
| **Abdallah** | `CQP-6` screening and PRISMA protocol (due 28 Oct) | `CQP-10` RQ4 | Review the draft PoC contract for data, guard and SQL (`CQP-26`) |

Full task map: [SPRINT_0.md §4](SPRINT_0.md#4-task-map).

## 5. The working loop for every task

1. **Read** your Jira issue completely (see [SPRINT_0.md §6](SPRINT_0.md#6-how-to-use-your-jira-issue)).
2. **Check prerequisites:** Blocks links, Gate G-A, and handoffs you are waiting for.
3. **Read the template part** your issue produces, in the university template and the lecture guide, and the team's private Proposal map page. No issue contains a ready-made AI prompt; if you use an AI tool, brief it yourself (§7).
4. **Produce** your deliverable. Every source, number and claim must be real and checkable.
5. **Verify it yourself** against the acceptance criteria in the issue.
6. **Request independent review** from the reviewer named in the issue or QA sub-task. Nobody reviews their own work.
7. **Record delivery evidence** as a Jira comment: link, version, date, and @mention the consumers.
8. **Repository changes only:** follow the GitHub workflow in [CONTRIBUTING.md](../CONTRIBUTING.md) (branch → draft PR → human review → owner-authorized merge).

### Example: a correct academic-task handoff

> **Comment on `CQP-3`:** "SLR protocol v1.0 is ready: University Drive `01-SLR/protocol_v1.0` (link in this comment only, never in the public repository). Databases: only those confirmed reachable through MIU/EKB. Search strings logged with date and result count. Reviewed by Abdallah (QA-05) on <date>. @Abdallah @Abdelrahman you can start `CQP-12` / `CQP-13` inputs."

What makes it correct: a location and version, real logged evidence, the named reviewer, and the consumers notified. It contains no private links in the public repository and no invented counts.

### Example: a correct code-task handoff

> **Comment on `CQP-26`:** "Guard v0.2 meets Interface Contract v1.0 (`SqlRequest`/`SqlResult`). Branch `feat/cqp-26-sql-guard` in the code repository the owner designated. Tests: <n> pass, <m> fail (`<test command>` output saved in `05-PoC-Docs`). Crafted `DELETE`/`DROP` rejected before execution; row counts unchanged. Known limitation: no timeout test yet. @Amr ready for C1 integration."

What makes it correct: the contract version, where the code is, the **actual** command output, the safety evidence, an honest limitation, and the integrator notified. The placeholders `<n>` and `<m>` stand for the counts you actually observed; never fill them in from memory.

## 6. Where things go: public vs private

This repository is **public**. Anyone on the internet can read it, including every past commit.

| Location | What goes there |
|---|---|
| **This GitHub repository (public)** | Approved project documentation, public-safe architecture, onboarding, contribution rules, status, public-safe technical contracts. Source code **only** after the owner approves publishing it here (open decision, [PROJECT_STATUS.md §4](../PROJECT_STATUS.md#4-open-decisions-from-specificationmd-22)) |
| **Jira `CQP` (private)** | Task steps, assignments, delivery comments, QA verdicts |
| **University Drive (private)** | Search logs, screening/PRISMA sheets, extraction sheets, slide decks, PoC docs and test evidence, consented recordings. Paper PDFs **only when their access and sharing terms permit it**; otherwise DOI links, bibliographic metadata, extraction notes and permitted references. Folder and access setup is **pending** (Amr) |
| **Private Overleaf project** | The university template and the working Proposal Document |
| **Private code repository (if the owner designates one)** | PoC code, if the owner decides it should not be public |

**Never commit:** university e-mail addresses, Jira account IDs, the private university template, private Drive or Overleaf links, instructor recordings or transcripts, paper PDFs (paywalled or not), voice recordings, API keys, passwords, database credentials, `.env` files, real personal data, downloaded third-party datasets, or large generated artifacts. Use your GitHub **noreply** e-mail for commits. Details: [AGENTS.md §4](../AGENTS.md#4-what-must-never-be-committed).

## 7. Using AI tools

No issue and no document in this repository gives a ready-made AI prompt: what you need changes with the task and with what you find. If you use an AI tool, brief it yourself from your Jira issue and the template, correct it when it is wrong, and hold it to these rules:

- An AI tool working in this repository reads `AGENTS.md` and `CLAUDE.md` first.
- Do not expand, reduce or redesign the V3.1 scope. Do not change the title, the registration Abstract, the v6 diagram or the marked blocks in `docs/`.
- Nothing is described as implemented, measured, collected or approved unless the team has confirmed it.
- No invented papers, citations, numbers, benchmark results or test output. Open every source yourself.
- P2 and P4 are defined in [SPECIFICATION.md §15.1](SPECIFICATION.md); do not redefine them.
- Do not guess people's identities, GitHub handles or Jira accounts.
- Work only on a feature branch; never push to `main`, merge or force-push.
- Never give an AI tool secrets, private links, personal data or restricted datasets.

## 8. Next milestone and immediate actions

The next milestone is **Gate G-A on 28 Oct 2026** (PoC Interface Contract v1.0) together with the protocol and framework tasks due 28 Oct. Immediate actions:

1. Everyone: read §3 and open your first Jira task from §4.
2. Amr: confirm the GitHub handles of Sayed and George, create the University Drive folder, decide where PoC code lives, and send the PoC scope to the supervisor.
3. Component owners: review [poc/INTERFACE_CONTRACT_DRAFT.md](poc/INTERFACE_CONTRACT_DRAFT.md) and post questions on `CQP-22` before 28 Oct.
