# Team Start Here — ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic

Welcome. This page is the onboarding path for the five team members and for any AI agent working with them. It links to the canonical files instead of repeating them.

## 1. ClearQuery in one minute

- **What it is:** an ambiguity-aware Voice-to-SQL system for **Egyptian Arabic**. It is an **AI Central Hub** for **one synthetic demonstration company** with three separately authorized workspaces: **Sales** (primary evaluation domain), **Inventory** and **HR**.
- **The problem:** managers ask business questions in Egyptian Arabic that can mean more than one thing. A technically valid SQL query can then return a confident but wrong business answer (a **silent semantic error**).
- **The idea:** turn each question into a **Business Intent Representation (BIR)** grounded in an approved business catalog, detect material ambiguity on the **original Arabic**, and choose **Answer / Clarify / Abstain** **before** any SQL is generated. Only an Answer produces guarded, **read-only** SQL, and every number comes from the database.
- **The pipeline:** Egyptian-Arabic voice or text → speech recognition (voice only) → editable Arabic transcript → Arabic-to-English translation → English Text-to-SQL, with the original Arabic kept for intent and ambiguity checking ([SPECIFICATION.md §8.1](SPECIFICATION.md)).
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
| **Amr** | `CQP-2` RQ baseline (due 27 Oct) | `CQP-22` Phase A: PoC scope + Interface Contract v1.0 | Create the University Drive folder and record it in `CQP-1` section E; send the PoC scope to the supervisor |
| **Sayed** | `CQP-3` SLR protocol (due 27 Oct) | `CQP-7` RQ1 | Review the draft PoC contract for voice/ASR/translation (`CQP-23`) |
| **Abdelrahman** | `CQP-4` extraction and quality framework (due 28 Oct) | `CQP-8` RQ2 | Review the draft PoC contract for BIR and the decision policy (`CQP-24`) |
| **George** | `CQP-5` IEEE structure and references (due 28 Oct) | `CQP-9` RQ3 | Review the draft PoC contract for the UI (`CQP-25`) |
| **Abdallah** | `CQP-6` screening and PRISMA protocol (due 28 Oct) | `CQP-10` RQ4 | Review the draft PoC contract for data, guard and SQL (`CQP-26`) |

Full task map: [SPRINT_0.md §4](SPRINT_0.md#4-task-map).

## 5. The working loop for every task

1. **Read** your Jira issue completely (see [SPRINT_0.md §6](SPRINT_0.md#6-how-to-use-your-jira-issue)).
2. **Check prerequisites:** Blocks links, Gate G-A, and handoffs you are waiting for.
3. **Run the AI execution prompt** from your issue in a new AI session, giving it only the inputs it asks for.
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
| **Jira `CQP` (private)** | Task instructions, AI execution prompts, assignments, delivery comments, QA verdicts |
| **University Drive (private)** | Search logs, screening/PRISMA sheets, extraction sheets, paper PDFs, slide decks, PoC docs and test evidence, consented recordings. Folder and access setup is **pending** (Amr) |
| **Private Overleaf project** | The university template and the working Proposal Document |
| **Private code repository (if the owner designates one)** | PoC code, if the owner decides it should not be public |

**Never commit:** university e-mail addresses, Jira account IDs, the private university template, private Drive or Overleaf links, instructor recordings or transcripts, paywalled PDFs, voice recordings, API keys, passwords, database credentials, `.env` files, real personal data, downloaded third-party datasets, or large generated artifacts. Use your GitHub **noreply** e-mail for commits. Details: [AGENTS.md §4](../AGENTS.md#4-what-must-never-be-committed).

## 7. AI agent handoff prompt

Paste this at the start of an AI session that will work in this repository, then add your Jira task's own prompt.

```text
You are helping on ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic
(MIU graduation project, V3.1). Repository: Amr-Heibaa/voice-to-sql-egyptian-arabic (public).

Before doing anything, read in this order:
1. AGENTS.md and CLAUDE.md (rules)
2. PROJECT_STATUS.md (current status)
3. docs/SPECIFICATION.md (canonical V3.1 specification; read the sections relevant to the task completely)
4. docs/ARCHITECTURE.md (approved architecture and governance rules R1-R5)
5. docs/SPRINT_0.md and the guide for my track (docs/proposal/, docs/presentation/ or docs/poc/)
6. CONTRIBUTING.md (branch and pull request rules)
My Jira task is CQP-__ ; I will paste its content.

Rules:
- Do not expand, reduce or redesign the V3.1 scope. Do not change the title, the registration
  Abstract, the v6 diagram or the marked blocks in docs/.
- Do not claim anything is implemented, measured, collected or approved unless I confirm it.
- No invented papers, citations, numbers, benchmark results or test output.
- Do not redefine P2 or P4; quote SPECIFICATION.md section 15.1.
- Do not guess people's identities, GitHub handles or Jira accounts.
- Work only on a feature branch; never push to main; never merge; never force-push.
- Touch only files my task needs. Never commit secrets, private links or personal data.
- Finish by listing every file you changed and every check you ran with its real result.
```

## 8. Next milestone and immediate actions

The next milestone is **Gate G-A on 28 Oct 2026** (PoC Interface Contract v1.0) together with the protocol and framework tasks due 27–28 Oct. Immediate actions:

1. Everyone: read §3 and open your first Jira task from §4.
2. Amr: confirm the GitHub handles of Sayed and George, create the University Drive folder, decide where PoC code lives, and send the PoC scope to the supervisor.
3. Component owners: review [poc/INTERFACE_CONTRACT_DRAFT.md](poc/INTERFACE_CONTRACT_DRAFT.md) and post questions on `CQP-22` before 28 Oct.
