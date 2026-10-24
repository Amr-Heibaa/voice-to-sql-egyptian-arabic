# Change Record D-33 — TA-Approved Official Title

| Field | Value |
|---|---|
| Decision | **D-33** |
| Date | 2026-10-24 |
| Decision source | The Teaching Assistant explicitly approved the new official project title, as reported by the student in the D-33 instruction (24 Oct 2026) |
| New official title | **ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic** |
| Replaces | *Voice-to-SQL in Egyptian Arabic* (TA-approved 23 Oct 2026, D-29), kept as dated history |
| Approval level | TA approval of the title. **Not** formal committee approval of the expanded scope |
| Unchanged | The Abstract (verbatim) and Form Fields 2–6; scope (Sales, Inventory, HR; AI Schema Design with Admin review); the pipeline; read-only SQL; dataset strategy; evaluation methodology; the supervisor-approved v6 diagram; the GitHub repository name `voice-to-sql-egyptian-arabic` |
| Status | University registration **NOT SUBMITTED**; implementation **NOT STARTED**; custom datasets and recordings **PLANNED, not collected** |

## Provenance

D-33 is applied **on top of the D-31 derivatives** and changes two embedded documents. Their blocks are now marked `amendment="D-31,D-33"`. The original package hash is kept in `source_sha256`, and `derivative_sha256` is the hash after both amendments. **Neither block is byte-identical to its source.** The Field 2–6 boxes in `docs/REGISTRATION_FORM_FIELDS.md` are still byte-identical to the original `FINAL_FORM_COPY_PASTE.md` and are verified box by box. Applying D-31 and then the replacements below to the original package files reproduces both blocks exactly.

| Repository document | After D-31 (SHA-256) | After D-31 + D-33 (SHA-256) |
|---|---|---|
| `docs/SPECIFICATION.md` | `0032b8c945a81857d30c82a2075b97f5ecd90d151ab8bd336321187cdf312743` | `ce28cdbff729b1d38bb69ce296efc572f492d406368ed8a507cd666ccc48a1f0` |
| `docs/REGISTRATION_FORM_FIELDS.md` | `ec89264912b95773804fb366c83ef207db33b50fb5e59826f3fc8aa91e379a61` | `9a5eb9b44459c1330baff9b3a3eb698f263f7d2e03a9a56148f06f9edb28233f` |

## Authored files updated (outside embedded blocks)

- `README.md`: H1 heading and the official-title status row.
- `PROJECT_STATUS.md`: H1 heading, status rows, Field 1 row and the approvals table.
- `AGENTS.md`: project line, current-stage line and rule 1 (exact title); next decision number.
- `PROJECT_EVOLUTION.md`: H1 heading, timeline row, title history (D-29 marked superseded) and the decision index.
- `docs/README.md`: H1 heading, index and provenance table.
- The H1 headings of `docs/SPECIFICATION.md`, `docs/ARCHITECTURE.md`, `docs/DATASET_STRATEGY.md` and `docs/EVALUATION_PLAN.md`, and the repository notes of `docs/SPECIFICATION.md` and `docs/REGISTRATION_FORM_FIELDS.md`.

Historical references to *Voice-to-SQL in Egyptian Arabic* (D-28 and D-29 rows, timelines, earlier change records) are kept unchanged as dated history.

## Edits inside embedded blocks (11, before → after)

**T1** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* Snapshot line records the D-33 title update.

Before:

````text
repository amendment D-31, 23 October 2026)
````

After:

````text
repository amendment D-31, 23 October 2026; title update D-33, 24 October 2026)
````

**T2** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* Current official title replaced; the D-29 title is kept as dated history.

Before:

````text
**Official/form title:** ***Voice-to-SQL in Egyptian Arabic*** — **TA APPROVED** (23 Oct 2026, confirmed by the student). The TA had requested a shorter title than the working name above. No "(Company Ideas – IBM)" suffix is used unless the university separately requires it. This is TA approval of the title, not committee approval of the expanded scope. The short title does not narrow the V3.1 scope, which stays as specified here (Form Field 1, Q01, D-29).
````

After:

````text
**Official/form title:** ***ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*** — **TA APPROVED** (approval recorded 24 Oct 2026, as reported by the student; D-33). It replaces the earlier TA-approved short title *Voice-to-SQL in Egyptian Arabic* (23 Oct 2026, D-29), which is kept as history only. No category suffix (such as "(Company Ideas – IBM)") is used unless the university separately requires it. This is TA approval of the title, not committee approval of the expanded scope. The title does not change the V3.1 scope, which stays as specified here (Form Field 1, Q01, D-33).
````

**T3** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* History table (§2) gains a dated row for the title update.

Before:

````text


**Unclear transcript fragment:**
````

After:

````text

| Official title update, 24 Oct 2026 | The TA explicitly approved the new official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* (as reported by the student). | Form Field 1 and the current documents updated (D-33); the 23 Oct title is kept as history; scope, Abstract, Fields 2–6 and v6 unchanged; form NOT submitted. |

**Unclear transcript fragment:**
````

**T4** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* Phase 0 status note (§20) names the current title.

Before:

````text
the title (TA-approved, D-29),
````

After:

````text
the title (TA-approved, D-29; replaced on 24 Oct 2026 by the TA-approved *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*, D-33),
````

**T5** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* Form-status list (§19), Field 1.

Before:

````text
1. Project Title (**TA APPROVED 23 Oct 2026:** *Voice-to-SQL in Egyptian Arabic*; no category suffix unless separately required by the university).
````

After:

````text
1. Project Title (**TA APPROVED, recorded 24 Oct 2026 (D-33):** *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*; replaces the title TA-approved on 23 Oct 2026, *Voice-to-SQL in Egyptian Arabic* (D-29); no category suffix unless separately required by the university).
````

**T6** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* Open-decision table (§22): Q01 shows the current title and keeps the D-29 resolution as history.

Before:

````text
| Q01 | Exact official V3 project title | **Resolved 23 Oct 2026: TA APPROVED *Voice-to-SQL in Egyptian Arabic*** (confirmed by the student; D-29). No "(Company Ideas – IBM)" suffix unless the university separately requires it. Earlier options A/B were not selected. |
````

After:

````text
| Q01 | Exact official V3 project title | **Resolved, updated 24 Oct 2026: TA APPROVED *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*** (as reported by the student; D-33). No category suffix unless the university separately requires it. *History:* resolved 23 Oct 2026 as TA APPROVED *Voice-to-SQL in Egyptian Arabic* (D-29), now superseded; earlier options A/B were not selected. |
````

**T7** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* Next-step list (§26) keeps the 23 Oct fact and notes the supersession.

Before:

````text
(2) done: the TA approved the title *Voice-to-SQL in Egyptian Arabic* (Q01 resolved);
````

After:

````text
(2) done: the TA approved the title *Voice-to-SQL in Egyptian Arabic* (Q01 resolved; superseded on 24 Oct 2026 by the TA-approved title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic*, D-33);
````

**T8** · `docs/SPECIFICATION.md` · occurrences replaced: 1

*Reason:* Change-log row for D-33 (§27).

Before:

````text


**End of the V3.1 team-approved planning specification.**
````

After:

````text

| 2026-10-24 | **Official title update (D-33)** | TA explicitly approved the new official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* (as reported by the student); header, §2, §19, §20, §22 Q01 and §26 updated; Form Field 1 updated; earlier titles kept as history; see `docs/CHANGE_RECORD_D-33.md` | **Abstract, Fields 2–6, scope, architecture, datasets, evaluation and v6 unchanged; GitHub repository name unchanged; form NOT submitted** |

**End of the V3.1 team-approved planning specification.**
````

**T9** · `docs/REGISTRATION_FORM_FIELDS.md` · occurrences replaced: 1

*Reason:* Document header shows the current title.

Before:

````text
**Voice-to-SQL in Egyptian Arabic** · V3.1 · 23 October 2026 · Registration status: **NOT SUBMITTED**
````

After:

````text
**ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic** · V3.1 · 23 October 2026 (Field 1 updated 24 October 2026, D-33) · Registration status: **NOT SUBMITTED**
````

**T10** · `docs/REGISTRATION_FORM_FIELDS.md` · occurrences replaced: 1

*Reason:* States that Field 1 no longer comes unchanged from the package draft.

Before:

````text
Every value is extracted unchanged from the registration package's form draft (`04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md`, not included in this repository).
````

After:

````text
Every value is extracted unchanged from the registration package's form draft (`04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md`, not included in this repository), except Field 1, which was updated on 24 October 2026 to the newly TA-approved title (D-33); the package draft still holds the earlier title.
````

**T11** · `docs/REGISTRATION_FORM_FIELDS.md` · occurrences replaced: 1

*Reason:* Field 1 value replaced by the exact TA-approved title.

Before:

````text
## Field 1 — Project Title

```text
Voice-to-SQL in Egyptian Arabic
```
````

After:

````text
## Field 1 — Project Title

```text
ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic
```
````
