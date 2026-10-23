# Change Record D-31 — Clean-Repository Documentation Corrections

| Field | Value |
|---|---|
| Decision | **D-31** (continues the package decision log D-01–D-30) |
| Date | 2026-10-23 |
| Authorized by | The student, in the Phase 1.5 "Final Staging Cleanup" instruction (23 Oct 2026), after reviewing the Phase 1 staging report |
| Applies to | This repository only. The final registration package, its manifest and `FINAL_FORM_COPY_PASTE.md` were **not** modified |
| Purpose | Fix stale status wording and references that do not resolve in a clean repository (staging-report issues A1–A5 and A9) |
| Impact | **None on scope, design or registration content.** The title, the Abstract, the six form-field texts, the v6 diagram, architecture decisions, the evaluation methodology, dataset decisions and all counts are unchanged |
| Edits | 35 exact text replacements in 5 source documents |

## How provenance works after D-31

- Blocks changed by D-31 are marked `BEGIN AMENDED DERIVATIVE` … `END AMENDED DERIVATIVE`. Each marker keeps the **original package source SHA-256** for provenance and adds the **derivative SHA-256** of the amended text. **An amended block is not byte-identical to its source and must never be described as such.**
- Blocks that D-31 did not touch stay `BEGIN VERBATIM` (only the evaluation notes in `docs/EVALUATION_PLAN.md` Part B), together with the Abstract in `README.md` and the v6 image, which remain byte-identical.
- **Reproducibility:** applying the replacements below to the original package files reproduces each derivative exactly (checked by re-running the amendment and comparing hashes). Every "before" text occurs in the original source exactly the number of times stated, and no replacement overlaps another, so the order of application does not matter.
- The six field boxes in `docs/REGISTRATION_FORM_FIELDS.md` are verified one by one against the original `FINAL_FORM_COPY_PASTE.md`, so the registration text itself is still byte-identical.

| Repository document | Package source | Original SHA-256 | Derivative SHA-256 |
|---|---|---|---|
| `docs/SPECIFICATION.md` | `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md` | `5116f13cfe3909dcb37cb95cef0301e203ab6fbe45541292c23e6030c1c82fc6` | `0032b8c945a81857d30c82a2075b97f5ecd90d151ab8bd336321187cdf312743` |
| `docs/ARCHITECTURE.md (Part A)` | `03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md` | `78b9b9d456ed6ec251c576e0afc5f8e884a82c2f0e72091a8caec2d1843d043a` | `b7e3d2ca37670a5121e7f5635619f3628f2426a60f875b3d596b9fa73678aba8` |
| `docs/ARCHITECTURE.md (Part B)` | `03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md` | `ce1384180d0a180ed15a03266356ad7c1bb80774ef5cf385ac2841ff7d15a0ba` | `aacf664ed7eb2af4d1adb6d4c544e707e0a997f70c291fd6b8b2c71ad6745c9d` |
| `docs/DATASET_STRATEGY.md` | `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md` | `724ac0b92b82ec1ddcfbe93bf596683e6c1481e7104e151112ac3150a62adf05` | `a29aa0926496f2823682cf4b2498c70a3505fae270f51dbfc6b3b229af9d8038` |
| `docs/REGISTRATION_FORM_FIELDS.md` | `FINAL_FORM_COPY_PASTE.md` | `157d641e856a4602f2f717f306865c1eb8fef2fb773f6a7fe9a362c20a36f804` | `ec89264912b95773804fb366c83ef207db33b50fb5e59826f3fc8aa91e379a61` |

## Summary by issue

| Issue | What changed | Edits |
|---|---|---|
| A1 | Outdated DS-11 status (Fields 4–5 are student-confirmed final) | 2 |
| A2 | Incorrect historical V2 form filename | 1 |
| A3 | Misleading version/status wording | 4 |
| A4 | Legacy "V3 draft" self-reference | 1 |
| A5 | Misleading "at-least-one" spoken-example heading | 1 |
| A9 | References to files that are not in this repository | 25 |
| D-31 | Change-log entry | 1 |

Note on A2: the earlier text cited `01_MIU_FORM_READY_TO_PASTE_FINAL.md`. No file with that name exists anywhere in the registration package (it may have been an earlier working filename, which cannot be verified). The archived V2 form is `01_READ_ONLY_V2_BASELINE/MIU_FORM_V2_FROZEN_NOT_SUBMITTED.md`, which the specification already listed correctly in §24.1.

Note on A9: references to excluded files are either re-pointed to the repository document that now holds the same content, or explicitly labelled as registration-package archives that are not included in this repository. The one piece of required content that existed only in an excluded file, the seven inventory-ledger invariants (deep-research record §3.2), is now inlined unchanged in `docs/DATASET_STRATEGY.md` §4.3.

## Every edit (before → after)

### A1 — Outdated DS-11 status (Fields 4–5 are student-confirmed final)

**A1.1** · `docs/DATASET_STRATEGY.md` (source `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md`) · occurrences replaced: 1

*Reason:* Heading date did not reflect the DS-11 status.

Before:

````text
## 9. Decision status (updated 22 Oct 2026)
````

After:

````text
## 9. Decision status (updated 22 Oct 2026; DS-11 status updated 23 Oct 2026, D-31)
````

**A1.2** · `docs/DATASET_STRATEGY.md` (source `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md`) · occurrences replaced: 1

*Reason:* Superseded by D-30.

Before:

````text
The TA replied positively to the dataset evidence; the final form wording awaits student confirmation |
````

After:

````text
The TA replied positively to the dataset evidence (support for the evidence, not approval of the wording). The final Field 4 and Field 5 wording was **student-confirmed final on 23 Oct 2026 (D-30)** |
````

### A2 — Incorrect historical V2 form filename

**A2.1** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* The cited V2 filename exists nowhere in the package; the archived file is MIU_FORM_V2_FROZEN_NOT_SUBMITTED.md (also listed in §24.1).

Before:

````text
The original V2 six-field draft, `01_MIU_FORM_READY_TO_PASTE_FINAL.md`, is archived read-only. V3's new draft is located under `04_FORM_PREPARATION_NOT_SUBMITTED/` and contains the same six categories:
````

After:

````text
The original V2 six-field draft is archived read-only in the registration package as `01_READ_ONLY_V2_BASELINE/MIU_FORM_V2_FROZEN_NOT_SUBMITTED.md` (not included in this repository). The final V3.1 field text, generated unchanged from the package's form draft (`04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md`), is in `docs/REGISTRATION_FORM_FIELDS.md` and contains the same six categories:
````

### A3 — Misleading version/status wording

**A3.1** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* The snapshot date alone hid the 23 Oct synchronization (D-20–D-30).

Before:

````text
**Snapshot:** 22 October 2026 · Misr
````

After:

````text
**Snapshot:** 22 October 2026 (V3.1 baseline; last synchronized 23 October 2026 through D-30; repository amendment D-31, 23 October 2026) · Misr
````

**A3.2** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Pointed to excluded files and still said "team-approved … do not claim faculty approval" although the supervisor approved v6 (D-18).

Before:

````text
Use the bundled file `03_ARCHITECTURE_AND_FIGMA/SYSTEM_OVERVIEW_STYLE_REFERENCE_USER_SUPPLIED.png` as visual guidance in the Figma design conversation; the Figma prompt in `03_ARCHITECTURE_AND_FIGMA/` sets the architectural labels. The rendered, **team-approved** figure is `System-Overview-3840x2160-v6.png`; do not claim faculty approval.
````

After:

````text
That reference image (visual style only; it depicts a different, older project) and the Figma Make prompt were the historical inputs for the figure; both are kept in the registration package, not in this repository. The rendered figure is `assets/System-Overview-3840x2160-v6.png`, approved by the project team and the academic supervisor; do not claim committee approval.
````

**A3.3** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* "NOW" and "Finalize …" read as if registration content were still open.

Before:

````text
### Phase 0 — NOW: form preparation and scope lock
````

After:

````text
### Phase 0 — form preparation and scope lock (content complete 23 Oct 2026; submission pending)

*Status (D-31): the title (TA-approved, D-29), the Abstract (student-confirmed final, D-27) and all six form fields (D-30) are finalized, and v6 is supervisor-approved. Still open: the student's personal submission of the form, a check of the live form's input limits, and committee confirmation of the expanded scope (Q12). The bullets below are the original Phase 0 plan, kept as history.*
````

**A3.4** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* The independent audit has been completed.

Before:

````text
(4) an independent final review of the package (ChatGPT) runs;
````

After:

````text
(4) done: an independent final review of the package (ChatGPT) was completed (reported by the student, 23 Oct 2026);
````

### A4 — Legacy "V3 draft" self-reference

**A4.1** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Legacy wording called the current V3.1 specification "this V3 draft".

Before:

````text
2. This V3 draft supersedes V2 design descriptions *where stated*, but the untouched V2 snapshot records history and research details.
````

After:

````text
2. This V3.1 specification supersedes the V2 and V3-draft design descriptions *where stated*; the untouched V2 and V3-draft snapshots (archived in the registration package and summarized in `PROJECT_EVOLUTION.md`) record history and research details.
````

### A5 — Misleading "at-least-one" spoken-example heading

**A5.1** · `docs/ARCHITECTURE.md (Part A)` (source `03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md`) · occurrences replaced: 1

*Reason:* "At-least-one" read as the target; the plan is ≈60 typed items and 24 recordings per Inventory/HR workspace, and one voice query is only a floor (spec §15.4).

Before:

````text
| Workspace | Data and approved metrics | At-least-one mandatory spoken example | Security proof |
````

After:

````text
| Workspace | Data and approved metrics | Example spoken question (illustrative; planned targets: spec §14.3 and §15.4) | Security proof |
````

### A9 — References to files that are not in this repository

**A9.1** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 5

*Reason:* Package path of the approved diagram re-pointed to its byte-identical repository copy.

Before:

````text
`03_ARCHITECTURE_AND_FIGMA/System-Overview-3840x2160-v6.png`
````

After:

````text
`assets/System-Overview-3840x2160-v6.png`
````

**A9.2** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* "Included with this package" is untrue for the repository.

Before:

````text
requested a **Figma Make prompt**, included with this package.
````

After:

````text
requested a **Figma Make prompt** (both are historical inputs kept in the registration package, not in this repository).
````

**A9.3** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Reading instructions pointed to package-only files.

Before:

````text
Read `00_START_HERE/README_FIRST.md` and `02_CURRENT_SPECIFICATION/V3_TO_V3_1_DECISION_CHANGELOG.md` for context. Files under `01_READ_ONLY_V2_BASELINE/` and `01B_READ_ONLY_V3_DRAFT_BASELINE/` remain immutable historical snapshots.
````

After:

````text
Read `README.md`, `PROJECT_STATUS.md` and `PROJECT_EVOLUTION.md` (which condenses the V3 → V3.1 decision changelog) for context. The V2 and V3-draft snapshots remain immutable historical records in the registration package; they are not part of this repository and are summarized in `PROJECT_EVOLUTION.md`.
````

**A9.4** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* "In this ZIP" is untrue for the repository.

Before:

````text
1. **Historic artifacts:** Files under `01_READ_ONLY_V2_BASELINE/` are immutable V2 snapshots in this ZIP, to prevent agents overwriting project history.
````

After:

````text
1. **Historic artifacts:** The V2 and V3-draft snapshots are immutable records kept in the registration package (`01_READ_ONLY_V2_BASELINE/`, `01B_READ_ONLY_V3_DRAFT_BASELINE/`; not part of this repository), to prevent agents overwriting project history.
````

**A9.5** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Package path re-pointed to the repository document.

Before:

````text
See `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md`.
````

After:

````text
See `docs/DATASET_STRATEGY.md`.
````

**A9.6** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Reference to an excluded research record made explicit and self-contained.

Before:

````text
Full evidence: `06_RESEARCH_AND_DATA/V3_1_DATASET_VERIFICATION_LOG.md`.
````

After:

````text
The full license and access evidence is recorded in the registration package's dataset verification log (`06_RESEARCH_AND_DATA/V3_1_DATASET_VERIFICATION_LOG.md`, not included in this repository); the conclusions this project relies on are stated in this section, §24.2 and `docs/DATASET_STRATEGY.md` §11.
````

**A9.7** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Package path re-pointed to the repository document.

Before:

````text
Details: `06_RESEARCH_AND_DATA/V3_1_EVALUATION_NOTES_TRANSLATION_PIPELINE.md`.
````

After:

````text
Details: `docs/EVALUATION_PLAN.md`, Part B.
````

**A9.8** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Reference to excluded research records made explicit.

Before:

````text
The relevant public links and research source notes are in `06_RESEARCH_AND_DATA/`.
````

After:

````text
The relevant public links are listed in §24.2; the fuller research source notes are archived in the registration package (`06_RESEARCH_AND_DATA/`, not included in this repository).
````

**A9.9** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Instruction referred to excluded historical inputs as if present.

Before:

````text
A dedicated **Figma Make prompt** lives at `03_ARCHITECTURE_AND_FIGMA/HIGH_LEVEL_OVERVIEW_FIGMA_MAKE_PROMPT.md`; attach the bundled style-only reference image inside Figma Make and use that prompt.
````

After:

````text
A dedicated **Figma Make prompt** and the style-only reference image were used in Figma Make to produce the figure; both are historical inputs kept in the registration package (`03_ARCHITECTURE_AND_FIGMA/`), not in this repository.
````

**A9.10** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Made the diagram hash self-contained.

Before:

````text
SHA-256 recorded in the package manifest)
````

After:

````text
SHA-256 `62d3743e297e5eba7c0ea0e062643c7f756291777911942b73e1e2bddd280653`, as recorded in the registration package manifest)
````

**A9.11** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Reference to an excluded folder.

Before:

````text
The bundled `05_TEAM_AI_ONBOARDING/` guide trains teammates and helps their agent produce an individualized learning/implementation plan.
````

After:

````text
`AGENTS.md` and `CLAUDE.md` in this repository brief teammates and their AI agents; the original team onboarding guide is archived in the registration package (`05_TEAM_AI_ONBOARDING/`, not included in this repository).
````

**A9.12** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* "In this ZIP" is untrue for the repository.

Before:

````text
### 24.1 Frozen project sources in this ZIP

- `01_READ_ONLY_V2_BASELINE/VOICE_TO_SQL_PROJECT_HANDOVER_V2_FROZEN.md`: prior comprehensive V2 snapshot (31 sections), **unaltered**.
- `01_READ_ONLY_V2_BASELINE/AI_AGENT_STARTER_PROMPT_V2_FROZEN.md`: prior prompt, **unaltered**.
- `01_READ_ONLY_V2_BASELINE/MIU_FORM_V2_FROZEN_NOT_SUBMITTED.md`: prior six-field form draft, **unaltered**.
````

After:

````text
### 24.1 Frozen project sources (registration package; not in this repository)

These files remain, hash-verified and unaltered, in the registration package `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip`; `PROJECT_EVOLUTION.md` summarizes them.

- `01_READ_ONLY_V2_BASELINE/VOICE_TO_SQL_PROJECT_HANDOVER_V2_FROZEN.md` (registration package): prior comprehensive V2 snapshot (31 sections), **unaltered**.
- `01_READ_ONLY_V2_BASELINE/AI_AGENT_STARTER_PROMPT_V2_FROZEN.md` (registration package): prior prompt, **unaltered**.
- `01_READ_ONLY_V2_BASELINE/MIU_FORM_V2_FROZEN_NOT_SUBMITTED.md` (registration package): prior six-field form draft, **unaltered**.
````

**A9.13** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Local machine path replaced by an accurate description.

Before:

````text
- Text-to-SQL research package (independent, not modified): `Downloads/MIU_VoiceToSQL_V3_1_TextToSQL_Dataset_Research_2026-10-23/` (discovery report, verification log, evidence screenshots E1–E5).
````

After:

````text
- Text-to-SQL research package (independent, not modified; discovery report, verification log, evidence screenshots E1–E5): a separate local research folder dated 23 Oct 2026, kept outside both the registration package and this repository. The dataset facts used by the project are restated in R15–R19 above.
````

**A9.14** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Reference to excluded research records made explicit.

Before:

````text
The more detailed source/method map is inside `06_RESEARCH_AND_DATA/`.
````

After:

````text
The more detailed source/method map is archived in the registration package (`06_RESEARCH_AND_DATA/`, not included in this repository).
````

**A9.15** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Reading rule pointed to package-only files.

Before:

````text
1. Read this entire V3 file, the change log, and the team onboarding guide. Consult the **V2 frozen handover** for historical details, never to override explicit V3 deltas.
````

After:

````text
1. Read this entire V3.1 file, `PROJECT_STATUS.md`, `PROJECT_EVOLUTION.md` (decision index) and `AGENTS.md`. The **V2 frozen handover** (archived in the registration package, not in this repository) is for historical details only, never to override explicit V3 deltas.
````

**A9.16** · `docs/ARCHITECTURE.md (Part A)` (source `03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md`) · occurrences replaced: 1

*Reason:* "In this folder" is untrue for the repository.

Before:

````text
The team-approved figure is `System-Overview-3840x2160-v6.png` in this folder
````

After:

````text
The team-approved figure is `assets/System-Overview-3840x2160-v6.png`
````

**A9.17** · `docs/ARCHITECTURE.md (Part B)` (source `03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md`) · occurrences replaced: 1

*Reason:* "In this ZIP" is untrue for the repository.

Before:

````text
## Two meanings of the term 'read-only' in this ZIP
````

After:

````text
## Two meanings of the term 'read-only' in this project
````

**A9.18** · `docs/ARCHITECTURE.md (Part B)` (source `03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md`) · occurrences replaced: 1

*Reason:* Archive location made explicit.

Before:

````text
**Archived baseline:** Files in `01_READ_ONLY_V2_BASELINE/` are preserved without editing.
````

After:

````text
**Archived baseline:** The historical V2 and V3-draft snapshots in the registration package (`01_READ_ONLY_V2_BASELINE/`, `01B_READ_ONLY_V3_DRAFT_BASELINE/`; not part of this repository) are preserved without editing.
````

**A9.19** · `docs/ARCHITECTURE.md (Part B)` (source `03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md`) · occurrences replaced: 1

*Reason:* Archive location made explicit.

Before:

````text
**Archive note:** both `01_READ_ONLY_V2_BASELINE/` and `01B_READ_ONLY_V3_DRAFT_BASELINE/` are historical snapshots.
````

After:

````text
**Archive note:** both `01_READ_ONLY_V2_BASELINE/` and `01B_READ_ONLY_V3_DRAFT_BASELINE/` are historical snapshots in the registration package, not in this repository; see `PROJECT_EVOLUTION.md`.
````

**A9.20** · `docs/DATASET_STRATEGY.md` (source `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md`) · occurrences replaced: 1

*Reason:* References to excluded research records made explicit and self-contained.

Before:

````text
Evidence for every external source is in `V3_1_DATASET_VERIFICATION_LOG.md`; the reasoning is in `V3_1_DATASET_DEEP_RESEARCH.md`.
````

After:

````text
Evidence for every external source was recorded in the registration package's dataset verification log and the reasoning in its dataset deep-research record (`06_RESEARCH_AND_DATA/V3_1_DATASET_VERIFICATION_LOG.md`, `06_RESEARCH_AND_DATA/V3_1_DATASET_DEEP_RESEARCH.md`; neither is included in this repository). The conclusions this plan relies on (sources, links, licenses and roles) are restated in §11 and in `docs/SPECIFICATION.md` §14.5 and §24.2.
````

**A9.21** · `docs/DATASET_STRATEGY.md` (source `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md`) · occurrences replaced: 1

*Reason:* The cited invariants lived only in an excluded file; they are now inlined unchanged.

Before:

````text
The seven invariants in Research §3.2, plus: no product sold in a branch before it was first received there; the snapshot on the as-of date equals the ledger sum.
````

After:

````text
The seven ledger invariants below (originally specified in §3.2 of the dataset deep-research record, which is archived in the registration package and not included in this repository):

1. `on_hand(p,b,t) = Σ movements(p,b,≤t)`.
2. `on_hand ≥ 0` unless backorders are explicitly modeled (recommend: not modeled).
3. Every `SALE` movement maps 1:1 to a `sales_lines` row (same date, branch, product and quantity).
4. `RETURN_TO_STOCK` ≤ returned qty of the linked sale line and only for `restockable = true`.
5. Each `TRANSFER_OUT` has a matching `TRANSFER_IN` (same qty; in-transit lag explicit).
6. Snapshots equal ledger roll-ups exactly.
7. A threshold is chosen by the validity date, never "latest".

Plus: no product sold in a branch before it was first received there; the snapshot on the as-of date equals the ledger sum.
````

**A9.22** · `docs/DATASET_STRATEGY.md` (source `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md`) · occurrences replaced: 1

*Reason:* Package file name re-pointed to the repository document.

Before:

````text
- Full protocol: `V3_1_EVALUATION_NOTES_TRANSLATION_PIPELINE.md`.
````

After:

````text
- Full protocol: `docs/EVALUATION_PLAN.md`, Part B.
````

**A9.23** · `docs/DATASET_STRATEGY.md` (source `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md`) · occurrences replaced: 1

*Reason:* Local machine paths and an excluded file replaced by an accurate description.

Before:

````text
Sources: the independent research package `Downloads/MIU_VoiceToSQL_V3_1_TextToSQL_Dataset_Research_2026-10-23/` (not modified) and the team's independent review `Downloads/TEXT_TO_SQL_DATASET_RECOMMENDATION.md`. Licenses and sizes were re-checked on the Hugging Face API on 23 Oct 2026 (`V3_1_DATASET_VERIFICATION_LOG.md`, §23 Oct addendum).
````

After:

````text
Sources: an independent Text-to-SQL dataset research package (not modified) and the team's independent dataset review, both kept as local research records outside the registration package and this repository. Licenses and sizes were re-checked on the Hugging Face API on 23 Oct 2026 and recorded in the registration package's dataset verification log (23 Oct addendum; not included in this repository); the resulting links and licenses are given in the table below.
````

**A9.24** · `docs/REGISTRATION_FORM_FIELDS.md` (source `FINAL_FORM_COPY_PASTE.md`) · occurrences replaced: 1

*Reason:* Reference to a package-only file made explicit. Field text unchanged.

Before:

````text
Every value is extracted unchanged from `04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md`.
````

After:

````text
Every value is extracted unchanged from the registration package's form draft (`04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md`, not included in this repository).
````

**A9.25** · `docs/REGISTRATION_FORM_FIELDS.md` (source `FINAL_FORM_COPY_PASTE.md`) · occurrences replaced: 1

*Reason:* Repository location added. Field text unchanged.

Before:

````text
Field 6 file location in the package: `MIU_VoiceToSQL_V3_1_Team_Scope_Freeze_2026-10-22/03_ARCHITECTURE_AND_FIGMA/System-Overview-3840x2160-v6.png`
````

After:

````text
Field 6 file location in this repository: `assets/System-Overview-3840x2160-v6.png` (byte-identical to `MIU_VoiceToSQL_V3_1_Team_Scope_Freeze_2026-10-22/03_ARCHITECTURE_AND_FIGMA/System-Overview-3840x2160-v6.png` in the registration package).
````

### D-31 — Change-log entry

**D-31.1** · `docs/SPECIFICATION.md` (source `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md`) · occurrences replaced: 1

*Reason:* Change-log row for D-31.

Before:

````text


**End of the V3.1 team-approved planning specification.**
````

After:

````text

| 2026-10-23 | **Repository amendment (D-31)** | Clean-repository corrections only: package paths re-pointed to repository files or labelled as registration-package archives; V2 form filename corrected (§19); stale status wording updated (header snapshot, §1.2, §20 Phase 0, §26); see `docs/CHANGE_RECORD_D-31.md` | **No change to scope, title, Abstract, v6, architecture decisions or evaluation methodology; form NOT submitted** |

**End of the V3.1 team-approved planning specification.**
````
