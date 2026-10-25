# AGENTS.md — Rules for AI Agents and Contributors

Project: **ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic** (MIU Software Engineering graduation project), V3.1 team-approved planning baseline.

These rules apply to every AI agent (Claude Code, Codex, ChatGPT, Copilot and others) and every human contributor working in this repository.

## 1. Read first, in this order

1. This file and [CLAUDE.md](CLAUDE.md): the repository instructions.
2. [PROJECT_STATUS.md](PROJECT_STATUS.md): what is and is not done or approved, right now. Then [docs/TEAM_START_HERE.md](docs/TEAM_START_HERE.md) and [docs/SPRINT_0.md](docs/SPRINT_0.md) for the current milestone and task map.
3. [docs/SPECIFICATION.md](docs/SPECIFICATION.md): the **canonical V3.1 specification and source of truth**. Read it completely before proposing anything.
4. [docs/ARCHITECTURE.md](docs/ARCHITECTURE.md): architecture, demonstration contract and the read-only / Admin governance contract (rules R1–R5).
5. The Jira `CQP` issue you are working on (the human pastes it; agents do not browse Jira on their own) and the guide for its track: [docs/proposal/](docs/proposal/README.md), [docs/presentation/](docs/presentation/README.md) or [docs/poc/POC_KICKOFF.md](docs/poc/POC_KICKOFF.md).
6. [CONTRIBUTING.md](CONTRIBUTING.md): branch, pull request, review and validation rules.
7. [docs/DATASET_STRATEGY.md](docs/DATASET_STRATEGY.md), [docs/EVALUATION_PLAN.md](docs/EVALUATION_PLAN.md) and [PROJECT_EVOLUTION.md](PROJECT_EVOLUTION.md) when the task touches data, evaluation or history. History never overrides the current spec.

**Authority order:** (1) the user's newest explicit decision in conversation; (2) `docs/SPECIFICATION.md` and the other canonical docs in `docs/`; (3) verified repository code and tests, once they exist; (4) history. If two current documents disagree, stop and report the conflict instead of choosing silently.

## 2. Current stage

- Official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*: **TA approved** (D-33). Abstract: **student-confirmed final**. All six registration form fields: **finalized**.
- University registration form: **SUBMITTED on 25 Oct 2026** (owner-confirmed, D-37). Formal committee approval of the expanded scope: **not obtained**.
- Implementation: **NOT STARTED**. Custom datasets and recordings: **PLANNED, not collected**. Evaluation: **NOT STARTED**.
- Current milestone: **Sprint 0, Proposal Discussion readiness** (D-38), tracked in the private Jira project `CQP` ([docs/SPRINT_0.md](docs/SPRINT_0.md)). Its three deliverables (Proposal Document, 15-slide Presentation, minimal PoC) are **not completed**; the PoC is **not implemented**, and its scope is the team's proposal pending supervisor confirmation. The old Jira project `SCRUM` (D-37) is superseded.
- **Do not start coding, generating data or creating infrastructure unless the user explicitly authorizes that task.** Planning, reviewing and drafting are fine.
- Never describe anything as implemented, collected, measured, submitted, registered or committee-approved unless the user has confirmed it.

## 3. Non-negotiable project rules

1. **Exact title:** *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* (TA approved, D-33, 24 Oct 2026). The earlier title *Voice-to-SQL in Egyptian Arabic* (D-29) is history only. Do not add a suffix unless the university requires one; do not rename the project, and do not rename the GitHub repository `voice-to-sql-egyptian-arabic` without explicit approval.
2. **The Abstract is frozen.** The text between the `BEGIN VERBATIM ABSTRACT` markers in [README.md](README.md) and Field 2 of [docs/REGISTRATION_FORM_FIELDS.md](docs/REGISTRATION_FORM_FIELDS.md) must never be rewritten, shortened, expanded or translated.
3. **The v6 diagram is frozen.** Never redesign, regenerate, edit, compress or replace `assets/System-Overview-3840x2160-v6.png` (SHA-256 `62d3743e297e5eba7c0ea0e062643c7f756291777911942b73e1e2bddd280653`). Changing it needs new supervisor approval.
4. **Full V3.1 scope stays intact:** Sales, Inventory and HR are all mandatory functioning workspaces; ambiguity-aware selective answering (BIR, ambiguity detection, Answer / Clarify / Abstain); the TA-clarified English-to-SQL pipeline; safe read-only SQL; AI Schema Design with Admin approval. Do not silently drop, downgrade (for example, voice to typed-only) or expand the scope.
5. **Processing order (SPECIFICATION.md §8.1) — Egyptian-Arabic Voice → Arabic Text → English Text → English-to-SQL, with Arabic-anchored ambiguity checking:** BIR, ambiguity detection and the decision run on the **original confirmed Arabic** before any SQL. The English translation is derived and audited and may never resolve an ambiguity. English-to-SQL runs only after an Answer decision; Clarify and Abstain execute no SQL.
6. **Read-only analytics:** a single SELECT over allowlisted views, AST + allowlist + server-side department authorization + BIR↔SQL consistency checks, least-privilege read-only role, timeouts and row caps. A parser alone is not security.
7. **No automatic DDL.** Admin approval of a schema design publishes metadata only. Provisioning is a separate, human, operator-controlled step in an isolated demo environment. No LLM-supplied CREATE / ALTER / DROP ever executes.
8. **Authorization comes from the server**, never from model output. Unauthorized workspace requests are denied before any model call.
9. **Data:** one explicitly **synthetic** demonstration company. HR uses invented records only; no salary, national ID, phone, address, performance or health fields. Never collect or commit real personal or employee data.
10. **Research honesty:** no invented results, interviews, approvals, dataset counts, benchmarks or GitHub/CI evidence. Do not claim novelty for Text-to-SQL, schema generation, semantic layers or clarification in general (SPECIFICATION.md §1.2, §16).
11. **Fair evaluation:** P2 and P4 receive byte-identical frozen inputs; prompt iteration on dev data only; human English references, gold SQL and gold results never enter prompts; no training or fine-tuning.

## 4. What must never be committed

- Passwords, API keys, tokens, connection strings, `.env` files, private keys or certificates.
- Voice recordings, consent forms, speaker-ID keys or any participant data (they live in an access-controlled team drive, never in Git).
- Real HR or personal data of any kind.
- Downloaded third-party datasets (Casablanca is CC BY-NC-ND, no redistribution; AraSpider redistribution terms are uncertain; AMBROSIA's authors ask that it not be uploaded to GitHub or Hugging Face).
- Backup ZIPs, registration-package archives, the historical V2/V3 snapshots, duplicate specifications or scratch research outputs.

The [.gitignore](.gitignore) blocks the common cases, but it is not a substitute for checking `git status` before every commit.

## 5. Change protocol

The canonical documents in `docs/` embed approved package text in marked blocks:

- `BEGIN VERBATIM … sha256="…"`: byte-identical to the package source.
- `BEGIN AMENDED DERIVATIVE … source_sha256="…" derivative_sha256="…" amendment="D-31"`: package text changed by a documented amendment. The original source hash is kept for provenance. **Never describe an amended block as byte-identical to its source.**

To keep them traceable:

1. **Propose before editing.** Give the file, section, old text and new text, and wait for the user's explicit approval. Never edit a marked block on your own initiative.
2. When an approved change is applied: turn a `VERBATIM` block into an `AMENDED DERIVATIVE` block (or update an existing one), keep `source_sha256`, update `derivative_sha256` and the amendment ID in the marker and in [docs/README.md](docs/README.md#provenance), write a change record with the exact before and after text (like [docs/CHANGE_RECORD_D-31.md](docs/CHANGE_RECORD_D-31.md)), and add a dated entry to [PROJECT_EVOLUTION.md](PROJECT_EVOLUTION.md#5-decision-index). The next decision is **D-39**; record who authorized it.
3. Status-only changes go to [PROJECT_STATUS.md](PROJECT_STATUS.md) first.
4. Keep exactly one canonical document per topic. Do not add `SPEC_v2.md`, `*_old.md`, `*_final_final.md` or copies of archive files.

## 6. Language and style

- Canonical documents, the specification and formal academic text stay in **English**.
- When explaining to the Egyptian student team, use **Egyptian Arabic with English technical terms** unless asked otherwise.
- Use the project's terms consistently: BIR, SRR, Answer / Clarify / Abstain, P0–P4, S0–S2, workspace, Admin, operator, Security suite.

## 7. Git and GitHub

- The repository is **public** (D-36, 24 Oct 2026) and has **no license**: licensing and ownership are undecided, and public visibility is not a license. Do not add a LICENSE file, change the repository visibility or suggest that the project owns or may redistribute third-party datasets.
- Everything pushed, including commit metadata (author names and e-mail addresses), is visible to anyone and may be copied by forks. Check §4 before every commit, and use GitHub's private no-reply e-mail address for commits.
- Do not initialize Git, create remotes, commit, push, publish, open pull requests or change repository settings without the user's explicit instruction for that step.
- Never rewrite published history or force-push.
- Do not guess people's identities, GitHub handles or Jira accounts; use only mappings the owner has confirmed ([PROJECT_STATUS.md](PROJECT_STATUS.md)).
- Finish every task by listing every file you changed and every check you ran, with its real result. Never report a check you did not run.
- `main` is protected (D-35). Never push to `main`: work on a feature branch and open a pull request as described in [CONTRIBUTING.md](CONTRIBUTING.md). A merge needs one approval from a human other than the author. An AI agent never approves or merges a pull request, and the human who opens a pull request is responsible for all AI-generated content in it.
- Line endings are normalized to LF by [.gitattributes](.gitattributes) so the recorded block hashes stay valid; the PNG is binary.
