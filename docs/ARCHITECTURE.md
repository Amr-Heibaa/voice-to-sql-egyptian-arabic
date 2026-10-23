# V3.1 Architecture and Governance Contract — Voice-to-SQL in Egyptian Arabic

> **Repository note (23 Oct 2026).** This file joins two current architecture documents from the final registration package. Both are **D-31 amended derivatives** (references and one misleading table heading changed; no architecture decision changed); see [CHANGE_RECORD_D-31.md](CHANGE_RECORD_D-31.md).
>
> - **Part A — System architecture and demonstration contract:** source `03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md`, original SHA-256 `78b9b9d456ed6ec251c576e0afc5f8e884a82c2f0e72091a8caec2d1843d043a`; derivative SHA-256 `b7e3d2ca37670a5121e7f5635619f3628f2426a60f875b3d596b9fa73678aba8`.
> - **Part B — Read-only SQL, schema approval and department governance contract:** source `03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md`, original SHA-256 `ce1384180d0a180ed15a03266356ad7c1bb80774ef5cf385ac2841ff7d15a0ba`; derivative SHA-256 `aacf664ed7eb2af4d1adb6d4c544e707e0a997f70c291fd6b8b2c71ad6745c9d`.
>
> The normative processing order is [SPECIFICATION.md §8.1](SPECIFICATION.md); the conceptual architecture is SPECIFICATION.md §7.

## Approved High-Level System Overview (v6)

![V3.1 High-Level System Overview, v6 — approved by the project team and the academic supervisor](../assets/System-Overview-3840x2160-v6.png)

*Team-approved (22 Oct 2026) and academic-supervisor-approved (recorded 23 Oct 2026). Not a university committee approval of the expanded scope. Byte-identical to the registration package (SHA-256 `62d3743e297e5eba7c0ea0e062643c7f756291777911942b73e1e2bddd280653`). Do not redesign, regenerate, edit or replace this image.*

---

## Part A — System architecture and demonstration contract

<!-- BEGIN AMENDED DERIVATIVE source="03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md" source_sha256="78b9b9d456ed6ec251c576e0afc5f8e884a82c2f0e72091a8caec2d1843d043a" derivative_sha256="b7e3d2ca37670a5121e7f5635619f3628f2426a60f875b3d596b9fa73678aba8" amendment="D-31" -->
# V3.1 System Architecture and Demonstration Contract

**State:** planned/approved by team as the target architecture; **not implemented**.

## One hub, three real workspaces

| Workspace | Data and approved metrics | Example spoken question (illustrative; planned targets: spec §14.3 and §15.4) | Security proof |
|---|---|---|---|
| **Sales** | `stores`, `products`, `sales_headers`, `sales_lines`, `returns`, `product_costs`; revenue/gross/net/profit only where required data exist | "مين أكتر فرع كسبان الشهر اللي فات؟" -> clarify revenue versus profit where material | HR-only data are inaccessible |
| **Inventory** | `stock_movements`/snapshots, `reorder_thresholds`, shared controlled `products`/`stores`; stock-on-hand, low stock | "إيه المنتجات اللي قربت تخلص في فرع إسكندرية؟" | Sales-restricted net-profit and HR records unavailable to Inventory-only user |
| **HR** | **synthetic only** `employees`, `departments`, `leave_requests`; active headcount, approved leave days, new hires if data support | "أنهي قسم عنده أكتر إجازات الشهر ده؟" | HR-only user cannot query Sales/Inventory restricted data; private HR columns filtered |

### High-level paths

**Analytics (TA-clarified pipeline, synchronized 23 Oct 2026; normative order in spec §8.1):** Authenticated user -> server resolves authorized workspace and permissions -> Voice/Text -> pretrained ASR -> editable, user-confirmed **Arabic transcript** (authoritative, retained throughout) -> **BIR + ambiguity detection on the original Arabic** with the workspace semantic catalog -> **Answer / Clarify / Abstain** (Clarify and Abstain execute no SQL). In parallel, Arabic transcript -> ambiguity-preserving **Arabic-to-English translation** (derived; an audit logs any collapsed ambiguity, e.g. "كسبان" -> "most profitable", and never changes the decision). After **Answer** only: English question + resolved BIR -> **English-to-SQL** -> AST / allowlist / department authorization / BIR↔SQL consistency guards -> SELECT via read-only role -> DB-grounded result/chart/trace. All models are pretrained; no mandatory fine-tuning.

**Schema Design:** Authorized designer -> incomplete natural-language application description -> SRR and explicit/inferred/unknown requirements -> proposed tables/columns/PK/FK/relationships + ERD -> validators -> human Admin approve/revise/reject -> versioned design artifact/registry. **Approval is not SQL DDL execution.**

**Integrated Inventory story:** Designer describes stock tracking -> AI proposes inventory tables and flags assumptions -> Admin requests changes and approves revised design -> independent operator validates and provisions matching schema in sandbox/demo data store -> operator loads coherent fictional data -> publisher approves catalog/views -> Inventory Manager asks a voice question -> system answers or clarifies under safe read-only SQL. Match approved schema version to provisioned version.

**Sales independence:** Sales research benchmark must run even if the Schema Design subsystem is unavailable.

**HR independence:** HR must not be merely a voice prompt over Sales schema. It needs own data, metrics and permissions, demonstrating real context switching.

## RBAC (suggested permission model; exact IAM implementation not chosen)

- `sales_analyst`: Sales approved views only.
- `inventory_analyst`: Inventory approved views and explicitly shared product/store dimensions only.
- `hr_analyst`: HR approved aggregate/minimized personnel data only; never direct broad row-level PII access.
- `designer`: create/revise Schema Design artifacts only.
- `admin`: review versioned proposals and approve metadata; may inspect auditable changes.
- `operator`: separate controlled provisioning/import tasks in isolated demonstration DB; **not a language model tool**.

Roles can be combined by explicit backend authorization, but no user is allowed to choose a new role by merely switching a UI card.

## Data readiness requirements

- Generate one fictional company with 3 clearly documented departments. Sales and Inventory relationships should be coherent, not automatically assume matching sales and stock without tested rules.
- Keep UCI Online Retail II, if used, in a separate evidence/experiment track; do not misrepresent it as fictional-company stock/HR data.
- Catalog versioning distinguishes approved metric definitions and aliases in all three workspaces.
- HR uses **synthetic-only data**, no real staff/personnel records, and limited fields.
- Evaluations on specific queries require a frozen seed and DB snapshot.

## Diagram requirements

The professor favors a brief, visual **high-level overview**, not the detailed flow listed above. The user has supplied the visual reference; Figma Make should follow its style while depicting three department cards, one Central Hub, Voice-to-SQL Analytics, AI Schema Design with Admin Review, and governed data. Put ASR/BIR/SQLGlot, SRR JSON, three baselines and audit detail **outside** the high-level figure. The team-approved figure is `assets/System-Overview-3840x2160-v6.png` (team- and supervisor-approved, not committee approval). **23 Oct 2026 compatibility note:** the speech-to-text and Arabic-to-English translation stages are deliberately not drawn, at the same level of abstraction as ASR/BIR/SQL-guard detail. The image is unchanged (SHA-256 verified). Any wish to show translation in the figure is a supervisor decision (spec Q15), not a reason to edit the approved image.
<!-- END AMENDED DERIVATIVE source="03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md" -->

---

## Part B — Read-only SQL, schema approval and department governance contract

<!-- BEGIN AMENDED DERIVATIVE source="03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md" source_sha256="ce1384180d0a180ed15a03266356ad7c1bb80774ef5cf385ac2841ff7d15a0ba" derivative_sha256="aacf664ed7eb2af4d1adb6d4c544e707e0a997f70c291fd6b8b2c71ad6745c9d" amendment="D-31" -->
# Read-Only SQL, Schema Approval, and Department Governance Contract

**Purpose:** This document prevents the most dangerous misunderstanding in the combined project: *a system that proposes database schemas is not allowed to execute unrestricted SQL through its Analytics endpoint*.

## Separate action classes

| Action | Allowed actor | Permission type | MVP execution rule |
|---|---|---|---|
| Query authorized department metric/data | Authenticated department user | `analytics.query` | SELECT only, vetted view/object set, guarded DB role |
| View own query SQL/intent | Same authorized user, if policy permits | `analytics.audit_read` | Redact sensitive values/logs |
| Import CSV/XLSX | Authorized operator | `data.load` | Isolated ingestion worker/credentials |
| Create/modify *draft schema artifact* | Designer | `schema.propose` | Store metadata draft, **not DDL** |
| Review proposal version | Admin | `schema.review` | Approve/request revisions/reject, auditable |
| Publish approved *metadata* | Admin/authorized publisher | `schema.publish` | Versioned registry and view mapping only |
| Execute CREATE/ALTER/DROP | NOT a public app action | Controlled sandbox operator (if separately approved) | Excluded from initial MVP |

## Rule R1: keep analytics credentials read-only

Use an `analyst_ro` PostgreSQL role or separate department-scoped read-only roles with `SELECT` on allowed analytic views, not source write tables. Revoke risky default grants, restrict `search_path`, use read-only transactions, timeouts, row limits, no dynamic SQL execution and audited, parameterized queries as appropriate. Keep the data loader's `loader_rw` separate. A parser alone does not establish security.

## Rule R2: authorize the department before constructing model context

The model can only access schema metadata and relation IDs for a department that the authenticated backend has authorized. Do not accept an arbitrary `department_id`, `workspace_id` or table name from LLM output as a permission grant. Reject cross-department queries at the server and database boundaries. RLS is optional and adds complexity; it must not be advertised as implemented unless configured and tested.

## Rule R3: design artifacts are inert until reviewed

The Schema Design service must **never** run proposed DDL against live databases. It can validate identifiers, FKs, columns and types and show an ERD or optional read-only DDL preview. `APPROVED` means the *reviewed design proposal* has passed human review; it does **not** mean the physical tables exist or contain data. Publishing an approved schema to the registry is distinct from provisioning and importing.

## Rule R4: record exact versions

Every answer and proposed schema should refer to `company_id`, `workspace_id`, `catalog_version`, `approved_schema_version`, `policy_version`, `run_id`, and (where appropriate) reviewer identity and date. Authorization and versions are set by the backend, not invented by the LLM.

## Rule R5: tests required before any AI/database linkage

1. `DROP TABLE`, `UPDATE`, `INSERT`, nested write CTE and multi-statement strings rejected.
2. `SELECT` referencing unauthorized schema/table/column rejected.
3. Injection hidden inside Arabic natural-language text cannot bypass allowlists.
4. Changing workspace in client payload does not change access permissions.
5. Unapproved schema proposal cannot be published by designer role.
6. Approval of a proposed schema does not trigger DDL execution.
7. Permissions are still enforced when SQL AST parser fails open or sees unusual constructs.
8. Query with no approved data/metric abstains; does not hallucinate records.

## Two meanings of the term 'read-only' in this project

**Archived baseline:** The historical V2 and V3-draft snapshots in the registration package (`01_READ_ONLY_V2_BASELINE/`, `01B_READ_ONLY_V3_DRAFT_BASELINE/`; not part of this repository) are preserved without editing. **Database mode:** All user-facing analytics queries must be safe **read-only SQL**. These are independent requirements, and both apply.

**Status:** Proposed engineering contract, not yet proven by implementation or tests.


## V3.1 additional three-department security gates

- Configure Sales, Inventory and HR as independent authorized contexts with one shared orchestration engine.
- Require positive read-only queries for each workspace and negative Sales-to-HR, HR-to-Sales, Inventory-to-HR and forged-workspace tests.
- Treat HR as high-sensitivity even with synthetic demo data; expose aggregates/minimized views, not unrestricted raw employee fields.
- An Admin-reviewed schema metadata artifact does not grant direct access across departments.
- Operator-only isolated schema provisioning is separated from Analytics credentials; no LLM-supplied CREATE/ALTER/DROP may execute.

**Archive note:** both `01_READ_ONLY_V2_BASELINE/` and `01B_READ_ONLY_V3_DRAFT_BASELINE/` are historical snapshots in the registration package, not in this repository; see `PROJECT_EVOLUTION.md`.
<!-- END AMENDED DERIVATIVE source="03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md" -->
