# Change Record D-39 — Jira Tasks Aligned with the University Template

| Field | Value |
|---|---|
| Decision | **D-39** |
| Date | 2026-10-27 |
| Authorized by | The team member working with Claude Code in this session (Jira account shown as "Sayed abdo"), in explicit instructions of 27 Oct 2026: align the Jira `CQP` tasks with the university proposal template and the lecture guide, remove everything the template does not ask for, remove all AI prompts, and keep the repository documents consistent with Jira |
| What this records | (a) The rewrite of the Jira `CQP` task descriptions, targets and list order; (b) the repository files changed to match |
| Impact | Planning and documentation only. The title, Abstract, specification, architecture, datasets, evaluation methodology, registration fields and v6 diagram are unchanged. Owners are unchanged and no issue was deleted. Implementation is **NOT STARTED**; no search, screening or result exists |

## 1. Jira changes (27 Oct 2026)

Edited through the Jira REST API with the account above. Every edit returned HTTP 204. The previous descriptions stay in each issue's Jira history.

- **`CQP-1`:** a short description with the three deliverables, the rule that the university template and the lecture guide decide the content and format of the document, the lecture's order of work with targets, and the University Drive folders. The requirements traceability matrix, effort table, risk table, handoff register and critical path were removed.
- **`CQP-2` … `CQP-16` (Proposal Document):** each description now names the template part it produces, what the template asks to delete, keep and add, short steps and "Done when". The AI execution prompts, estimates and the extra artefacts they required (evidence-strength ratings, claim-audit lists, metric-mapping tables, traceability matrix, 20% double-screening sample) were removed. Main content decisions, all taken from the template and the lecture guide:
  - order of work: RQs → criteria, databases and search strings (shown to the supervisor before searching) → recording sheet and screening rules → extraction columns and quality checklist → Overleaf setup → searches and screening → **corpus freeze on 1 Nov** → Table I → Tables II and III → Results RQ1–RQ4 → short RQ5 answer (III-E) → Proposed Solution → Introduction, Discussion, Conclusion, Abstract → final review;
  - two people judge every paper during screening;
  - quality assessment uses the template's five criteria (Yes = 1, Partial = 0.5, No = 0; below 0.5 excluded and counted in PRISMA);
  - Tables I–III keep the template's rows and columns (Table I: "Main task" instead of "LR Stage");
  - Section III uses A = RQ1, B = RQ2, C = RQ3 (added), D = RQ4 and a short E = RQ5;
  - Section VI uses the template headings A–E in order; Fig. 2 is the approved System Overview v6, unchanged;
  - `CQP-15` ends with a final review of the whole document against the lecture guide's checklist.
- **`CQP-17` … `CQP-26` (Presentation and PoC):** the AI execution prompt and the estimate were removed from each description; the other sections were kept. References to removed artefacts were corrected (`CQP-17`, `CQP-19`, `CQP-20`, `CQP-21`, `CQP-22`, `CQP-24`), and the readiness checklist that existed only inside the `CQP-21` prompt was moved into its steps.
- **`CQP-27` … `CQP-31` (independent reviews):** short review checklists; reviewers and authors under review unchanged.
- **Targets:** `CQP-3` 28 Oct; `CQP-13` 2 Nov; `CQP-14` 3 Nov (start 2 Nov); `CQP-7`, `CQP-8`, `CQP-9`, `CQP-10` 4 Nov; `CQP-11` 5 Nov (start 4 Nov); `CQP-15` 8 Nov. Other dates unchanged.
- **Titles:** `CQP-11` "RQ5: Short Answer (III-E) and Inputs for VI-B"; `CQP-14` "Tables II and III"; `CQP-15` "Introduction, Discussion, Conclusion, Abstract and Final Review"; `CQP-16` "Proposed Solution (Section VI)".
- **After reading the sample proposal (same day):** `CQP-5` shows the header date format used in the sample; `CQP-13` changes "the LR phase addressed" in the paragraph above Table I to "the main task"; the `CQP-15` final review also checks for leftover template wording, internal notes, first-person "I" and spelling mistakes.
- **List order (Rank):** `CQP-1`, `CQP-2`, `CQP-3`, `CQP-6`, `CQP-4`, `CQP-5`, `CQP-12`, `CQP-13`, `CQP-14`, `CQP-7`, `CQP-8`, `CQP-9`, `CQP-10`, `CQP-11`, `CQP-16`, `CQP-15`, then `CQP-17` … `CQP-31` as before.

## 2. Verification performed

- Every description update and rank change returned HTTP 204.
- A read-back of all 31 descriptions found no remaining "AI Execution Prompt", "AI Review Prompt", estimate line, "EVIDENCED"/"INFERRED" label, handoff-register reference, claim-audit list or metric-mapping table.
- The list order was read back after ranking and matches §1.
- Rendered descriptions were spot-checked: the bracketed citations [1] and [2] and the example search string render correctly.

## 3. Repository files changed by D-39

- `docs/SPRINT_0.md`: plan note, status, milestones (corpus freeze), task map titles, deliverables and targets, QA scope, gates, and "How to use your Jira issue" (no ready-made AI prompts).
- `docs/TEAM_START_HERE.md`: status line, first-task dates, working loop step 3, Jira row, §7 replaced by rules for using AI tools (the handoff prompt was removed), §8 dates.
- `docs/proposal/README.md`: Jira description and the document workflow in the lecture's order of work.
- `docs/proposal/PROPOSAL_REQUIREMENTS.md`: paper structure (Tables I–III in Section II, III-E, Section VI headings), RQ placement, tables and figures, section ownership and reviews.
- `docs/proposal/RESEARCH_QUESTIONS.md`: where RQ5 is answered; RQ4 evidence wording.
- `docs/proposal/RQ_GAP_SOLUTION_MATRIX.md`: marked as an optional working aid.
- `docs/proposal/SLR_PROTOCOL_DRAFT.md`: Jira tasks win over the draft; RQ5 placement; ACL Anthology row; two screeners for every record; template quality threshold.
- `docs/presentation/README.md`: Slide 11 source.
- `docs/poc/INTERFACE_CONTRACT_DRAFT.md`: reference to the `CQP-22` prompt replaced by the `CQP-24` description.
- `PROJECT_STATUS.md`, `PROJECT_EVOLUTION.md`, `README.md`, `docs/README.md`, `AGENTS.md` (next decision D-40) and this record.

No canonical document block in `docs/` was edited, and the v6 diagram is unchanged.

## 4. Open items

1. Tell the project owner (Amr) about the rewrite. He owns `CQP-1`, `CQP-2`, `CQP-11` and `CQP-16`; his history shows `CQP-2` moved to In Progress on 25 Oct and back to To Do on 26 Oct, before this rewrite.
2. The sample document (CodeAtlas, SWE07) was read on 27 Oct 2026 but is not stored in this repository (it is another team's private university material). What to take from it and what not to copy is reflected in the Jira tasks and in the team's private Proposal map page.
3. The team's private Proposal map page, which explains each template part and its task, is kept in sync with Jira outside this repository.
