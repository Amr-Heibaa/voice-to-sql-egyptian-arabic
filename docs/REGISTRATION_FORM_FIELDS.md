# Final Registration Form Fields (V3.1) — Submitted 25 Oct 2026

> **Repository note (updated 24 Oct 2026).** The block below records the final copy-paste text of the six MIU registration-form fields.
>
> - **Source:** `FINAL_FORM_COPY_PASTE.md` in the final export folder (generated unchanged from `04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md` in `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip`, which is not included in this repository). **Original source SHA-256:** `157d641e856a4602f2f717f306865c1eb8fef2fb773f6a7fe9a362c20a36f804`.
> - **This is an amended derivative, not a byte-identical copy.** D-31 changed two explanatory lines outside the field boxes ([CHANGE_RECORD_D-31.md](CHANGE_RECORD_D-31.md)). **D-33** (24 Oct 2026) replaced the **Field 1** value with the TA-approved official title *ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic* and updated the header line ([CHANGE_RECORD_D-33.md](CHANGE_RECORD_D-33.md)). **The text inside the field boxes for Fields 2–6 is byte-identical to the source** and is verified box by box. **Derivative SHA-256:** `9a5eb9b44459c1330baff9b3a3eb698f263f7d2e03a9a56148f06f9edb28233f`.
> - **All six fields are final** (title TA-approved, D-33; Abstract student-confirmed final; Fields 4–5 student-confirmed final; Scope team-approved; diagram team- and supervisor-approved). **Status update (D-37):** the student submitted the form personally; the owner confirmed the submission on 25 Oct 2026. Committee acceptance is not confirmed. The status line inside the block below is the dated 23–24 Oct snapshot and is kept unchanged.
> - The **Abstract (Field 2) must never be rewritten**, shortened, expanded or translated.

<!-- BEGIN AMENDED DERIVATIVE source="FINAL_FORM_COPY_PASTE.md" source_sha256="157d641e856a4602f2f717f306865c1eb8fef2fb773f6a7fe9a362c20a36f804" derivative_sha256="9a5eb9b44459c1330baff9b3a3eb698f263f7d2e03a9a56148f06f9edb28233f" amendment="D-31,D-33" -->
# MIU Registration Form — Final Copy-Paste Values

**ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic** · V3.1 · 23 October 2026 (Field 1 updated 24 October 2026, D-33) · Registration status: **NOT SUBMITTED**

Copy only the text inside each box. Every value is extracted unchanged from the registration package's form draft (`04_FORM_PREPARATION_NOT_SUBMITTED/MIU_FORM_V3_1_DRAFT_NOT_SUBMITTED.md`, not included in this repository), except Field 1, which was updated on 24 October 2026 to the newly TA-approved title (D-33); the package draft still holds the earlier title.

## Field 1 — Project Title

```text
ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic
```

## Field 2 — Project Description (Abstract)

```text
Managers in small and medium-sized organizations often need quick answers from business databases but depend on technical staff to write SQL queries. However, ambiguous Egyptian-Arabic business questions can cause silent semantic errors, where a technically valid SQL query returns a business answer that does not match the user’s intended meaning.

This project proposes an AI Central Hub for one synthetic demonstration company with three functional, separately authorized workspaces: Sales, Inventory and Human Resources. Users will ask typed or spoken Egyptian-Arabic questions; the system will convert each question into a structured Business Intent Representation grounded in an approved departmental catalog, detect material ambiguity or missing data, and select one of three decisions (Answer, Clarify or Abstain) before generating guarded, read-only SQL whose results come directly from the database.

A second mode will help developers turn incomplete application requirements into proposed relational schemas with explicit assumptions and open questions for human Admin review; approval will not execute database changes.

The primary evaluation will compare this ambiguity-aware approach with a strong, clarification-enabled LLM baseline under matched data and context, measuring business-answer accuracy, silent errors, clarification quality and risk–coverage trade-offs for voice and text questions. Verification will test SQL safety, cross-department access control and the review workflow, while schema proposals will be assessed separately by independent reviewers.
```

## Field 3 — Project Scope

```text
The project will deliver one AI Central Hub for a single, explicitly synthetic demonstration company, with two complementary modes. Mandatory MVP capabilities: (1) three functional, separately authorized workspaces (Sales, Inventory and HR) that share one analytics engine but use department-specific schemas, approved metric catalogs and permissions; (2) typed and spoken Egyptian-Arabic questions with an editable speech transcript; (3) Business Intent extraction, ambiguity detection and an Answer/Clarify/Abstain policy with at most one clarification turn; (4) guarded, read-only SQL over authorized views, returning results, charts and the interpretation used; and (5) authentication, server-side department authorization and audit logging. Sales is the primary research domain: the main contribution is the reliable interpretation of ambiguous Egyptian-Arabic business questions, evaluated against a strong baseline. Inventory will support stock-level, stock-movement and reorder-threshold analytics, and HR will support headcount and leave analytics on invented records; both demonstrate context switching and denial of unauthorized cross-department access. The secondary capability is AI-assisted schema design: a developer submits incomplete requirements and receives proposed tables, attributes, keys, relationships, assumptions and questions, which an Admin approves, revises or rejects as versioned drafts. Approval publishes metadata only; any database setup and data loading are performed separately by an authorized operator in an isolated demonstration environment, as in the planned Inventory end-to-end scenario. Excluded from the MVP: complete ERP, HR or payroll systems; automatic production DDL; autonomous application generation; real personal data; multi-company deployment; live ERP/POS connectors; and training foundation models.
```

## Field 4 — AI Application

```text
AI will be used where the system must understand flexible human language, while deterministic controls will enforce correctness and safety. (1) Speech recognition: a pretrained multilingual ASR model, selected on development data, will transcribe spoken Egyptian Arabic into an editable transcript that the user confirms; machine learning is suitable because dialect pronunciation, code-switching and speaker variation cannot be captured reliably by hand-written rules. (2) Business intent understanding: a large language model will map the confirmed Egyptian-Arabic question to a structured Business Intent Representation (metric, entities, filters, time period and ranking) using only the approved catalog of the user's workspace; this handles synonyms, dialect wording and incomplete phrasing. (3) Ambiguity support: working on the original Arabic wording, the model will propose candidate interpretations and flag unresolved meanings, while deterministic resolvers and an explicit policy decide whether to answer, ask one clarification question or abstain, so decisions do not rely on model confidence alone. (4) Translation: a pretrained translation or language model will translate the confirmed question into English and is instructed to preserve ambiguous terms. The Arabic original remains the reference for intent, so an English rendering such as "most profitable" cannot silently resolve the Egyptian word "كسبان" (earned the most). (5) English question-to-SQL: only after an Answer decision (directly or after one clarification), the model will generate a SELECT query from the English question and the resolved intent. The query must pass a SQL parser, an allowlist of authorized views, department authorization, consistency checks against the intent and execution under read-only database permissions, so reported numbers come from the database, not from the model. Clarify and Abstain decisions execute no SQL. (6) Schema design: the model will recommend tables, attributes, keys and relationships from incomplete application descriptions and label its assumptions and open questions; deterministic validators check keys and references, and a human Admin approves, revises or rejects each version, with no automatic database changes. Authentication, department permissions, SQL validation, the decision policy and Admin approval are rule-based or human-controlled, not AI. The project will use existing pretrained speech, translation and language models with prompting and vocabulary guidance; it does not require training or fine-tuning any model.
```

## Field 5 — Dataset

```text
The project requires data, and the primary data will be created by the team: no verified public dataset combines Egyptian-Arabic business questions, ambiguity labels, SQL and a multi-department company database. The system follows the pipeline Egyptian-Arabic voice → speech-to-text → Arabic transcript → Arabic-to-English translation → English question-to-SQL, while the original Arabic question is kept for intent and ambiguity checks. Pretrained models will be used without training or fine-tuning, so the datasets below serve evaluation, model selection and reference. All project-generated data are planned, not yet collected, and not publicly available.

A. Project-generated data (primary)
(1) Egyptian-Arabic Question-to-SQL benchmark (primary evaluation): about 400 written Sales items, comprising 375 semantic items (about 180 clear → Answer, 110 ambiguous → Clarify and 85 unanswerable or out-of-scope → Abstain) and 25 authorization and security cases evaluated separately, plus smaller Inventory and HR sets in the same format. Each item contains the Egyptian-Arabic question, a human-reviewed English equivalent that preserves any ambiguity, a Business Intent annotation, the expected decision, the clarification target for ambiguous items, a reason code for Abstain items, and gold SQL with its expected result for every supported answerable interpretation. Example: "مين أكتر فرع كسبان الشهر اللي فات؟" ("Which branch earned the most last month?") → Clarify (highest net sales or highest gross profit). Two annotators label intent and decision independently; a second person checks every gold SQL query against the exact question and executes it on two snapshots of the project's own synthetic PostgreSQL database. Development and test sets are separated by question template.
(2) Synthetic company database (PostgreSQL), on which all gold SQL runs: a documented, seeded generator will create one fictitious Egyptian company with Sales (branches, products, sales, returns and time-dependent costs), Inventory (a stock-movement ledger derived from the same sales, with snapshots and reorder thresholds) and HR (departments, employees and leave requests with invented records only). Automated checks verify foreign keys, stock reconciliation and leave-date rules.
(3) Voice recordings: a core set of 192 spoken benchmark questions from at least 10 consenting native Egyptian-Arabic speakers, with manually verified transcripts, collected under a written consent and privacy protocol; development and test sets use different speakers and question templates.
(4) Schema-design benchmark: 30–60 deliberately incomplete application briefs with independently reviewed reference designs.

B. Public datasets (reference, model selection or optional evaluation only; not merged with project data and not translated into the test set)
(5) English question-to-SQL. Spider: English questions paired with SQL over multi-table databases; reference benchmark. https://huggingface.co/datasets/xlangai/spider (CC BY-SA 4.0). BIRD Mini-Dev: English questions with gold SQL, including PostgreSQL; optional check of the English-to-SQL component. https://huggingface.co/datasets/birdsql/bird_mini_dev (CC BY-SA 4.0). Gretel Synthetic Text-to-SQL: synthetic English question–SQL pairs across business domains such as retail and human resources; additional English-to-SQL reference. https://huggingface.co/datasets/gretelai/synthetic_text_to_sql (Apache 2.0).
(6) Arabic–English–SQL alignment. AraSpider: Spider's English questions with Modern Standard Arabic translations and the same SQL; reference for translation-based Text-to-SQL, not Egyptian dialect. https://huggingface.co/datasets/ahmedheakl/araspider (licensing: its Hugging Face repository declares MIT, while the underlying Spider dataset is licensed CC BY-SA 4.0; because the redistribution terms of the derived content are uncertain, it is used for reference only and not redistributed).
(7) Egyptian-Arabic speech recognition. Casablanca, Egyptian subset: ASR evaluation only (validation split for model selection, test split for final reporting). https://huggingface.co/datasets/UBC-NLP/Casablanca (CC BY-NC-ND 4.0, research use only).
Ambiguity benchmarks such as AMBROSIA and AmbiQT inform the ambiguity categories and are not used as data. UCI Online Retail II (CC BY 4.0) and Contoso Data Generator V2 (MIT) remain optional, separately reported retail references outside the main benchmark.
```

## Field 6 — High-Level System Overview Diagram (file to upload)

```text
System-Overview-3840x2160-v6.png
```

Field 6 file location in this repository: `assets/System-Overview-3840x2160-v6.png` (byte-identical to `MIU_VoiceToSQL_V3_1_Team_Scope_Freeze_2026-10-22/03_ARCHITECTURE_AND_FIGMA/System-Overview-3840x2160-v6.png` in the registration package).
<!-- END AMENDED DERIVATIVE source="FINAL_FORM_COPY_PASTE.md" -->
