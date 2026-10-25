# PoC Interface Contract — DRAFT v0.1 (input to Gate G-A)

> **DRAFT, NOT APPROVED.** This is a starting point for `CQP-22` Phase A. It becomes **Interface Contract v1.0** only when Sayed, Abdelrahman, George and Abdallah each comment "Contract v1.0 agreed" on `CQP-22` (**Gate G-A, 28 Oct 2026**). Until then every field name, type and error code below may change. Nothing here is implemented.
>
> **Where the frozen version lives.** The approved v1.0 is recorded on `CQP-22` and in the University Drive (`05-PoC-Docs`). A public-safe copy may be proposed for this file through a pull request; the owner decides.

Design sources: [../SPECIFICATION.md](../SPECIFICATION.md) §8.1 (processing order), §8.3 (illustrative BIR), §8.4 (decision policy), §10.2 (execution safety), §17.1–§17.2 (logical boundaries and example endpoints, not finalized). Scope: [POC_KICKOFF.md](POC_KICKOFF.md).

## 1. General conventions (proposed)

- **`trace_id`**: one opaque identifier created when a question is submitted and carried, unchanged, by every object below. Every log line and every trace-panel entry includes it.
- **`contract_version`**: every object carries `"contract_version": "1.0"` after the gate; a mismatch is an error, not a silent fallback.
- **Language fields**: `_ar` fields hold Arabic text, `_en` fields English text.
- **Department**: the PoC has one workspace, `sales`. The value comes from server-side configuration, **never** from model output ([../SPECIFICATION.md](../SPECIFICATION.md) §8.3).
- **Examples** use synthetic values only.
- **Transport** (function calls or local HTTP) is decided at G-A; the objects are the same either way.

## 2. Original vs normalized Arabic

| Field | Produced by | Meaning | Rule |
|---|---|---|---|
| `transcript_ar_raw` | ASR (`CQP-23`) | What the ASR returned | Kept for the trace; never used for decisions |
| `question_ar` (`q_ar`) | User confirmation (UI, `CQP-25`) | The confirmed Arabic question, typed or edited transcript | **Authoritative.** Stored unchanged for the whole request |
| `question_ar_normalized` | BIR component (`CQP-24`) | A derived form for matching (for example unified alef/yaa forms, digits) | Used only for catalog matching; never shown as the user's words and never replaces `question_ar` |
| `question_en` (`q_en`) | Translation (`CQP-23`) | Derived English translation | Non-authoritative; may never resolve an ambiguity; used for Text-to-SQL only after ANSWER |

## 3. Objects (proposed)

### 3.1 `AsrResult` (owner: `CQP-23`)

```json
{
  "trace_id": "t-0001",
  "audio_id": "a-0001",
  "transcript_ar_raw": "<ASR output>",
  "confidence": null,
  "engine": "<engine name and version>",
  "error": null
}
```

`confidence` is optional and is never used alone to decide anything. Audio is not stored in Git.

### 3.2 `TranslationResult` (owner: `CQP-23`)

```json
{
  "trace_id": "t-0001",
  "text_ar_original": "<question_ar, unchanged>",
  "text_en": "<derived English translation>",
  "engine": "<engine name and version>",
  "error": null
}
```

The translator is instructed to preserve ambiguity rather than choose a reading ([../SPECIFICATION.md](../SPECIFICATION.md) §8.1 step 5).

### 3.3 `Bir` — minimal Business Intent Representation (owner: `CQP-24`)

A subset of the illustrative BIR in [../SPECIFICATION.md](../SPECIFICATION.md) §8.3, with the same field names where they overlap. Produced from `question_ar` and the catalog only.

```json
{
  "trace_id": "t-0001",
  "department_id": "sales",
  "intent_type": "rank",
  "metric_candidates": ["revenue", "transaction_count"],
  "resolved_metric": null,
  "dimensions": ["branch"],
  "filters": {},
  "time_expression": "<Arabic time phrase or null>",
  "time_range": null,
  "as_of_date": "<fixed ISO date for the demo>",
  "rank": {"order": "desc", "limit": 1},
  "ambiguity_flags": ["METRIC_UNRESOLVED"],
  "unsupported_reason": null
}
```

`department_id` is copied from server configuration, not from the model. Metric IDs must exist in the catalog. The Jira prompt in `CQP-22` uses shorter names (`intent`, `metric`, `dimension`, `ambiguous_slots`); the naming is a **G-A decision**, and this draft follows the specification.

### 3.4 `Decision` (owner: `CQP-24`)

```json
{
  "trace_id": "t-0001",
  "type": "CLARIFY",
  "reason": "METRIC_UNRESOLVED",
  "clarification_question_ar": "<one targeted question>",
  "options": [
    {"slot": "metric", "value": "revenue", "label_ar": "<label>"},
    {"slot": "metric", "value": "transaction_count", "label_ar": "<label>"}
  ]
}
```

`type` is exactly one of `ANSWER`, `CLARIFY`, `ABSTAIN`. ABSTAIN requires a specific `reason` (for example `MISSING_DATA`, `UNSUPPORTED_METRIC`, `WRITE_REQUEST`, `UNSAFE_SQL`, `CLARIFICATION_LIMIT`). The decision is deterministic given the BIR and the catalog; model self-reported confidence is never the only basis ([../SPECIFICATION.md](../SPECIFICATION.md) §8.4).

### 3.5 `ClarificationResponse` and clarification state (owners: `CQP-25` sends, `CQP-24` applies)

```json
{
  "trace_id": "t-0001",
  "slot": "metric",
  "chosen_option": "revenue"
}
```

State rules:

- At most **one** clarification turn per question. The server keeps the pending BIR keyed by `trace_id`.
- The choice must be one of the offered options; anything else is an error.
- The choice updates the **same** BIR (`resolved_metric`), then the policy runs again. A second unresolved ambiguity ends in ABSTAIN (`CLARIFICATION_LIMIT`).
- **No SQL is generated or executed while a clarification is pending.**

### 3.6 `SqlRequest` and `SqlResult` (owner: `CQP-26`)

```json
{
  "trace_id": "t-0001",
  "department": "sales",
  "sql": "<one SELECT generated after ANSWER>"
}
```

```json
{
  "trace_id": "t-0001",
  "sql": "<the SQL as checked>",
  "validated": true,
  "rejected_reason": null,
  "rows": [],
  "row_count": 0,
  "columns": [],
  "elapsed_ms": null
}
```

When `validated` is `false`, the SQL was **not executed**, `rows` is empty and `rejected_reason` names the rule (for example `NOT_SINGLE_SELECT`, `DDL_OR_DML`, `MULTI_STATEMENT`, `OBJECT_NOT_ALLOWED`). A rejection is turned into ABSTAIN (`UNSAFE_SQL`) by the orchestrator.

### 3.7 `Answer` (owner: `CQP-22` assembles; `CQP-25` displays)

```json
{
  "trace_id": "t-0001",
  "decision": "ANSWER",
  "text_en": "<answer built from the returned rows>",
  "text_ar": null,
  "interpretation": {"metric": "revenue", "time_range": "<range>", "filters": {}},
  "sql_shown": "<executed SQL>",
  "data_rows": []
}
```

Every number in `text_en` or `text_ar` comes from `data_rows`. If the rows are empty, the answer says so; it never invents a value.

## 4. Errors and fail-closed handling (proposed codes)

| Code | Raised by | Result for the user |
|---|---|---|
| `ASR_FAILED` | `CQP-23` | Ask the user to type the question; nothing else runs |
| `TRANSLATION_FAILED` | `CQP-23` | ABSTAIN with an explanation (no SQL without `q_en`) |
| `BIR_INVALID` | `CQP-24` | Schema validation failed: ABSTAIN |
| `CATALOG_MISSING_TERM` | `CQP-24` | ABSTAIN (`UNSUPPORTED_METRIC`) or CLARIFY, per policy |
| `SQL_REJECTED` | `CQP-26` | ABSTAIN (`UNSAFE_SQL`); the SQL is not executed |
| `DB_TIMEOUT` / `DB_ERROR` | `CQP-26` | Visible error; no partial or guessed numbers |
| `CONTRACT_VERSION_MISMATCH` | any | Visible error; stop |

Any unexpected exception ends in a visible error or ABSTAIN, never in an answer.

## 5. Safe execution boundary

- Only the guard in `CQP-26` may hand SQL to the database, and only through a **read-only** database user. No other component holds database credentials.
- The guard accepts exactly one `SELECT` over allow-listed objects; it rejects DDL, DML, multi-statements and non-allow-listed functions. Parser success alone is not security ([../SPECIFICATION.md](../SPECIFICATION.md) §10.2).
- Write-oriented natural-language requests are refused earlier, by the policy, with `WRITE_REQUEST`.
- Credentials come from environment variables, never from code or committed files.

## 6. Test inputs and expected behavior (to be finalized in the PoC scope)

| Test | Input mode | Expected decision | Expected database effect | Checked by |
|---|---|---|---|---|
| A clear question | typed, voice | ANSWER | One validated SELECT; real rows | `CQP-22` matrix |
| B ambiguous question, then a choice | typed, voice | CLARIFY → ANSWER | No SQL before the choice | `CQP-22` matrix |
| B with an invalid choice | typed | Error, then ABSTAIN | No SQL | `CQP-24` tests |
| C net profit without cost data | typed (voice SHOULD) | ABSTAIN `MISSING_DATA` | No SQL | `CQP-22` matrix |
| Write request in Arabic | typed | ABSTAIN `WRITE_REQUEST` | No SQL; row counts unchanged | `CQP-24`, `CQP-27` |
| Crafted `DELETE` / `DROP` / multi-statement SQL to the guard | direct | `validated: false` | Not executed; row counts unchanged | `CQP-26`, `CQP-27` |

Actual results are recorded with date and tester in the test matrix (University Drive `05-PoC-Docs`), never in this draft.

## 7. Integration ownership

Amr (`CQP-22`) owns the contract, its versioning, the end-to-end driver and the integration order: data and guard with BIR first, then voice and translation, then the UI. Each component owner keeps their objects valid against the frozen contract and announces any needed change on `CQP-22` before making it.
