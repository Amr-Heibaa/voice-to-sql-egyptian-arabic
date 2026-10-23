# V3.1 Specification — Voice-to-SQL in Egyptian Arabic

> **Repository note (23 Oct 2026).** The block between the `BEGIN AMENDED DERIVATIVE` and `END AMENDED DERIVATIVE` markers is the **team-approved V3.1 specification**, the project's **canonical source of truth**.
>
> - **Source:** `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md` in `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip`. **Original source SHA-256:** `5116f13cfe3909dcb37cb95cef0301e203ab6fbe45541292c23e6030c1c82fc6` (kept for provenance).
> - **This is an amended derivative, not a byte-identical copy.** Repository amendment **D-31** (23 Oct 2026) changed only references and stale status wording; every change, with its before and after text, is listed in [CHANGE_RECORD_D-31.md](CHANGE_RECORD_D-31.md). **Derivative SHA-256:** `0032b8c945a81857d30c82a2075b97f5ecd90d151ab8bd336321187cdf312743`.
> - Scope, design, architecture decisions, the evaluation methodology, the title and the Abstract are unchanged by D-31.
> - Status statements inside the block are dated 22–23 Oct 2026; the live status is [PROJECT_STATUS.md](../PROJECT_STATUS.md). Paths written as `docs/…`, `assets/…`, `README.md`, `PROJECT_STATUS.md`, `PROJECT_EVOLUTION.md` or `AGENTS.md` are repository paths; any `0x_…` path is explicitly labelled as part of the registration package and is not in this repository.
> - Do **not** edit the block casually; follow the change protocol in [AGENTS.md](../AGENTS.md#5-change-protocol).

<!-- BEGIN AMENDED DERIVATIVE source="02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md" source_sha256="5116f13cfe3909dcb37cb95cef0301e203ab6fbe45541292c23e6030c1c82fc6" derivative_sha256="0032b8c945a81857d30c82a2075b97f5ecd90d151ab8bd336321187cdf312743" amendment="D-31" -->
# MIU Graduation Project — V3.1 Team-Approved Scope Specification and AI Agent Handover

**Working project name:** Voice-to-SQL in Egyptian Arabic with Ambiguity-Aware Selective Answering: A Multi-Department AI Data Hub with Admin-Reviewed Schema Design  
**Official/form title:** ***Voice-to-SQL in Egyptian Arabic*** — **TA APPROVED** (23 Oct 2026, confirmed by the student). The TA had requested a shorter title than the working name above. No "(Company Ideas – IBM)" suffix is used unless the university separately requires it. This is TA approval of the title, not committee approval of the expanded scope. The short title does not narrow the V3.1 scope, which stays as specified here (Form Field 1, Q01, D-29). The archived V2 wording is unchanged.  
**Final registration synchronization (23 Oct 2026):** the TA clarified the processing pipeline (Egyptian-Arabic voice → speech-to-text → Arabic transcript → Arabic-to-English translation → English question → English-to-SQL → guarded execution), and §8.1 now specifies how this order preserves the Arabic-anchored ambiguity contribution. The TA replied positively to the Text-to-SQL dataset evidence (AraSpider, Spider, BIRD Mini-Dev). That reply is evidence support, not formal approval of the form wording, title, scope or architecture. The TA approved the revised short Abstract (as reported by the student). The exact 213-word text is **confirmed by the student as final** and is in Form Field 2 verbatim (Q13 resolved). Form status: **NOT SUBMITTED**.  
**Snapshot:** 22 October 2026 (V3.1 baseline; last synchronized 23 October 2026 through D-30; repository amendment D-31, 23 October 2026) · Misr International University (MIU) · Software Engineering graduation project  
**Version:** V3.1 — **TEAM-APPROVED PLANNING BASELINE**, NOT a submitted form or formal committee-approved implementation. This supersedes the V3.0 scope draft, not its historical record.  
**Authority:** The TA accepted the multi-department Central Hub direction and proposed Admin-reviewed schema assistance; a professor advised implementing feasible expansion instead of relegating every capability to future work. The **team/user explicitly selected Sales, Inventory, and HR as three mandatory demonstration workspaces**. This is a team scope decision, not evidence of university committee approval or completed software.  
**Implementation:** No codebase, deployed application, completed dataset, trained models, study participants, or experiment outputs have been furnished for verification. All software designs here are **PROPOSED**, not implemented.  
**High-level system overview graphic:** The user has now provided a visual reference and requested a **Figma Make prompt** (both are historical inputs kept in the registration package, not in this repository). The team has since **approved `assets/System-Overview-3840x2160-v6.png`** (PNG, 3840 × 2160) as the High-Level System Overview; it is **approved by the project team and the academic supervisor** (supervisor approval recorded 23 Oct 2026 on the user's confirmation), **not committee-approved**, and not yet attached to a submitted form. Do not substitute the conceptual architecture for the approved diagram, and do not redesign or replace it.

> **How to use this file:** This file is the current **V3.1 team-approved planning source of truth**. Read `README.md`, `PROJECT_STATUS.md` and `PROJECT_EVOLUTION.md` (which condenses the V3 → V3.1 decision changelog) for context. The V2 and V3-draft snapshots remain immutable historical records in the registration package; they are not part of this repository and are summarized in `PROJECT_EVOLUTION.md`. The official university form is not filled/submitted, and the team-approved diagram (`System-Overview-3840x2160-v6.png`) is not yet attached to a submitted form.

---

## V3.1 team-scope acceptance gate (effective 22 October 2026)

**Status terminology:** The team has **approved this planning scope**. The system is **NOT implemented**, the official MIU form remains **UNFILLED/UNSUBMITTED**, the extended scope is **NOT confirmed as committee-approved**, and the high-level diagram is **team-approved (v6: `System-Overview-3840x2160-v6.png`), not committee-approved**. The user's supplied style reference and the bundled Figma Make prompt were the inputs for that diagram.

**Must be demonstrably working at graduation MVP:**

1. **Sales:** existing Voice-to-SQL voice/text path with BIR, ambiguity-aware selective answering, read-only SQL and rigorous P2-versus-P4 primary evaluation.
2. **Inventory:** separate authorized analytics workspace; a concrete schema-design proposal reviewed by Admin; after **separate operator-controlled provisioning and data loading**, a real end-to-end query about stock/reorder values with explicit metric rules.
3. **HR:** a **third mandatory, working workspace** using synthetic-only employee/department/leave data, its own governed metrics, both typed and spoken Egyptian-Arabic analytics, and cross-department access denial; **not** a full HR information system.
4. **Central Hub:** one authenticated shared platform and one reusable analytics stack selecting approved catalogs/views/policies for the active workspace, not three hard-coded independent apps.
5. **AI Schema Design:** user submits an incomplete idea, AI proposes structured requirements and relational schema with assumptions/questions, Admin reviews a versioned design artifact; approval **does not execute DDL**. A safe isolated demonstration environment may be provisioned separately by an operator for the Inventory bridge.
6. **Research evaluation:** P2/P4 analytics study remains **primary**; schema design quality/review remains **secondary**; permissions/hub integration are mandatory verification. Corpus counts are proposed targets, not existing results.

**Reference-sensitive deliverable:** A compact high-level diagram with Sales/Inventory/HR, common Hub, two modes, Admin Review and governed data is required for the form. The team-approved result is `assets/System-Overview-3840x2160-v6.png`; do not redesign or replace it.

---

## 1. Executive overview — revised for the TA's approved direction

The project is a proposed **single-company AI-powered data hub** whose shared conversational interface serves multiple departments, initially through a bounded demonstration. It has two complementary but distinct workflows: **(A) reliable business-data querying with Egyptian-Arabic voice/text** and **(B) AI-assisted database-schema planning from incomplete natural-language application requirements**. Each department operates through an explicitly selected workspace with approved metadata, business meanings, data access and permitted operations. Administrators review schema proposals before they become approved artifacts; ordinary questions cannot modify live databases.

For analytics, the existing research core remains unchanged: speech-to-text with an editable transcript; an ambiguity-preserving **Arabic-to-English translation** that feeds **English question-to-SQL** generation (TA-clarified pipeline, 23 Oct 2026; the original Arabic stays authoritative for intent, §8.1); **Business Intent Representation (BIR)**; **business-metric, entity and time resolution**; detection of material ambiguity; an explicit **Answer / Clarify / Abstain** policy; guarded read-only PostgreSQL SQL; and verifiable tables/charts with the interpretation and SQL trace. For database design, a developer or other authorized designer describes an application at a high level—even with missing requirements—and the AI proposes entities, tables, fields, data types, keys, cardinalities and relationships, explains assumptions and questions, and submits a reviewable **draft**, never self-authorizing database changes.

The central hub is **a shared AI application layer across departments**, **not** a new ERP, **not** automatic implementation of complete apps, **not** a universal cross-domain system already tested, and **not** proof of a new market. The **team-selected graduation MVP includes three functional workspaces: Sales, Inventory, and HR**, for **one explicitly synthetic demonstration organization**. Sales anchors the primary analytics study; Inventory demonstrates the schema-proposal-to-approved-metadata-to-analytics bridge; HR demonstrates a different business domain and strict access isolation using fictitious employee records. Multi-company deployment and arbitrary industry coverage remain out of scope. Academic registration of this precise scope is still pending.

**One-sentence positioning (provisional):** *A governed, department-aware AI data hub that helps teams propose database structures from incomplete requirements and then ask trustworthy Egyptian-Arabic voice/text questions over approved business data.*

### 1.1 Status legend

- **CONFIRMED HISTORY**: Supported by the existing plan, official original concept, or the user's report of the TA discussion.
- **TA-APPROVED DIRECTION**: Multi-department Central Hub was accepted by the TA; not automatically a university-committee commitment.
- **TA-REQUESTED**: AI-assisted schema design and administrator supervision were explicitly suggested by the TA.
- **PROPOSED V3 DESIGN**: Our structured recommendation for implementation, to be reviewed and locked before coding.
- **PENDING DECISION**: Requires team/academic input; do not silently resolve.
- **UNVERIFIED**: No primary artifact, execution, license, test or confirmation was supplied.
- **DEFERRED**: Outside the proposed graduation MVP.

### 1.2 Primary context priorities for every AI agent

1. The user's **newest explicit decisions** override earlier recommendations, and actual verified repository files override conceptual guesses about implementation.
2. This V3.1 specification supersedes the V2 and V3-draft design descriptions *where stated*; the untouched V2 and V3-draft snapshots (archived in the registration package and summarized in `PROJECT_EVOLUTION.md`) record history and research details.
3. The user has **not yet filled or submitted** the university form. Do not describe V3 as formally registered or committee-approved.
4. The user has supplied a **high-level overview reference image** and requested a Figma Make prompt. That reference image (visual style only; it depicts a different, older project) and the Figma Make prompt were the historical inputs for the figure; both are kept in the registration package, not in this repository. The rendered figure is `assets/System-Overview-3840x2160-v6.png`, approved by the project team and the academic supervisor; do not claim committee approval.
5. Preserve the original Egyptian-Arabic **voice** requirement. Do not silently downgrade the mandatory voice path to typed-only.
6. Do not claim novelty in generic Text-to-SQL, schema generation, natural-language interfaces, semantic layers, or question clarification.

---

## 2. History, rationale, and what changed

| Stage | What happened | Result |
|---|---|---|
| University's original concept | Egyptian-Arabic Voice-to-SQL for business analytics over a realistic retail database; ASR, schema-aware LLM, SQL guard, charts and evaluation. | The project must retain voice, actual query execution, and evaluation. |
| V2 research refinement, 20–21 Oct 2026 | Natural-language querying is already supported by competitors; the team focused on **silent semantic errors** in business questions. | Retail-first M1–M8 and primary P2-vs-P4 study. |
| Team's existing three improvements | Structured **Business Intent Understanding/BIR**, **Ambiguity Detection with Clarification**, and **Selective Answering (Answer / Clarify / Abstain)**. | The TA's mention of the three added features refers to these *already present* improvements. |
| TA's new discussion | A **Central Hub** for departments across companies/domains, plus an AI capability to suggest tables, schema and relations from incomplete application requirements under Admin supervision. | Broaden the platform vision without discarding BIR and reliability. |
| User's latest confirmation | The TA **agreed to the Central Hub addition**. | Start V3 scope integration and prepare the official form; not evidence of committee approval. |
| V3.1 team freeze, 22 Oct 2026 | Professor advised implementing feasible expansion; team confirmed three mandatory functional workspaces, including HR; user supplied an overview visual reference and requested a Figma Make prompt. | New V3.1 team scope freeze, renewed six-field form draft, reference-driven diagram prompt (the team-approved diagram v6 followed the same day); official registration still pending. |
| Final registration preparation, 23 Oct 2026 | TA approved the revised short Abstract, asked for a shorter title, clarified the pipeline (voice → speech-to-text → Arabic-to-English translation → English-to-SQL), and replied positively ("TOUHFA — Elhamdullah") to three Text-to-SQL dataset screenshots (AraSpider, Spider, BIRD Mini-Dev). | Pipeline (§8.1), dataset references (§14.5), evaluation (§15) and form Fields 4–5 synchronized; later the same day the student confirmed the final Abstract text (D-26/D-27) and the TA approved the title *Voice-to-SQL in Egyptian Arabic* (D-29); form NOT submitted. |

**Unclear transcript fragment:** The TA also said to add a 'SQL' aspect, but the recording alone does not establish whether she means DDL previews, hand-written SQL assistance, or existing SQL generation. **Do not invent a third separately approved SQL feature.** This is a pending clarification and should not change the read-only query contract. *Update 23 Oct 2026:* the TA's later clarification of the pipeline (Arabic-to-English translation followed by **English-to-SQL**) may be what that remark meant, but nothing confirms the link, so Q07 stays open and no DDL or SQL-authoring feature is added.

### 2.1 Non-goals derived from history

- Replacing or competing feature-for-feature with Power BI, Databricks Genie, Power Apps, ERPs or comprehensive database-design suites.
- Claiming that combining two mature categories is inherently novel or creates proven market demand.
- Building and maintaining every enterprise department and every domain at production grade for the graduation MVP.
- Building an autonomous agent that edits production databases, creates complete web applications, or uses unscoped credentials.

---

## 3. Objectives, contribution, and success conditions

### 3.1 Product objectives

**O1 — Accessibility:** Managers can obtain grounded analytical answers without typing SQL, using voice or text, initially in Egyptian Arabic.

**O2 — Trustworthiness:** A business question's meaning is represented explicitly and ambiguous/unanswerable requests are not silently converted into authoritative but semantically incorrect numerical answers.

**O3 — Shared departmental experience:** Sales, Inventory **and HR** each operate as a functioning authorized workspace in one AI hub, with genuinely distinct approved schemas, metrics, permissions and tests.

**O4 — Assisted database modeling:** An authorized user can describe an application without enumerating all requirements; the AI proposes a reviewable relational design and identifies missing decisions.

**O5 — Human control:** An Admin must approve schema versions; querying cannot perform schema mutations, and review is auditable.

**O6 — Falsifiable evaluation:** Compare methods fairly against strong baselines and report error/coverage tradeoffs and schema-review quality honestly.

### 3.2 Central research hypothesis retained from V2

> **H-A (primary analytics):** Given matched business context, database snapshots, model constraints and clarification permissions, an explicit BIR plus selective-answering policy (P4) reduces materially incorrect direct business answers relative to a strong clarification-enabled LLM baseline (P2), while retaining usable answer coverage on Egyptian-Arabic voice/text retail questions.

### 3.3 New bounded hypotheses introduced for V3

> **H-S (schema-design, provisional):** Structured requirement extraction, explicit assumption/clarification handling, validation and human review yield more requirement-faithful, reviewable schema proposals than direct LLM schema prompting on a bounded set of incomplete briefs.

> **H-H (hub, engineering):** A shared analysis stack can correctly select department-specific context and enforce database authorization boundaries for all three mandatory demonstrated workspaces (Sales, Inventory, and HR) without cross-department data exposure.

> **H-M (market, unverified):** A subset of technical designers and business users may value an integrated schema-planning and conversational analytics workflow, rather than separately configured tools. This requires interviews, workflows and usability evidence; existing SME digitization statistics are not proof.

**Important:** V3 now has **two distinct evaluation tracks plus integration tests**. A result on SQL cannot automatically validate the schema-generation claim, and approval-workflow testing cannot establish market demand.

---

## 4. Users, roles, access, and department model

| Persona | Intended action | Access boundary |
|---|---|---|
| Business analyst/manager | Select own department; ask typed or spoken questions; view permitted results/charts. | Read-only views and preapproved metrics for that department. |
| Department lead | Review definitions and proposed datasets; report ambiguous terminology. | Approved department-specific metadata, not global administrator access. |
| Developer / database designer | Describe an application; examine proposed tables/fields/relations and ERD; revise submission. | Can create/revise draft schema proposals, cannot promote unapproved designs or execute DDL. |
| Admin / academic reviewer | Accept, reject, request revisions or publish a schema/catalog configuration; review audit trail and departmental rights. | Explicit authenticated approval and optional controlled sandbox provisioning; no inferred approval. |
| Researcher / QA | Run fixed evaluation sets and audit errors. | Sanitized/synthetic data and test environments; credentials must not be exposed. |

**Tenant model:** one demo company only. **Department** means an authorization/context boundary within that company. A department is not the same as a separate tenant, and 'multi-domain' means *architectural extensibility*, not full production-ready generality.

**Department selection — confirmed TEAM scope decision:** **Sales + Inventory + HR are mandatory functional MVP workspaces** within one fictitious demo company. HR requires a dedicated **synthetic-only** HR schema/metric catalog, a usable voice/text query journey and tested HR-only access controls. The university committee has not yet formally approved this expanded scope.

### 4.1 Example user stories

- As a Sales manager, I ask which branch had the highest net sales last month and see the approved definition of net sales.
- As an Inventory manager, I ask which products are below an approved reorder threshold; if no threshold exists, the hub clarifies or abstains.
- As an HR user in a **mandatory functioning MVP workspace**, I ask about approved headcount/leave metrics through voice or text and cannot access Sales/Inventory data outside my permission scope.
- As a developer, I explain a library/clinic/retail application and obtain suggested tables, keys, relationships and a list of assumptions.
- As an Admin, I see a proposed schema diff and unresolved issues and can approve or reject a **versioned design artifact**.
- As a student evaluator, I run P2 and P4 on identical questions, permissions, metrics and DB snapshots and evaluate both answer quality and access-denial behavior.

---

## 5. Scope matrix and MVP boundaries

| Component | V2 relationship | Proposed V3 MVP decision | Status |
|---|---|---|---|
| Egyptian-Arabic **voice** and typed questions | Retained | Mandatory end-to-end path including editable ASR transcript | V2 baseline; retained |
| Arabic-to-English translation → English question-to-SQL | P3 ablation in V2/V3 | Mandatory stage of the analytics path (pretrained model, no training); translation is non-authoritative and must preserve ambiguity; BIR/ambiguity checks stay on the original Arabic (§8.1) | TA-clarified pipeline, 23 Oct 2026 |
| BIR / semantic catalog | Retained | Mandatory metric/entity/date interpretation and provenance | V2 baseline; retained |
| Ambiguity Detection + Clarify | Retained | Mandatory; material business uncertainty, one focused clarification | V2 baseline; retained |
| Answer / Clarify / Abstain | Retained | Mandatory deterministic/structured decision policy | V2 baseline; retained |
| Read-only SQL + dashboard | Retained | Mandatory DB permission controls, AST checks, result/chart/SQL trace | V2 baseline; retained |
| Data import + benchmarks | Retained | Mandatory retail CSV/XLSX pipeline and P2-vs-P4 evaluation | V2 baseline; retained |
| Central Hub shell | New | Shared interface, **three functioning department contexts (Sales, Inventory, HR)** and server-enforced role-aware routing | Mandatory team-selected V3.1 scope |
| AI-assisted schema design | New | Requirements brief → draft tables/relations → validated preview → Admin review | TA-requested, implementation proposed |
| Schema/Business Metadata Registry | New shared infrastructure | Versioned approved snapshots usable by both modes | V3 proposed |
| Automatic DDL execution | Not in V2 | **Exclude from ordinary app path**; optional sandbox-only later under explicit approval | DEFERRED |
| Production ERP/live application generation | Not in V2 | Excluded | DEFERRED |
| HR department, bounded scope | New | **Mandatory functioning HR workspace**: synthetic employee/leave data, catalog, voice/text questions, secure isolation tests | Required V3.1 planned deliverable |
| Full HR suite, Finance/Medical domains | Not in V2 | Payroll, recruiting, HR workflow engine, medical/finance production support excluded | DEFERRED |
| Cross-company multi-tenancy | V2 excluded | Still excluded | DEFERRED |
| Full multi-turn agent | V2 excluded | Still excluded apart from one clarification and bounded schema revision | DEFERRED |

**Scope principle:** Make the platform *designed for multiple domains* while validating the *shipped MVP* on a limited, explicit set of departments and domains. Do not convert the marketing phrase 'any department, any domain' into an unbounded delivery promise.

---

## 6. Functional modules: retain M1–M8, add M9–M10

| ID | Module | Expected deliverable | End-to-end completion proof |
|---|---|---|---|
| **M1** | Retail CSV/XLSX import | Deterministic source mapping, validation, idempotent load to project-controlled PostgreSQL | Repeated import produces consistent records, corrupt data rejected, audit record exists. |
| **M2** | Retail database + approved metric catalog | Six-table canonical retail model, documented metrics, business rules | Manually verified calculations on fixed database snapshots. |
| **M3** | Egyptian-Arabic aliases/lexicon | Metric synonyms, product/branch aliases, numeric/date expressions, code-switch cases | Resolver test cases include clear and ambiguous terms. |
| **M4** | Structured Business Intent + selective policy | BIR extraction + deterministic resolution + Answer/Clarify/Abstain with one clarification | Ambiguous/unanswerable examples route correctly with explanations. |
| **M5** | Safe SQL query path | Schema-grounded SQL, structural & BIR checks, read-only DB access, result formatting | Mutation and unauthorized-object tests blocked; allowed SELECT returns gold result. |
| **M6** | Voice path | ASR → editable transcript → same pipeline as typed questions | Paired voice/text tests replayable with transcripts. |
| **M7** | Hub analytics interface | Department selector (Sales / Inventory / HR), voice/text input, clarification, answer/chart, understood intent and SQL trace | Successful **three-workspace** demonstration with negative permission tests. |
| **M8** | Evaluation & V&V harness | P0–P4 controlled baselines, annotated data, reproducible reporting | Fixed-run config and risk-coverage results, not just demo screenshots. |
| **M9** | AI Schema Design & Admin Review | Requirements intake, proposed tables/columns/keys/FKs, assumptions, ERD/diff, review states | Admin can accept/reject; draft never executes DDL. |
| **M10** | Department-Aware Registry & Governance | **Three functioning workspaces** with department-specific approved schemas/catalogs, access policy, provenance and audit | Sales, Inventory and HR queries work using one shared engine; unauthorized cross-department queries are denied. |

**Status of every module M1–M10:** Planned/design only, not marked implemented or tested. IDs M9/M10 are new planning identifiers, not official faculty numbering.

---

## 7. Revised conceptual architecture — not the final form diagram

The user has now supplied the professor-style **high-level overview visual reference** and requested a matching Figma Make prompt. The following is technical prose architecture; the **team-approved figure** for the form is `assets/System-Overview-3840x2160-v6.png`.

```
Browser / Web UI
  [company context] [authorized department] [Analytics | Schema Design]
                   |
        Auth / Role + Department Context
                   |
         Shared AI Application Hub
          /                   \
      ANALYTICS               SCHEMA DESIGN
   voice/text intake      application description
   ASR + transcript       structured requirements (SRR)
   BIR on Arabic text    proposed entities / PK / FK
   approved catalog      assumptions / targeted questions
   AR->EN translation    non-executing schema checks
   (derived, audited)    draft ERD / schema diff
   answer / clarify               |
   / abstain                      |
   EN-to-SQL, guarded             |
   SELECT                         |
          \                      Admin Review
           \                      /
          Versioned Approved Metadata Registry
             |         |        |
        department ACL   catalog   schema version
             |
        Controlled Department Data Sources
     [project-controlled PostgreSQL, curated views]
             |
       Grounded answers / audit & evaluation
```

**Architectural separation:** V3 has **two different intent schemas**: `BIR` for querying and `SRR` (proposed name: *Schema Requirements Representation*) for designing. Reusing a shared uncertainty and approval philosophy is reasonable; forcing an application-design requirement into the analytical BIR contract is not.

### 7.1 Control plane vs data plane

- **Control plane:** users/roles, company/dept membership, approved schema metadata, metric catalogs, policy versions, schema proposal review states, audit, benchmark configs.
- **Data plane:** imported departmental transaction data and read-only SELECT execution. Department data can be in one database with isolated schemas/views or in separate sources; no mandatory single monolithic database.
- **AI inference boundary:** model outputs are untrusted **proposals**; policy, approvals, permissions, parser checks and execution guards run outside the model.

### 7.2 Department routing decision

To reduce scope and avoid accidental data access, the **MVP UI requires an explicit department/workspace selection**; backend authorization checks that choice. Automatic inference of a department from a question is optional and may never grant access. Similarly the two modes are selected explicitly; an LLM need not decide whether a user intended to query or design.

### 7.3 Dependency between the two workflows

A query can work on **already-approved/imported** schemas without first running Schema Design. Conversely, an approved schema proposal with no tables provisioned or data loaded **cannot yield analytics**. A safe integrated demonstration is:

1. Describe an application; receive draft schema and questions.
2. Admin approves a versioned schema *design artifact*.
3. An operator **separately** provisions a sandbox schema and loads synthetic/sample data using controlled tooling (if included in the demo).
4. Publish an approved read-only view/catalog configuration.
5. The user queries the resulting dataset through Analytics, producing an answer/clarification/abstention.

Never claim schema approval automatically creates the whole application or fills tables with business data.

---

## 8. Analytics workflow and core V2 behavior

### 8.1 Processing stages (synchronized with the TA-clarified pipeline, 23 Oct 2026)

**TA-clarified pipeline:** Egyptian-Arabic voice → speech-to-text → Arabic transcript → Arabic-to-English translation → English natural-language question → English-to-SQL → guarded SQL execution. **Contribution-preserving rule:** the English translation is a *derived, non-authoritative* artifact used for SQL generation. Business intent, ambiguity detection and the Answer/Clarify/Abstain decision are anchored on the **original confirmed Egyptian-Arabic transcript** and the approved semantic catalog. Translation may never resolve an ambiguity; only the user (through the single clarification) or an approved catalog rule may. All models are pretrained and used with prompting and catalog guidance, without mandatory fine-tuning or training from scratch.

1. **Authorization gate.** The user authenticates and explicitly selects an authorized **department** and `Analytics` mode. Unauthorized workspace requests are denied here, before any model call.
2. **Input and transcript.** The user types Egyptian Arabic or speaks. A pretrained ASR model (optionally biased with catalog vocabulary) produces a **visible, editable Arabic transcript**, and the user confirms it before semantic processing. The confirmed text `q_ar` is the **authoritative question** and is retained, unchanged, for the whole request (audit, BIR, clarification and evaluation). Typed input skips ASR, and `q_ar` is the typed text.
3. **Approved context loading.** The backend loads **only** the selected workspace's approved schema/views, metric definitions, Arabic/English aliases (`name_ar`/`name_en`), time policy and as-of date.
4. **Business intent on the Arabic (authoritative).** The LLM receives `q_ar` plus the approved catalog and outputs schema-validated `BIR` JSON. It does **not** receive the English translation, so a translation cannot leak an interpretation into the intent. Deterministic resolvers then check metric, time, entity aliases and data availability, and a catalog lexicon of known ambiguous Egyptian-Arabic terms (e.g., "كسبان" → {net_sales, gross_profit}) sets ambiguity flags directly from the Arabic wording.
5. **Ambiguity-preserving translation (parallel to step 4, derived).** A pretrained translation or language model translates `q_ar` into English `q_en`. It is instructed to preserve ambiguity, keep catalog entity names consistent with `name_en`, and mark any catalog-flagged ambiguous Arabic term (e.g., *"earned the most [source term: كسبان, unresolved]"*) instead of choosing a reading. A deterministic **translation audit** compares `q_en` with the BIR's catalog matches. It logs any collapsed ambiguity (e.g., "most profitable" for "كسبان") and any dropped or changed entity. **The audit never changes the decision.** The BIR from step 4 governs. For evaluation, `q_en` is computed once per item and condition and cached.
6. **Decision policy (before any SQL).** An independent deterministic policy selects exactly one outcome: **Answer**, **Clarify**, or **Abstain**, based on the Arabic-anchored BIR, resolver results and authorization context.
7. `Clarify`: ask one targeted, actionable question in Egyptian Arabic. The user's choice updates the *same* BIR (e.g., `resolved_metric = gross_profit`), and the policy runs again. **No SQL is generated or executed while a clarification is pending.** Repeated free-form dialogue is not required, and the MVP allows one clarification turn.
8. `Abstain`: give a specific reason (missing data, unauthorized view, unsupported concept, critical unresolved meaning). **No SQL is generated or executed.**
9. `Answer` → **English question-to-SQL.** Only now does the LLM generate one bounded SELECT over authorized views. Its input is `q_en` **together with the resolved BIR constraints** (metric definition, filters, time range, grouping, ranking) and the authorized schema. Where `q_en` and the resolved BIR differ (for example, after a clarification, or when the audit flagged a collapse), **the resolved BIR takes precedence**.
10. **Guards.** The SQL is AST-parsed (single SELECT, no DDL/DML, no multi-statements), checked against the object/column allowlist and server-side department authorization, and checked for **BIR↔SQL consistency** (metric expression, filters, date constraints, group-by, ranking and joins). SQL that fails a guard is not executed, and the request is handled under the existing Abstain rule (unsafe or inconsistent SQL). Execution uses a least-privilege read-only DB role with timeout and row cap.
11. **Output.** Render numerical results returned **by PostgreSQL**, the table/chart, the interpreted metric, filters and timeframe (shown in Arabic), the SQL trace and limitations, and write audit records (`q_ar`, `q_en`, translation-audit flags, BIR, decision, SQL, guard results).

**Interaction summary:** `q_ar` → (BIR + ambiguity, authoritative) → policy → [clarify loop] → resolved BIR. In parallel, `q_ar` → `q_en` (derived, ambiguity-preserving) → audit only. After Answer: `q_en` + resolved BIR → English-to-SQL → guards → read-only execution. The decision never depends on the English wording, and SQL never runs before the decision.

### 8.2 Example of business ambiguity

Example transliteration: *'Meen aktar far3 kasban el-shahr elli fat?'* (Which branch was the biggest winner last month?). Possible metrics: revenue, net sales, gross profit; **net profit** requires operating expense data not guaranteed by the six-table retail MVP. The system should not silently pick one. Multiple distinct reasonable interpretations can be semantically ambiguous **even if two happen to produce the same result on one database snapshot**.

**Translation risk (23 Oct 2026):** a translation such as *"Which branch was the most profitable last month?"* would silently collapse "كسبان" to gross profit. Under §8.1 this cannot change the decision: the ambiguity flag comes from the Arabic wording and the catalog lexicon, the translation audit logs the collapse, and the SQL generator receives the metric only after the user's clarification.

Another example: *'El-makhzoon elly 2areeb yekhlas'* (stock close to running out) is underspecified unless the catalog provides a sanctioned reorder threshold, or the user selects one.

### 8.3 Proposed BIR JSON (illustrative; not code already running)

```json
{
  "mode": "analytics",
  "department_id": "sales",
  "intent_type": "rank",
  "metric_candidates": ["net_sales", "gross_profit"],
  "resolved_metric": null,
  "dimensions": ["store"],
  "filters": {},
  "time_expression": "last month",
  "time_range": null,
  "as_of_date": "<explicit evaluation reference date>",
  "rank": {"order": "desc", "limit": 1},
  "ambiguity_flags": ["METRIC_UNRESOLVED"],
  "entity_resolution": {},
  "confidence_notes": [],
  "decision": "CLARIFY"
}
```

The request record around the BIR (illustrative) also stores `question_ar` (the confirmed transcript, authoritative), `question_en` (the derived translation), `translation_audit` (e.g., `["AMBIGUITY_COLLAPSED:كسبان→most profitable"]`) and `input_mode` (`text`/`voice`). The BIR itself is produced from `question_ar` only.

`department_id` must originate in authenticated context, not untrusted prompt output. Metric candidate IDs must be known to the approved department catalog. Real JSON serializers will represent dates with concrete ISO dates; the placeholder above is illustrative.

### 8.4 Answer / Clarify / Abstain policy

- **ANSWER:** Metric resolved and approved, entities/time resolved, requested answer computable from authorized records and permitted SQL operations.
- **CLARIFY:** At least two material reasonable meanings remain, a needed business definition is unresolved, or ASR/entity uncertainty could change the answer; present few focused options. A clarification turn may be limited to one in the MVP.
- **ABSTAIN:** Missing required tables or costs, prohibited access, unsupported analytics, unsafe SQL, repeated unresolved ambiguity after limit, or absent valid metric definition. Explain, do not hallucinate.
- **NEVER:** rely exclusively on model self-reported confidence or SQL execution success as evidence the business meaning is correct.

### 8.5 Metrics and semantics

A versioned **Semantic Catalog** defines revenue, gross sales, net sales, units sold, discount handling, returns policy, gross profit (if costs exist), average order value, and date/timestamp interpretation. Avoid promising **net profit** without operating expense data. Keep locale variations for Egyptian Arabic, Latin transliterations, code-switching and common city/branch aliases. Dates like 'last month' resolve against fixed `as_of_date`, timezone and calendar policy; freeze these during evaluation.

---

## 9. Original canonical retail data model

The initial V2 model remains an excellent **demonstration/reference dataset**, not necessarily a universal schema for every department:

| Table | Purpose | Typical fields/relationships — illustrative only |
|---|---|---|
| `stores` | Retail branches | `store_id` PK, `store_name`, `region`, status |
| `products` | Product master | `product_id` PK, SKU, `product_name`, category |
| `sales_headers` | Transaction headers | `sale_id` PK, `store_id` FK, transaction date/time, discount/tax policy |
| `sales_lines` | Purchased items | `sale_line_id` PK, `sale_id` FK, `product_id` FK, quantity, unit price, line discount |
| `returns` | Returned items/events | `return_id` PK, `sale_line_id` FK, date, returned qty/value |
| `product_costs` | Time-dependent cost data | `product_id` FK, valid-from date, unit cost (and possibly cost policy) |

Retail SQL and mathematical definitions must be reconciled with the *actual physical schema and import source*. No SQL migration for this model has been presented as implemented. Decide whether sales-header and sales-line discount conventions overlap; protect from double counting. Treat refunds, taxes, canceled invoices and temporal cost joins explicitly.

**Inventory extension:** A separate `inventory_snapshots` or `stock_movements` table is a **V3 proposal** only. Without approved inventory quantity/threshold data, answering reorder questions must abstain or clarify; the existence of `products` alone is insufficient.

**Cross-department metadata:** The control-plane registry associates a workspace with approved SQL views, permitted joins, metric catalog and version. It should not naïvely join HR and Sales records or expose other departments' private columns.

---

## 10. Data import, credentials, and SQL Read-Only contract

### 10.1 Data ingestion (unchanged from V2, now department-scoped)

- Accept project-owned or licensed CSV/XLSX retail exports; perform deterministic column mapping, type/value checks, rejected-row audit and repeated-load idempotency.
- Load only through separate `loader_rw` import credentials within allowed schemas; do not give these to the conversational model or ordinary analytics endpoint.
- Publish known-good curated analytic **views** and a matching catalog version. A new department requires explicit onboarding and tests, not merely changing a prompt.
- Do not assert live Odoo/POS/ERP connectors or federated enterprise integration in the MVP.

### 10.2 Non-negotiable execution safety

- Default-deny SQL execution; allow only a single SELECT statement over strictly allowlisted relations/columns and known permitted functions.
- Use a structural AST/parser guard (e.g. SQLGlot **as one component**), ban writes/DDL, multi-statements, dynamic SQL and unsafe functions; parser success alone is not execution safety.
- Check rendered SQL against BIR-approved metric, filters, date constraints, group-by and joins, then database permissions.
- Execute with least-privilege `analyst_ro` or department-specific read-only roles, restricted connection/search_path, transaction read-only, timeout, row cap and resource limits.
- The **server** determines authorization from identity/department membership. Never trust an LLM-generated table name or `department_id` to grant permission.
- Confirm department isolation with negative tests, including malicious text and requests to query another workspace.
- Store a minimal, access-controlled audit log; avoid retaining raw voice/PII by default without consent or clear need.

### 10.3 Crucial distinction between two meanings of 'read-only'

1. **Historic artifacts:** The V2 and V3-draft snapshots are immutable records kept in the registration package (`01_READ_ONLY_V2_BASELINE/`, `01B_READ_ONLY_V3_DRAFT_BASELINE/`; not part of this repository), to prevent agents overwriting project history.
2. **Runtime security:** The analytics mode has *no data modification powers*; it must use read-only DB permissions, separate from schema design and approved ingestion.

The Admin's **approval of a schema design** is not an exemption from runtime read-only SQL safeguards. DDL deployment remains an explicit controlled operator action, deferred unless approved within a sandbox-only task.

---
## 11. New Schema Design Mode (M9) — precise functional design

**Core user intent:** *'I want to build an application for X; I can describe the idea but not every technical requirement. Suggest a database design and tell me what must be clarified.'* This is a **draft design assistant**, not a complete application generator.

### 11.1 Intake and structured representation

1. Authorized designer selects `Schema Design` mode and a destination workspace/domain, or proposes a new sandbox domain for admin review.
2. Accept high-level description typed in natural language; Egyptian Arabic text support is desired, but whether voice also applies to schema design is **PENDING**. Voice is mandatory for analytics only until further approval.
3. LLM extracts a proposed `SRR` (*Schema Requirements Representation*) with entities, workflows, actors, cardinality assumptions, retention/privacy concerns, essential required fields, ambiguous concepts, missing requirements, and stated versus inferred requirements.
4. Classify each requirement or proposed entity as `EXPLICIT`, `INFERRED_REQUIRES_CONFIRMATION`, or `UNKNOWN`. Do **not** present model assumptions as user requirements.
5. Ask focused clarification on high-impact uncertainties (e.g., multiple doctors per appointment? stock transfers? shared ownership?) rather than requiring a full specification up front.
6. Generate a constrained JSON **schema proposal**, a readable table list and ERD preview. Provide PK/FK directions, relationship cardinalities, nullability and uniqueness rules only where justified.
7. Run deterministic checks: PK presence, FK target existence, relationship/cardinality sanity, reserved-word and type checks, duplicate entities, cycles only where unsafe, essential requirement coverage and obvious privacy issues.
8. Version the proposal with explanatory `rationale`, `open_assumptions`, `validation_findings` and a diff from the prior proposal.
9. Send to Admin review. The Admin can `APPROVE`, `REQUEST_CHANGES`, or `REJECT` with comment, recorded identity/time/version. The model cannot approve on the Admin's behalf.
10. Upon approval, publish the **metadata artifact** to the registry after an explicit authorized action. Actual DDL execution/provisioning is a separate gated activity, not an implicit consequence.

### 11.2 SRR example (illustrative; not implemented)

```json
{
  "mode": "schema_design",
  "proposal_id": "draft-001",
  "department_context": "clinic_demo",
  "source_requirement": "Build a clinic appointment app with doctors and patients",
  "explicit_entities": ["patient", "doctor", "appointment"],
  "inferred_entities": ["specialty"],
  "workflow_assumptions": [
    {"id": "A1", "statement": "An appointment has exactly one doctor", "status": "UNCONFIRMED"}
  ],
  "questions": [
    "Can an appointment involve more than one doctor?",
    "Should payments be tracked?"
  ],
  "data_constraints": [],
  "design_status": "DRAFT"
}
```

A proposed schema artifact can additionally contain `tables[]`, `columns[]`, `constraints[]`, `relations[]`, `cardinality`, `sources[]` and `validation[]`. These are **design proposals**; the team must define and version the actual schema before implementation.

### 11.3 Review state machine

`DRAFT → VALIDATED_DRAFT → IN_REVIEW → APPROVED | REQUEST_CHANGES | REJECTED`.

- `REQUEST_CHANGES → DRAFT` creates a **new version**; no silent mutation of the approved one.
- `APPROVED → PUBLISHED` is an explicit Admin/publisher action and refers initially to metadata only.
- Design artifacts may be reviewed multiple times, with who/when/why preserved.
- Any published catalog version used for evaluation must be frozen and identifiable.

### 11.4 Schema generation quality gates (proposed)

- Every proposed FK targets a real compatible field; no orphan relations.
- Primary keys exist on durable entity tables unless an explicit model supports alternate conventions.
- Relationship cardinalities are stated and justified or flagged as assumptions.
- All *explicit* mandatory requirements map to an entity/attribute/constraint or an acknowledged unsupported item.
- No invented high-impact domain requirement (e.g., handling financial payments or diagnoses) is silently imposed.
- Sensitive personal data is minimized; health/HR examples use synthetic records and hypothetical fields only.
- An Admin can view a readable **why this table/relationship** explanation and an edit/diff summary.

### 11.5 Example integrated flow

**Design phase:** Developer: *'I need an application for employee leave requests.'* The hub suggests `employees`, `departments`, `leave_requests`, and maybe `leave_balances`; flags that balance accrual and approval policy need confirmation; Admin reviews a draft ERD.

**Data phase:** Approved design is optionally provisioned in a **sandbox**, and synthetic sample rows are loaded; metadata is reviewed/published.

**Analysis phase:** An authorized HR user asks *'Which department has the most approved leave days this month?'* The analytics engine uses the approved HR schema and leave-policy definitions, and it either answers, clarifies the definition of 'days', or abstains if leave approvals/durations are absent. **No cross-department table access is inferred by the LLM.**

---

## 12. Multi-Department Central Hub (M10) — exact meaning

The Central Hub is **one shared frontend, orchestration and governance layer** with **independent department contexts**, not one merged pool of unrestricted business records. A user can be permitted in one or multiple workspaces; the server authorizes each selection. Each department can have a separate physical data source or separate protected views.

### 12.1 Required shared hub functions (proposed)

- Login/session: authenticated user identity, roles, organization context and list of permitted department workspaces.
- Department selector and approved context loading: schema IDs/versions, view allowlist, metric dictionary, locale rules and source availability.
- Two explicit modes: `Ask Data` and `Design Schema`; mode access is role-dependent.
- Department audit: ask, clarify, abstain, query, proposal submit/review and publish events with version IDs.
- Metadata governance: change requests for synonyms, measures or columns; Admin approval and effective version.
- Privacy isolation: refuse unauthorized operations before any LLM sees restricted column names or data.
- Standard error states: `not authorized`, `department not configured`, `metric unavailable`, `data not imported`, `ambiguous`, `query rejected`, `schema awaiting approval`.

### 12.2 Minimum demonstrable department difference

A proper demo must show **three functional workspaces, not just three decorative tabs**: Sales (revenue/returns), Inventory (stock and reorder semantics), and HR (headcount/leave metrics), each with its own approved catalog, permissible views and authentically enforced roles. The same AI pipeline must switch its department context without retraining three different engines.

**Bounded generalization:** a working HR analytics path provides concrete non-retail business-domain evidence within the demo, but does not prove universal portability or production readiness for every industry.

### 12.3 Recommended configuration contract (proposal)

```json
{
  "workspace_id": "sales",
  "company_id": "demo_company",
  "catalog_version": "pending",
  "approved_schema_version": "pending",
  "authorized_view_ids": ["vw_sales_lines", "vw_store_sales"],
  "permitted_metrics": ["gross_sales", "net_sales", "units_sold"],
  "policies": {"max_rows": 500, "allow_sql_mutation": false},
  "status": "PROPOSED"
}
```

The actual view names, limits and policies must be chosen after the data schema and threat model. These are illustrative, **not deployed configuration**.

---

## 13. Functional requirements and acceptance criteria

| ID | Requirement | Verification evidence when implemented |
|---|---|---|
| FR-01 | Authorized user can select department and analytics mode; unauthorized workspace denied. | Backend and integration tests incl. tampered department IDs. |
| FR-02 | Egyptian-Arabic text and voice questions accepted; transcript editable before execution. | UI workflow + paired speaker samples. |
| FR-03 | Analytics extracts structured BIR grounded in the workspace catalog. | Golden JSON cases and resolver tests. |
| FR-04 | Ambiguous or unanswerable questions produce justified Clarify or Abstain. | Annotated ambiguity/answerability decision suite. |
| FR-05 | Answerable questions use safe, read-only, allowlisted SQL. | AST and PostgreSQL negative security tests. |
| FR-06 | Answer includes the used metric/timeframe, result/chart and a non-sensitive SQL trace. | Human inspection and automated result comparison. |
| FR-07 | Designer can submit an incomplete natural-language app brief. | Scenario tests incl. missing requirement cases. |
| FR-08 | Schema proposal includes tables, attributes, PK/FK, relationship cardinalities, assumptions and questions. | Structured-schema validator and expert review. |
| FR-09 | Admin can accept/reject/request revision on a specific draft version. | Role tests, state-machine transitions and audit. |
| FR-10 | Schema proposal cannot execute SQL DDL or alter the production database. | Privilege tests, API negative tests. |
| FR-11 | Approved metadata/correct role governs both the query and design experience. | Versioned registry and cross-workspace tests. |
| FR-12 | Reproducible benchmark runner records P0–P4, schema-baseline conditions and outcomes. | Test run manifest, held-out splits and scoring report. |
| FR-13 | Operator can import CSV/XLSX by fixed mapping without duplicate transactional rows. | Loader replay checks and rejected-row log. |
| FR-14 | User sees meaningful failure explanations and no fabricated results for missing tables/cost data. | Negative end-to-end tests. |

### 13.1 Non-functional targets (NOT achieved results)

- **Safety:** All disallowed SQL operations blocked in a defined adversarial suite; least-privilege DB grants tested independently. Test-suite 100% block is a release gate, **not a universal proof of security**.
- **Reproducibility:** dataset version/splits, SQL view versions, selected models, prompts, decoding settings and reference clock frozen per evaluation run.
- **Usability:** nontechnical managers can complete basic analytics questions; technical designers can understand schema diagrams and admin decisions.
- **Performance:** define per-mode latency budgets after piloting; V2 tentative p95 targets of 8 s text and 12 s voice are **planning estimates only** and cannot be assumed for the full V3 stack.
- **Maintainability:** versioned schemas/catalogs, modular interfaces, migration rollback plan if physical provisioning is ever included.
- **Privacy:** use consent for voice/interviews, synthetic data in HR/clinic demonstrations, no production secrets in logs or prompts.

---

## 14. Data assets and dataset strategy

### 14.1 What data exists versus what is planned

There is **no confirmed completed project-specific dataset or collected audio** in the available records. Public references and target counts below are a **data plan**. The previous V2 MIU form is frozen and contains a candidate dataset narrative; V3 must not pretend those datasets were already licensed, downloaded, annotated, cleaned or joined.

### 14.2 Retail primary analytics track (retain V2 plan)

- **Data sources (team-approved DS-1–DS-3, 22 Oct 2026):** the **primary** Sales benchmark uses the project-authored, seeded synthetic Egyptian retail company (six canonical tables); UCI **Online Retail II** (CC BY 4.0) is an optional, separately reported real-data check with no added fields; **Contoso Data Generator V2** (MIT) is an optional replication database and design reference. See `docs/DATASET_STRATEGY.md`.
- **Critical provenance:** Online Retail II lacks reliable branch/cost metadata for the proposed full six-table model. Do not splice real historical transactions with unrelated Contoso records as if both were observations from the same actual company. Clearly label and segregate real versus synthetic slices or use a documented entirely synthetic benchmark.
- **Target corpus (DS-7):** approximately **400** authored Egyptian-Arabic Sales items: **375 semantic-evaluation items** (≈180 clear → Answer, 110 ambiguous → Clarify, 85 unanswerable/out-of-scope → Abstain) with candidate interpretations and BIR/decision labels, plus **25 authorization/security cases** evaluated in a separate Security suite (§15.4), never in the P2-vs-P4 semantic metrics; development/test split by question template family.
- **Voice subset (DS-6):** **192 core recordings** (Sales 144, Inventory 24, HR 24; optional expansion to ≈260) from **at least 10 (target 12) consenting speakers**, speaker-disjoint and template-family-disjoint between development and test, with verified transcriptions; voice/text items reflect the same intended task. ASR choices are made on development data only; no ASR fine-tuning is required for the MVP, but evaluation on real Egyptian-Arabic speech is mandatory.
- **Gold SQL:** every answerable interpretation of every answerable item (clear and ambiguous) has **question-specific** gold PostgreSQL SQL, validated by a second person against **that exact question's** constraints and executed on two snapshots; this exceeds the original university minimum of **50** manually verified answerable questions.
- **Gold ground truth:** for clear examples, intended metric/entity/time/SQL and expected result on fixed snapshots; for ambiguous, alternate interpretations and clarification target(s); for unanswerable, expected abstention reason, with no fake gold executable SQL.
- **Human-reviewed English equivalents (23 Oct 2026, TA pipeline):** every item also carries a reference English equivalent written by a bilingual annotator and verified by a second annotator for meaning **and preserved ambiguity**. An ambiguous Arabic item keeps an ambiguous English equivalent, e.g., "earned the most", not "most profitable". These references are **evaluation-only**: they score the translation stage and support an optional oracle-translation ablation, and are **never** given to P2 or P4 in the main runs. Gold SQL is always written and validated against the project's own synthetic PostgreSQL database, never borrowed from public datasets.
- **Annotation:** two annotators and an independent adjudication protocol; make clear where gold labels may themselves be debatable.

### 14.3 Three-workspace demonstration data — TEAM-SELECTED mandatory scope

**One fictitious company, three working departments:** Sales, Inventory and HR. The integrated company dataset is synthetic and must be labeled as such in every figure, demo and report. A separate UCI Online Retail II real-data experiment, if performed, remains separately labeled and is never silently merged with fictional company records.

- **Sales:** synthetic stores/products/sales/returns/costs aligned to the original six-table retail model and governed revenue/net-sales/profit calculations. Sales remains the **primary** analytics research/evaluation domain; retain the strong P2-vs-P4 comparison and paired voice/text requirements.
- **Inventory:** synthetic `stock_movements` and/or `inventory_snapshots`, `reorder_thresholds`, and shared *approved* `stores`/`products` master-data views; stock-on-hand and low-stock definitions must be explicit. An authorized **operator** can provision a vetted Inventory design in an isolated demonstration database and load data after versioned schema approval. This is a **separate human-controlled step**, not the LLM running DDL.
- **HR:** **mandatory** synthetic `employees`, `departments` and `leave_requests` (plus optional safe `employment_events`/`leave_balances` only if needed), approved metrics such as active headcount, new hires and approved leave days. Do not collect real employee/personnel records. Use realistic but **invented** names/IDs; restrict sensitive columns. HR must support typed and Egyptian-Arabic spoken queries, not merely a landing-page card.
- **One shared analytics engine:** department metadata selects allowed views and business definitions; backend role checks precede context retrieval. Department-switch tests must prove absence of cross-department disclosure.
- **Recommended bounded evaluation:** Sales is the full primary benchmark; Inventory and HR each have small manually checked acceptance sets with clear, ambiguous and unanswerable questions (target ≈60 typed items each) and 24 voice recordings each (20 test); counts are planned targets, not collected data.
- **Provenance/control:** maintain seed, schema version, catalog version, synthetic generator script, approved metrics and query snapshots. The synthetic sales/inventory events must reconcile under their documented business conventions; do not assert automatic financial/stock consistency without tests.

---

### 14.4 New Schema Design benchmark (proposed)

- Construct a bounded set of **30–60** app requirement briefs initially (a sizing **suggestion**, not a mandatory university requirement) across at least **two scenarios/domains**, with deliberate omissions, conflicting statements and relevant approval decisions.
- Label explicit requirements, inferred-but-optional entities, mandatory missing clarifications, accepted reference ERDs/schema elements and schema-review adjudications. Avoid assuming one unique gold schema exists for every valid set of requirements.
- Use **multiple expert reviewers** where possible; score design equivalence and requirement coverage rather than exact table-name string matching alone.
- Candidate external check: **Text2Schema / SchemaAgent / RSchema** (arXiv:2503.23886). Verified 22 Oct 2026: the v1 abstract reported more than 500 pairs, v2 (17 Oct 2025) reports 381; the public repository file `datasets/RSchema/annotation.jsonl` holds 518 records and the repository has **no license**. Its requirements are fully specified, so it cannot test incomplete-requirement handling. Use only a small sanity subset, and only with written author permission (DS-8).
- Split by application/requirement template (not just random paraphrases); keep test cases unseen during prompt iteration.
- The schema track is a **separate research/engineering question**; adding 30–60 briefs does not replace the 50 gold SQL requirement or Arabic voice tests.

### 14.5 Supplementary research resources

- **AMBROSIA**: benchmark methodology for ambiguity, not Egyptian retail benchmark out of the box (no license stated; password-protected; authors ask that it not be re-uploaded — taxonomy and citation only).
- **PRACTIQ**: ambiguous/unanswerable conversational Text-to-SQL patterns (repository archived, generation code only, CC BY-NC 4.0 — taxonomy reference).
- **Ar-Spider**: written Modern/other Arabic Text-to-SQL resource, not direct Egyptian voice data (no repository license found — related-work citation only).
- **Public Text-to-SQL references by pipeline stage (DS-11, synchronized 23 Oct 2026; the TA replied positively to the Spider/BIRD/AraSpider evidence screenshots).** None is merged with Context A, translated into the test set, or used for training/fine-tuning:
  - **Spider** (English question → SQL, cross-domain multi-table; CC BY-SA 4.0; https://huggingface.co/datasets/xlangai/spider): English-to-SQL reference benchmark.
  - **BIRD Mini-Dev** (English question → SQL incl. PostgreSQL, with `evidence` business-term hints; CC BY-SA 4.0; https://huggingface.co/datasets/birdsql/bird_mini_dev): reference and **optional** PostgreSQL check of the English-to-SQL component.
  - **AraSpider** (Spider questions with Modern Standard Arabic translations and the same SQL; **licensing:** the HF repository declares MIT, while the underlying Spider dataset declares CC BY-SA 4.0. The redistribution terms of the derived content are therefore **uncertain**, and the project neither redistributes it nor treats it as covered by only one of these licenses; https://huggingface.co/datasets/ahmedheakl/araspider): reference for Arabic–English–SQL cross-language alignment; MSA, not Egyptian dialect or business data.
  - **Gretel Synthetic Text-to-SQL** (105,851 synthetic English question–SQL pairs with schema context across 100 domains incl. retail and HR; Apache 2.0; verified on the HF API 23 Oct 2026; https://huggingface.co/datasets/gretelai/synthetic_text_to_sql): additional English-to-SQL reference from the team's independent review. Its SQL is generic and not PostgreSQL-specific. **No commitment** to translate its 60,000–89,000 questions into Egyptian Arabic.
  - **AmbiQT** and **AMBROSIA** remain ambiguity research references (taxonomy, related work), not implementation datasets.
  - **AceMB** is **not** a confirmed source until its gated content is independently inspected.
  - These public datasets are English or MSA and non-business, and are likely present in LLM training data, so they are **not** suitable for the primary P2-vs-P4 evaluation.
- **Casablanca (Egypt subset)**: verified CC BY-NC-ND 4.0, research-only, validation and test splits only (846 + 846 segments); the validation split supports ASR model selection and the test split is reserved for final background reporting. **MGB-3**: official access terms unverified. **FLEURS `ar_eg`** is read MSA and must not be cited as Egyptian dialect. The full license and access evidence is recorded in the registration package's dataset verification log (`06_RESEARCH_AND_DATA/V3_1_DATASET_VERIFICATION_LOG.md`, not included in this repository); the conclusions this project relies on are stated in this section, §24.2 and `docs/DATASET_STRATEGY.md` §11.

---

## 15. Evaluation plan and baselines

### 15.1 Analytics experiments (unchanged fair primary comparison)

| Pipeline | Definition | Role |
|---|---|---|
| **P0** | Egyptian-Arabic question `q_ar` + its cached English translation `q_en` + schema → LLM SQL directly | Weak transparency baseline |
| **P1** | P0 plus the complete sanctioned business glossary, aliases, time policy and schema context | Context-enhanced baseline |
| **P2** | P1 plus explicit instructions to **clarify and abstain**, same one-turn limit; one LLM decides and writes the English-to-SQL query | **Strong primary baseline** |
| **P3** | *Redefined 23 Oct 2026 (translation is now part of every pipeline):* **English-only translation ablation**: P2 receives only `q_en`, not `q_ar` | Optional ablation; measures how much ambiguity is lost when the Arabic original is discarded (team confirmation pending, Q14) |
| **P4** | Arabic-anchored BIR/resolvers + deterministic Answer/Clarify/Abstain + English-to-SQL from `q_en` and resolved BIR + BIR↔SQL consistency guard (§8.1) | **Proposed method** |

**Matched inputs (P2/P4 fairness, 23 Oct 2026).** For every item and condition, all pipelines receive **byte-identical, frozen inputs**:
- the same confirmed Arabic text: in the text condition, the benchmark question; in the voice condition, the **same frozen ASR output** for that utterance;
- the same cached `q_en`, produced **once** by the same frozen translation model and prompt from that Arabic text;
- the same catalog, authorized views, as-of date, DB snapshot, LLM and version, temperature and clarification budget, and the same simulated user.

The authorization gate and the AST/allowlist/read-only SQL guard are shared infrastructure for every pipeline. The BIR↔SQL consistency check belongs to P4's method, because P2 has no BIR. Record prompts and outputs, and make **no claimed superiority until measured**. An external Wren AI/Genie product check is possible, but it is not an exactly controlled internal ablation unless settings can genuinely be matched.

**Leakage controls.** Human-reviewed English equivalents, gold SQL and gold results are **never** placed in any prompt. ASR, normalization, translation prompt/glossary and any few-shot exemplars are chosen on the **dev** split (or public datasets) identically for P2 and P4, never from test items. The ASR and translation configurations are frozen and hashed before the test run. Public Text-to-SQL datasets (§14.5) may supply generic exemplars or sanity checks but never test items. Details: `docs/EVALUATION_PLAN.md`, Part B.

### 15.2 Analytics metrics: define denominators before testing

Let `N_E` be the semantic-eligible evaluated requests (authorization/security cases excluded); `A` the number of delivered answers (direct or after one clarification); `W_A` numerically incorrect **direct** answers. Definitions approved under DS-7 (22 Oct 2026).

- **Business-Answer Accuracy (BAA, end-to-end):** correct final business answers (after at most one clarification) / all answerable semantic-eligible items (clear + ambiguous); abstaining on, or wrongly answering, an answerable item is a failure. Also report **policy-compliant BAA**, which additionally counts every unsafe direct answer (below) as a failure.
- **Unsafe Direct Answer Rate (policy violation):** materially ambiguous items answered directly without the necessary clarification / all clarification-required eligible items. It is recorded **even when the chosen interpretation coincidentally matches the intended answer**, reported separately from numerical correctness, and never credited as reliable ambiguity handling.
- **Silent Error Rate:** SER_direct = `W_A / N_E` (numerically incorrect direct answers); SER_final = all numerically incorrect delivered answers / `N_E`. **Authorization/security cases are excluded** from both.
- **Selective accuracy / risk:** correct / incorrect delivered answers ÷ `A` (`A > 0`); an answer to an unanswerable item is incorrect. Report with coverage so always abstaining is not rewarded.
- **Coverage:** `A / N_E`; compare P4 and P2 at **similar answer coverage** (risk–coverage curves on semantic-eligible items only).
- **Clarification precision:** correct clarifications (on a clarification-required item, with the correct target) / all clarification requests on eligible items. **Clarification recall:** correct clarifications / all clarification-required eligible items. An unnecessary clarification on a clear (or unanswerable) item, or one with the wrong target, is a false positive.
- **Abstention correctness:** Abstain precision/recall over eligible unanswerable and out-of-scope items, plus the mistaken-abstention rate on answerable items. **Unauthorized requests are excluded** and scored in the Security suite (§15.4).
- **SQL Execution Accuracy:** result equivalence on multiple fixed database snapshots; does not certify business intent.
- **ASR WER/CER and named entity error, voice-vs-text delta, latency p50/p95, interaction count, model cost**.
- **Translation stage (23 Oct 2026):** meaning preservation of `q_en` against the human-reviewed English equivalents (human-judged on a sample, plus an automatic score such as chrF reported as secondary), **entity preservation rate** (catalog entities kept), **Ambiguity-Preservation Rate** = clarification-required items whose `q_en` still keeps the ambiguity / |C*|, and its complement, the **Translation Ambiguity-Collapse Rate**. These are diagnostics of the translation component. In P4 a collapse must not change the decision (§8.1), and how often a collapse coincides with an unsafe direct answer in P2/P3 is reported.
- **Semantic versus numerical errors are kept separate.** A **semantic (business-meaning) error** is an answer delivered under an interpretation that differs from the intended or clarified one, including every unsafe direct answer, whatever the number. A **SQL/result error** is a delivered answer whose interpretation is correct but whose SQL result differs from the gold result. SER counts numerical incorrectness. The semantic/SQL split and a **stage attribution** (ASR → translation → BIR/resolver → policy → SQL generation → guard) are reported for every failure, so a translation-induced error is never mixed with an SQL bug.
- Paired analysis with confidence intervals and, when appropriate, McNemar/clustered bootstrap; benchmark is too small to overclaim subgroup effects without uncertainty.

**Release criteria and target values** from V2 were provisional planning gates, not measurements or academic pass/fail rules; V3 needs explicit reapproval of final numeric thresholds.

### 15.3 Schema track comparison (new)

| Scheme | Setup | Reason |
|---|---|---|
| **S0** | Same LLM directly generates schema from brief, no structured requirement checking | Strong simple baseline; measure direct prompt quality |
| **S1** | LLM with standardized schema-design instruction and domain exemplars | Better-context baseline |
| **S2 (proposed)** | SRR extraction + uncertainty/clarifications + structural checks + versioned Admin review | Proposed assisted workflow |

**Metrics:** explicit requirement coverage (incl. mandatory workflows), entity/table alignment, PK/FK correctness, relationship/cardinality accuracy, constraint validity, unsupported assumption rate, critical omission recall, non-executing proposed DDL validity if available, expert approval/revision counts, time to acceptable design, admin usability. Human approval is a *workflow*, so compare both proposal quality before approval and residual issues after bounded review time.

### 15.4 Three-workspace hub and authorization integration tests

- **Functional coverage:** three independently authorized workspaces **Sales, Inventory, HR** render a valid contextual query and corresponding chart/result through the same shared pipeline. Inventory and HR are each evaluated with ≈60 typed acceptance items and 24 Egyptian-Arabic recordings (20 test) under DS-6/DS-7; a single successful voice query is a floor, not the target.
- **Deny-by-default:** Sales-only users cannot see HR employee fields or Inventory-only metrics; HR-only users cannot query sales revenue, and Inventory-only users cannot read private HR records. Backend and DB policy enforce this before any LLM is given forbidden metadata. The 25 Sales authorization/security cases plus the Inventory/HR denial tests form a **separate Security suite**, excluded from P2-vs-P4 semantic metrics: unauthorized workspace access (including tampered workspace or role claims) must be **denied before any LLM invocation**; for cross-department questions inside an otherwise authorized workspace, a **safe scoped Abstain** is acceptable provided no restricted metadata is exposed, no unauthorized SQL executes and no data is disclosed. Not every security scenario must produce the same DENY outcome; DENY is an authorization-gate outcome, not a fourth model decision.
- **Tampering:** user changes `workspace_id`, forges role claims or prompts the model to join unauthorized sources; authorization and SQL guards block the request.
- **Approval integrity:** `DRAFT` design has no live SQL view; `APPROVED` metadata is not evidence of deployed physical tables; publish action and separately reviewed operator provisioning preserve version identifiers.
- **Context isolation:** department business vocabulary ('top', 'profit', 'low stock', 'active staff', 'days of leave') resolves only through the selected approved catalog and should trigger clarification on missing definitions.
- **State and audit:** Admin review state transitions and human actor, schema version, dataset version, trace/run ID and permission decisions are recorded without retaining synthetic/real sensitive raw utterances unnecessarily.

---

### 15.5 Verification vs validation

- **Verification:** are role checks, schema state machine, SQL permissions, date rules, approved catalog use, ETL, query answers and test harness implemented according to specification?
- **Validation:** do retail/dept managers and schema designers actually need/use the workflow, can they complete representative tasks with fewer costly mistakes and acceptable friction, and does expert feedback support business value?
- **No interviews/pilot outcomes yet.** Proposed qualitative plan: about **12+** managers/technical designers across target segments, followed by a small comparative task-based prototype trial if recruitment feasible; these are goals, not completed studies.

---

## 16. Market problem, research gap and competitor constraints

### 16.1 Three evidence layers must be separated

**Market context:** OECD's 2025 report documents obstacles and opportunities in SME digitalization in Egypt. Visa/MSMEDA's July 2025 survey reported **53%** of merchants sampled implemented digital payments in the previous two years, and **77%** of sampled SMEs believed such technologies would support growth. The Visa page also mentions interest in data-driven insights, **but these percentages describe payments, not BI adoption or purchase intent for our hub**.

**Technical evidence:** AMBROSIA (NeurIPS 2024) evaluates ambiguity even when database context is supplied; one Llama3-70B setup reported **30.7% recall on ambiguous** versus **64.5% on unambiguous** questions. Ar-Spider published an **LGESQL 65.57%** score on an Arabic written-query setting. These are study-specific figures and not our model's measured results. PRACTIQ addresses ambiguous and unanswerable conversational queries.

**Competitive evidence:** Wren AI already provides semantic modeling, SQL querying and evaluation/clarification primitives; Databricks Genie supports governed natural-language analytics; Microsoft Power Apps Copilot can create relational data tables from natural language; dbdiagram AI supports generating/modifying tables and relationships. **No claim that no competitor offers governance, schema generation, or clarification can be made.**

### 16.2 Provisional two-sided gap hypothesis

- **Analytics research gap:** the reliability of **Egyptian Arabic spoken business queries with material semantic ambiguity and ASR uncertainty** deserves reproducible evaluation under controlled context-matched baselines.
- **Schema-design research/engineering gap:** effective handling of **incomplete requirements, model assumptions, constraint validity, administrator review effort and eventual analytics reuse** should be measured rather than assumed.
- **Market gap hypothesis:** some organizations may benefit from a shared authorized workflow from schema proposal through approved data analytics. The sources reviewed do **not** prove a unique product void, broad willingness to pay or a validated Egyptian market segment for this package.

### 16.3 Competitor comparison (capability-driven, not numerical ranking)

| Alternative | Known area of overlap | Proposed differentiation to **test**, not assert |
|---|---|---|
| Wren AI | Conversational BI, semantic context/model definitions, ambiguity-aware workflows and governed SQL | Egyptian dialect voice/text reliability and rigorous P2-vs-P4 matched coverage |
| Databricks Genie | Natural-language analytics with curated knowledge, metrics, clarifications and benchmarks | Bounded prototype emphasizing explicit BIR and traceable uncertainty, **not** novelty of clarification |
| Power BI Copilot | Natural-language assisted analytics in BI workflows | Domain-scoped Egyptian dialect evaluation and visible selective-answering policy |
| Microsoft Power Apps Copilot | Natural-language app/table generation, relationships, data import | Incomplete-brief assumptions, review trace and controlled linkage to analysis |
| dbdiagram AI | Natural-language database schema creation, edits, constraints, relationships | Review workflow quality, requirement coverage and approved catalog reuse |
| Text2Schema / SchemaAgent (research) | Natural-language database logical schema generation, error detection/refinement | Test alternative structured requirements + human review; avoid claiming first AI schema assistant |

Caution: absence of an API or feature on an inspected product page is not proof that a product lacks it. The relevant public links are listed in §24.2; the fuller research source notes are archived in the registration package (`06_RESEARCH_AND_DATA/`, not included in this repository).

---

## 17. Candidate technical implementation stack — not selected

| Layer | Candidate | Selection criteria |
|---|---|---|
| UI | React/Next.js or another team-standard framework | Arabic RTL, microphone, diagrams, approvals, charts, easy hosting |
| Backend | Python FastAPI or comparable service | Typed validation, ASR/LLM orchestration, SQL AST enforcement, testing |
| DB | PostgreSQL for analytical data; control-plane metadata in PostgreSQL or another rational datastore | Read-only roles, views, transactions, audit, deterministic fixtures |
| ORM/schema | SQLAlchemy/Pydantic or equivalents | Versioned contracts; typed SRR/BIR; easy migrations for admin-only control plane |
| SQL AST | SQLGlot (parser/traversal) or comparable | Must supplement DB permissions, not replace them |
| ASR | Pretrained Whisper-family or tested alternatives | Actual Egyptian dialect WER/latency, supported licensing and operational cost |
| Translation (Arabic → English) | Pretrained MT model or the selected LLM with an ambiguity-preserving prompt, *unselected* | Egyptian-dialect adequacy, ambiguity preservation and entity fidelity on dev items; no fine-tuning |
| LLM | Hosted or local LLM, *unselected* | Structured extraction quality, English-to-SQL quality, latency, cost, Arabic language support, reproducibility |
| ERD | Mermaid/DBML/graph preview | Human-readability, diff support, export, no automatic DDL |
| Charts | Browser chart library | Deterministic chart rules for eligible result shapes |
| Evaluation | Pytest + dataset runner + metrics scripts | Reproducible annotations, run IDs, snapshots, CI integration |

**No framework/model/provider has been definitively chosen or installed based on the available project records.** Avoid creating fictional directory structure, environment files, GitHub URLs, CI results, deployed endpoints or credentials.

### 17.1 Proposed logical service boundaries

- `auth_workspace`: roles and department context; allowed contexts are server authoritative.
- `metadata_registry`: approved schema/catalog/aliases/views versioning.
- `analytics_orchestrator`: ASR transcript, BIR (from the Arabic), ambiguity-preserving translation and its audit, resolver/policy, English-to-SQL proposal and output formatting.
- `schema_design_orchestrator`: SRR, schema suggestion, sanity checks, diff, draft lifecycle.
- `approval_service`: Admin review, audit and publish decisions.
- `data_loader`: CSV/XLSX source validation and controlled import only.
- `safe_sql_gateway`: protected, read-only SQL execution; no caller access to write credentials.
- `evaluation_runner`: P0-P4/S0-S2 registry, snapshots, metrics and run logs.

This is a **logical decomposition**, not a mandate to build distributed microservices. A modular monolith is more realistic for a student MVP and avoids needless deployment complexity.

### 17.2 Possible API interactions (illustrations only)

`POST /analytics/ask`, `POST /analytics/clarify`, `POST /schema-proposals`, `GET /schema-proposals/{id}`, `POST /schema-proposals/{id}/review`, `GET /workspaces`, `GET /audit`, `POST /imports`; these are **example paths, not finalized API contracts**. All API authorization must be enforced server side. Define error shapes, schema versions and audit identifiers before implementation.

---

## 18. UI/UX and the team-approved high-level overview figure

### 18.1 Minimum UI screens (proposed)

1. **Hub Home / Department Selector:** displays only authorized departments and available modes.
2. **Ask Data:** voice button, transcript preview/edit, typed input, relevant clarification buttons, answer/chart/SQL and 'how the question was understood'.
3. **Schema Design:** text requirements brief, suggested entities/tables/columns/FKs, assumptions, high-impact questions, ERD preview, submit-for-review and revision diff.
4. **Admin Review:** proposal version, diff, uncertainty and missing requirements, accept/request changes/reject with reason, approval audit.
5. **Minimal Run/QA View** for team only: dataset status, test results, configured workspace and policy version.

### 18.2 High-level diagram — team- and supervisor-approved v6

The user has supplied a visual reference for the short, clean, **low-text system overview** favored by the professor. A dedicated **Figma Make prompt** and the style-only reference image were used in Figma Make to produce the figure; both are historical inputs kept in the registration package (`03_ARCHITECTURE_AND_FIGMA/`), not in this repository. The resulting export, approved by the project team and by the academic supervisor (recorded 23 Oct 2026 on the user's confirmation), is `assets/System-Overview-3840x2160-v6.png` (PNG, 3840 × 2160; SHA-256 `62d3743e297e5eba7c0ea0e062643c7f756291777911942b73e1e2bddd280653`, as recorded in the registration package manifest). This is not a formal university committee approval of the expanded scope; do not redesign, regenerate or replace it.

The single high-level figure should communicate only:

1. **One Central Hub** with three **functional department workspaces: Sales / Inventory / HR**.
2. **Two non-identical modes:** `Voice-to-SQL` for read-only analytics on authorized existing data; `AI Schema Design` for suggestions reviewed by `Admin`.
3. **Governed departmental data/approved metadata** uniting the modes after human-authorized provisioning and actual data loading.

Use short labels, minimal icons, generous space, no raw SQL, full table structures, lengthy bullet points, statistical percentages, benchmark names or detailed LLM processing steps. A detailed flow diagram can live elsewhere. Export only after human visual review, ideally in a high-resolution 16:9 format appropriate for the form.

**Compatibility with the TA-clarified pipeline (23 Oct 2026).** v6 shows *Voice / Text → Business Intent → Answer / Clarify / Abstain → Read-Only SQL*. It shows neither the speech-to-text nor the Arabic-to-English translation stage, which is consistent with the rule above that detailed processing steps stay out of the figure. Translation feeds SQL generation after the Answer decision (§8.1), so the figure summarizes the clarified flow rather than contradicting it. **The image is unchanged (SHA-256 re-verified).** Whether the supervisor or TA wants translation visible in the figure is an academic decision recorded as Q15. The approved image must not be edited without new supervisor approval.

---

## 19. Academic submission/form status

**The official MIU project registration form is still UNFILLED and UNSUBMITTED per the user's latest instruction.** The original V2 six-field draft is archived read-only in the registration package as `01_READ_ONLY_V2_BASELINE/MIU_FORM_V2_FROZEN_NOT_SUBMITTED.md` (not included in this repository). The final V3.1 field text, generated unchanged from the package's form draft (`04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md`), is in `docs/REGISTRATION_FORM_FIELDS.md` and contains the same six categories:

1. Project Title (**TA APPROVED 23 Oct 2026:** *Voice-to-SQL in Egyptian Arabic*; no category suffix unless separately required by the university).
2. Project Description / Abstract (**FINAL: exact 213-word text confirmed by the student 23 Oct 2026; revised short Abstract previously TA-approved, as reported by the student; inserted verbatim, do not rewrite**; the old 253-word version is superseded).
3. Project Scope (team-approved wording, unchanged).
4. AI Application (**student-confirmed final 23 Oct 2026**, covering the translation and English-to-SQL pipeline; subject only to the form's actual input limits).
5. Dataset (**student-confirmed final 23 Oct 2026** after the AraSpider licensing correction: custom benchmark primary; public Spider, BIRD Mini-Dev, Gretel, AraSpider and Casablanca with distinct roles; subject only to the form's actual input limits; the TA responded positively to the dataset evidence, not to the exact wording).
6. System Overview Diagram (**TEAM- AND SUPERVISOR-APPROVED: `System-Overview-3840x2160-v6.png`; not committee-approved; form not submitted**).

**Academic status nuance:** Earlier committee feedback said the *original V2 idea was suitable to submit*. The TA's support for new V3 additions **does not replace formal approval of the expanded registration**. A change to title, two-mode scope, dataset wording or diagram must be checked against actual form constraints and advisor review.

---

## 20. Proposed sequence and team workstreams

This is an **execution plan**, not an indication that tasks have been done or assigned to named students.

### Phase 0 — form preparation and scope lock (content complete 23 Oct 2026; submission pending)

*Status (D-31): the title (TA-approved, D-29), the Abstract (student-confirmed final, D-27) and all six form fields (D-30) are finalized, and v6 is supervisor-approved. Still open: the student's personal submission of the form, a check of the live form's input limits, and committee confirmation of the expanded scope (Q12). The bullets below are the original Phase 0 plan, kept as history.*

- The team-approved overview diagram (`System-Overview-3840x2160-v6.png`) exists; attach it unchanged to Field 6 when the form is finalized.
- Finalize the **official title** and concise abstract consistent with **team-selected Sales + Inventory + HR**, confirm exact Admin/operator sandbox provisioning boundaries and university form limits.
- Finalize V3 form fields using the team-approved overview diagram. Seek TA/committee confirmation of the **expanded** scope before treating registration as complete.
- Define the novelty and comparison statements carefully; do not assert market validation.

### Phase 1 — core baseline and permissions

- Create repo architecture, versioned design documents, PostgreSQL demo schema, import fixtures and protected analytic views.
- Implement authenticated workspace selection and read-only SQL privilege tests **before** connecting any LLM to the DB.
- Produce an approved metric catalog and one correct manual business report per metric.

### Phase 2 — BIR + voice + analytics

- Implement typed BIR flow, policy, safe SQL and chart traces.
- Add ASR with transcript confirmation, matched voice data and baseline tests.
- Enable **both Inventory and HR**, including the Inventory and HR Egyptian-Arabic voice test sets (DS-6), and test authorization/access denial across all three workspaces.

### Phase 3 — schema-design assistant and admin approvals

- Define SRR and versioned schema-artifact contracts; choose a small schema-quality annotation sample.
- Build propose/validate/preview/review flow with no automatic DDL execution.
- Compare S0/S1/S2, calibrate assumptions and review friction.

### Phase 4 — integration, evaluations and academic evidence

- End-to-end synthetic demo with approved schema metadata and controlled CSV import.
- Complete P2-versus-P4 paired comparisons, report risk/coverage and voice delta.
- Run permission and schema-review attack tests; conduct user interviews/tasks; record unknowns and limitations.
- Prepare defendable academic presentation, updated IEEE-style citations and reproducibility notes.

### 20.1 Suggested team split (if approximately four students)

- **Workstream A — Data & Security:** PostgreSQL, loader, views, role/department access, SQL guard tests.
- **Workstream B — Analytics NLP/ASR:** dialect terms, speech, BIR and selective-answering pipeline.
- **Workstream C — Schema Design & Admin:** SRR, schema proposals, ERD, reviewer workflows, audit/versioning.
- **Workstream D — Hub UI / QA & Evaluation:** frontend department switching, experiment runner, datasets, integration and user studies.

Workstreams are collaborative and names/ownership are **not yet assigned**. Everyone must understand metrics, threat boundaries and current status. `AGENTS.md` and `CLAUDE.md` in this repository brief teammates and their AI agents; the original team onboarding guide is archived in the registration package (`05_TEAM_AI_ONBOARDING/`, not included in this repository).

---

## 21. Risk register and scope control

| Risk | Why it matters | Mitigation / decision |
|---|---|---|
| Scope explodes across 'all departments' | Impossible to build/test universal platform within graduation timeline | **One-company three-workspace functional demo** (Sales/Inventory/HR), each bounded; no complete ERP/HR system. |
| Research contribution diluted | Two unrelated demos don't prove technical merit | Shared approved metadata/governance, separate hypotheses/metrics and integrated scenario. |
| SQL is executable but semantically wrong | Silent financial misinformation | BIR, metric definitions, material ambiguity and matched P2/P4 coverage controls. |
| AI-generated schema invents business requirements | Wrong application data model | SRR provenance, assumptions, targeted clarifications and Admin review. |
| Privilege bypass | Unauthorized departmental data leakage | Backend RBAC and DB grants; deny by default; adversarial cross-dept tests. |
| Schema proposal gets applied automatically | DDL risks and irreversibility | Review artifact only; separate authorized sandbox provisioning if ever added. |
| Real and synthetic datasets conflated | Misleading benchmark and wrong business metrics | Source provenance and honest synthetic labels. |
| ASR mistakes branch/product names | False answers despite valid SQL | Editable transcript; entity confidence; paired voice tests. |
| Market validation fabricated | Weak committee defense | Separate market context from interviews; report number of actual respondents only after collection. |
| Old form artifacts used as if current | Inconsistent submitted proposal | Immutable V2 archive, explicit V3 form draft, overview attachment pending. |
| Up-to-date competitor functions underestimated | False novelty claims | Inspect official documentation and evaluate baseline; dated source register. |

---

## 22. Decisions still open — do not silently fill these in

| ID | Pending decision | Current recommendation |
|---|---|---|
| Q01 | Exact official V3 project title | **Resolved 23 Oct 2026: TA APPROVED *Voice-to-SQL in Egyptian Arabic*** (confirmed by the student; D-29). No "(Company Ideas – IBM)" suffix unless the university separately requires it. Earlier options A/B were not selected. |
| Q02 | Professor's high-level overview layout/reference | **Resolved:** `System-Overview-3840x2160-v6.png` approved by the project team and the academic supervisor (supervisor approval recorded 23 Oct 2026); committee acceptance of the expanded scope pending. |
| Q03 | Initial department combination | **TEAM DECISION LOCKED: Sales + Inventory + HR** mandatory working MVP workspaces; formal form approval pending. |
| Q04 | Breadth of non-retail proof | **HR analytics is mandatory working non-retail domain**; additional clinic/library schema briefs optional for secondary evaluation. |
| Q05 | Admin approval scope | **TEAM WORKING DECISION:** Admin reviews/approves design artifact. Separate operator-controlled isolated sandbox provisioning may support the integrated Inventory demo. Never automatic production DDL. |
| Q06 | Does schema-design mode require voice? | Text mandatory; voice optional pending decision, without weakening analytics voice. |
| Q07 | Does TA's 'SQL' phrase require DDL preview or another tool? | Cannot infer from recording; ask if it affects form scope. *23 Oct 2026:* the TA's pipeline clarification (English-to-SQL) may cover it; not confirmed, so no new feature is added. |
| Q08 | Exact Inventory/HR/schema evaluation counts | Determine feasible small acceptance suites for **both Inventory and HR** during planning; all counts remain targets until verified. |
| Q09 | Models, libraries, hosting, exact API contracts | Choose after small spike and security design. |
| Q10 | Final accepted business metrics and data-generation scheme | Domain review and reproducible source constraints required. |
| Q11 | Admin vs developer permissions; approval audit retention | Freeze threat model and policy before coding. |
| Q12 | Formal committee approval of expanded V3 | Pending; TA acceptance is not committee registration. |
| Q13 | Exact text of the TA-approved short Abstract | **Resolved 23 Oct 2026:** the student supplied the exact text and confirmed it as the FINAL student-approved Abstract (TA approval of the revised short Abstract as reported by the student). It is in Form Field 2 verbatim (213 words). Do not rewrite it or restore the 253-word version. |
| Q14 | P3 redefinition as an English-only translation ablation | Proposed in the 23 Oct 2026 sync because translation is now in every pipeline. It is optional and does not affect the primary P2-vs-P4 comparison. Team confirmation pending. |
| Q15 | Should the translation stage appear in the high-level diagram? | v6 is unchanged and consistent at its level of abstraction (§18.2). Raise it with the supervisor only if the TA or supervisor asks. Never edit the approved image without new supervisor approval. |

---

## 23. Prepared short explanation for a team member / supervisor

> We are extending our Egyptian-Arabic Voice-to-SQL project without removing its existing reliability features. The AI hub is one common interface for different departments, each with approved database context and access permissions. Managers can ask voice or text questions through a BIR-based ambiguity-aware system that answers, asks a clarification, or abstains before running safe read-only SQL. Separately, a developer can describe an application's needs—even with incomplete requirements—and receive proposed database tables, columns and relationships, with assumptions and an ERD for an administrator to approve. Once an approved schema is **actually provisioned and populated** in a controlled environment, the same hub can support grounded analytics against it. Our market need is a hypothesis; we will compare against strong existing products and controlled research baselines.

---

## 24. Sources, previous artifacts and evidence register

### 24.1 Frozen project sources (registration package; not in this repository)

These files remain, hash-verified and unaltered, in the registration package `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip`; `PROJECT_EVOLUTION.md` summarizes them.

- `01_READ_ONLY_V2_BASELINE/VOICE_TO_SQL_PROJECT_HANDOVER_V2_FROZEN.md` (registration package): prior comprehensive V2 snapshot (31 sections), **unaltered**.
- `01_READ_ONLY_V2_BASELINE/AI_AGENT_STARTER_PROMPT_V2_FROZEN.md` (registration package): prior prompt, **unaltered**.
- `01_READ_ONLY_V2_BASELINE/MIU_FORM_V2_FROZEN_NOT_SUBMITTED.md` (registration package): prior six-field form draft, **unaltered**.
- External previous PDFs and presentation files existed in earlier conversation history but are **not** represented as final V3 artifacts. No new presentation is claimed complete; the overview diagram v6 is team-approved (§18.2).

### 24.2 Research and public references (links; accessed/verified Oct 22, 2026)

- [R1] OECD (2025), *SME and Entrepreneurship Policy in Egypt*, https://doi.org/10.1787/195d9c43-en . Market digitization context only.
- [R2] Visa/MSMEDA (2025), *Value of Acceptance* press release, https://www.visa.com/en-eg/newsroom/egypt-smes-digital-payments-growth-study . Payments figures, *not project-specific demand*.
- [R3] Saparina & Lapata (2024), *AMBROSIA*, NeurIPS, https://ambrosia-benchmark.github.io/ and https://proceedings.neurips.cc/paper_files/paper/2024/hash/a4c942a8405cc910f0a833d28d2573cc-Abstract-Datasets_and_Benchmarks_Track.html . Ambiguity benchmark.
- [R4] Dong et al. (2025), *PRACTIQ*, NAACL, https://aclanthology.org/2025.naacl-long.13/ . Ambiguity and unanswerability benchmark.
- [R5] Almohaimeed et al. (2024), *Ar-Spider*, https://arxiv.org/abs/2402.15012 . Arabic written Text-to-SQL, not Egyptian voice.
- [R6] Wang et al. (2025), *Text2Schema / SchemaAgent*, https://arxiv.org/abs/2503.23886 . Research on NL→schema; v1 reported more than 500 pairs, v2 reports 381; repository file holds 518 records; no repository license (verified 22 Oct 2026).
- [R7] Microsoft Learn, *Build apps through conversation with Copilot*, https://learn.microsoft.com/en-us/power-apps/maker/canvas-apps/ai-conversations-create-app . Table/relationship generation.
- [R8] dbdiagram official AI Assistant docs, https://docs.dbdiagram.io/ai-assistant/ . Natural-language database modeling.
- [R9] Wren AI docs, https://docs.getwren.ai/oss/reference/architecture . Semantic context, SQL and ambiguity primitives.
- [R10] Databricks AI/BI Genie docs, https://docs.databricks.com/aws/en/genie/ . Governed conversational analytics.
- [R11] SQLGlot docs, https://sqlglot.com/ . SQL parser, **not a complete validator**.
- [R12] UCI Online Retail II, https://archive.ics.uci.edu/dataset/502/online+retail+ii . Candidate real source.
- [R13] Contoso Data Generator V2, https://github.com/sql-bi/Contoso-Data-Generator-V2 . Candidate synthetic source.
- [R14] Casablanca dataset, https://huggingface.co/datasets/UBC-NLP/Casablanca . Multidialectal speech corpus; Egypt subset verified (CC BY-NC-ND 4.0, research-only; validation/test splits only).
- [R15] Yu et al. (2018), *Spider*, https://huggingface.co/datasets/xlangai/spider (arXiv:1809.08887). English cross-domain Text-to-SQL; CC BY-SA 4.0 (HF API, 23 Oct 2026).
- [R16] Li et al. (2023), *BIRD* / BIRD Mini-Dev, https://huggingface.co/datasets/birdsql/bird_mini_dev (arXiv:2305.03111). English Text-to-SQL incl. PostgreSQL; CC BY-SA 4.0 (HF API, 23 Oct 2026).
- [R17] Heakl et al. (2024), *AraSpider*, https://huggingface.co/datasets/ahmedheakl/araspider (arXiv:2402.07448). MSA–English–SQL. HF repository declares MIT; the underlying Spider data is CC BY-SA 4.0; redistribution terms are uncertain, so it is a reference only.
- [R18] Gretel (2024), *synthetic_text_to_sql*, https://huggingface.co/datasets/gretelai/synthetic_text_to_sql . 105,851 synthetic English question–SQL pairs, 100 domains; Apache 2.0 (HF API, 23 Oct 2026).
- [R19] Bhaskar et al. (2023), *AmbiQT*, https://github.com/testzer0/AmbiQT . Ambiguous Text-to-SQL questions with two valid SQL queries; ambiguity research reference only.
- Text-to-SQL research package (independent, not modified; discovery report, verification log, evidence screenshots E1–E5): a separate local research folder dated 23 Oct 2026, kept outside both the registration package and this repository. The dataset facts used by the project are restated in R15–R19 above.

References are not evidence that full source text or dataset licensing has been approved for project use; verify before external submission and datasets reuse. The more detailed source/method map is archived in the registration package (`06_RESEARCH_AND_DATA/`, not included in this repository).

---

## 25. Agent operational rules and collaboration protocol

1. Read this entire V3.1 file, `PROJECT_STATUS.md`, `PROJECT_EVOLUTION.md` (decision index) and `AGENTS.md`. The **V2 frozen handover** (archived in the registration package, not in this repository) is for historical details only, never to override explicit V3 deltas.
2. First report **current known status**, **assumptions**, **unresolved decisions**, and the **exact task requested**.
3. Keep the scope separated: Analytics (M1–M8) versus Schema Design (M9) versus Hub Governance (M10); **Sales, Inventory and HR are all mandatory planned working workspaces, not deferred examples**.
4. Preserve voice, the three confirmed differentiators and read-only query safety. Do not add production DDL execution without a new explicit decision.
5. Do not generate fake project results, dataset counts as if achieved, committee approvals, GitHub commits, architecture screenshots, benchmarks or user interviews.
6. Never treat the academic form as filled or submitted; current purpose is **preparing to fill it**.
7. Treat `assets/System-Overview-3840x2160-v6.png` as the **team-approved** high-level overview. Never redesign, regenerate or replace it; update form Section 6 **without erasing history** and only with user approval.
8. Before coding: ask for repository, stack and assigned task when those truly block implementation. Otherwise complete planning or drafting tasks with explicit proposals.
9. When explaining to Egyptian student teammates, prefer **Egyptian Arabic with English technical terms**, but keep the canonical specification and formal academic form copy in English unless directed otherwise.
10. Record revisions in the change log with date, who authorized, impacted form sections, and whether an artifact was actually executed/tested.

## 26. Current delivery and next exact step

**Completed for this handover only:** **V3.1 team scope baseline** with mandatory Sales/Inventory/HR, immutable V2 and V3-draft history, updated delta log, runtime read-only contract, university form **draft** (not entered), **Figma Make overview prompt** after reference receipt, **team-approved overview diagram v6**, team-approved dataset strategy (DS-1–DS-8), team onboarding + reusable prompts, research caveats and ZIP manifest.

**Not completed:** official form, committee registration,  architecture approval, implementation, database provisioning, ASR integration, schema generation, dataset collection, annotation, research evaluation, real user studies and student task assignments.

**Next actual step (23 Oct 2026):** (1) done: the exact TA-approved short Abstract is in Field 2 (Q13 resolved); (2) done: the TA approved the title *Voice-to-SQL in Egyptian Arabic* (Q01 resolved); (3) done: the student confirmed Fields 4–5 as final (D-30), subject only to the form's input limits; (4) done: an independent final review of the package (ChatGPT) was completed (reported by the student, 23 Oct 2026); (5) the user personally fills and submits the official form. Implementation does not start until separately authorized.

---

## 27. V3 change log

| Date | Version | Change | Status |
|---|---|---|---|
| 2026-10-20 to 2026-10-21 | V2 | Retail Voice-to-SQL, M1–M8, BIR/ambiguity/selective answering, matched P2/P4 | Frozen prior design |
| 2026-10-22 | V3 DRAFT | TA-approved Central Hub direction + TA-requested schema assistance + admin review, M9/M10, department governance and new evaluation track | Proposed implementation integration, **not yet submitted** |
| 2026-10-22 | **V3.1 TEAM BASELINE** | User fixed **three mandatory workspaces: Sales, Inventory, HR**; professor encouraged feasible implemented expansion; supplied visual reference; Figma Make prompt and updated form draft prepared | **Team scope adopted; figure/form/implementation not completed** |
| 2026-10-22 | **V3.1 documentation sync (DS-9/DS-10)** | Team approved System Overview v6; dataset strategy DS-1–DS-8 approved (DS-6/DS-7 with methodological corrections); metric definitions refined (separate Security suite; unsafe direct answers; clarification denominators); form draft Fields 5–6 synchronized | **Documentation synchronized; form NOT submitted; no implementation; team approval only** |
| 2026-10-23 | **Supervisor diagram approval and Field 5 links** | Academic supervisor approved System Overview v6 (recorded on the user's confirmation; image unchanged); form Field 5 restructured with verified direct dataset links and licenses | **Not committee approval; form NOT submitted; no implementation** |
| 2026-10-23 | **Final registration synchronization (D-20–D-24)** | TA-clarified pipeline (translation + English-to-SQL) written into §1, §5, §8.1–§8.3, §17; Arabic-anchored BIR and decision before any SQL; P2/P4 matched inputs incl. same ASR and cached translation; P3 redefined (Q14); translation and semantic-vs-SQL error metrics (§15.2); English equivalents in gold data (§14.2); public Text-to-SQL references (§14.5, R15–R19); title pending TA confirmation (Q01); Abstract text verification (Q13); diagram compatibility note (§18.2, Q15) | **Documentation only; v6 image unchanged; form NOT submitted; no implementation** |
| 2026-10-23 | **TA-approved Abstract inserted (D-26) and confirmed final by the student (D-27)** | Student supplied the exact short Abstract (213 words) and confirmed it in writing as the FINAL student-approved Abstract; the TA previously approved the revised short Abstract (as reported by the student); inserted verbatim into Form Field 2; Q13 resolved | **Form NOT submitted; title still pending TA confirmation** |
| 2026-10-23 | **Student-preferred title (D-28)** | Student chose *Voice-to-SQL in Egyptian Arabic* (variant *(Company Ideas – IBM)* only if the category is required) instead of options A/B; recorded as a candidate pending TA confirmation; scope, Abstract, diagram and dataset decisions unchanged | **Not TA-confirmed; form NOT submitted** |
| 2026-10-23 | **Title TA-approved (D-29)** | TA explicitly approved *Voice-to-SQL in Egyptian Arabic* (confirmed by the student); Field 1 marked TA APPROVED; no category suffix unless separately required; Q01 resolved; pending-title blocker removed | **Form NOT submitted; scope, Abstract, Fields 4–5, datasets and v6 unchanged** |
| 2026-10-23 | **Fields 4–5 student-confirmed final (D-30)** | Student approved Field 4 as final and Field 5 after an AraSpider licensing correction (HF repository MIT vs underlying Spider CC BY-SA 4.0; redistribution terms uncertain; reference only); length check found no known form limit, so no shorter versions were prepared | **All six fields final; form NOT submitted** |
| 2026-10-23 | **Repository amendment (D-31)** | Clean-repository corrections only: package paths re-pointed to repository files or labelled as registration-package archives; V2 form filename corrected (§19); stale status wording updated (header snapshot, §1.2, §20 Phase 0, §26); see `docs/CHANGE_RECORD_D-31.md` | **No change to scope, title, Abstract, v6, architecture decisions or evaluation methodology; form NOT submitted** |

**End of the V3.1 team-approved planning specification.**
<!-- END AMENDED DERIVATIVE source="02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md" -->
