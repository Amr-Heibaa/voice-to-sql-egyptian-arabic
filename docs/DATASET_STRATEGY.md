# V3.1 Dataset Strategy — ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic

> **Repository note (23 Oct 2026).** The block below is the **team-approved dataset strategy** (DS-1–DS-8 approved 22 Oct 2026; DS-11 synchronized 23 Oct 2026).
>
> - **Source:** `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md` in `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip`. **Original source SHA-256:** `724ac0b92b82ec1ddcfbe93bf596683e6c1481e7104e151112ac3150a62adf05` (kept for provenance).
> - **This is an amended derivative, not a byte-identical copy.** Repository amendment **D-31** (23 Oct 2026) changed only references and stale status wording; every change, with its before and after text, is listed in [CHANGE_RECORD_D-31.md](CHANGE_RECORD_D-31.md). **Derivative SHA-256:** `a29aa0926496f2823682cf4b2498c70a3505fae270f51dbfc6b3b229af9d8038`.
> - **Nothing below has been generated, collected, recorded, annotated or licensed.** Custom datasets and recordings are **planned**; all counts are targets. Live status: [PROJECT_STATUS.md](../PROJECT_STATUS.md).
> - **Third-party datasets** named below are referenced only. None is included in or redistributed through this repository, and the project claims no ownership of them or redistribution rights over them; each keeps its own license and terms.

<!-- BEGIN AMENDED DERIVATIVE source="06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md" source_sha256="724ac0b92b82ec1ddcfbe93bf596683e6c1481e7104e151112ac3150a62adf05" derivative_sha256="a29aa0926496f2823682cf4b2498c70a3505fae270f51dbfc6b3b229af9d8038" amendment="D-31" -->
# V3.1 Proposed Dataset Strategy

**Date:** 22 October 2026 · **Status:** **TEAM-APPROVED PLAN** (DS-1–DS-8 approved 22 Oct 2026; DS-6 and DS-7 as corrected; this is not university committee approval). Nothing below is built, collected, licensed or measured. Counts are **targets**. Evidence for every external source was recorded in the registration package's dataset verification log and the reasoning in its dataset deep-research record (`06_RESEARCH_AND_DATA/V3_1_DATASET_VERIFICATION_LOG.md`, `06_RESEARCH_AND_DATA/V3_1_DATASET_DEEP_RESEARCH.md`; neither is included in this repository). The conclusions this plan relies on (sources, links, licenses and roles) are restated in §11 and in `docs/SPECIFICATION.md` §14.5 and §24.2.

**Final registration synchronization (23 Oct 2026):** the TA clarified the pipeline (voice → speech-to-text → Arabic transcript → Arabic-to-English translation → English question-to-SQL) and replied positively to the Spider / BIRD Mini-Dev / AraSpider evidence. This file now adds (a) **human-reviewed English equivalents** to every benchmark item (§7.1–§7.3), (b) matched translation inputs for P2/P4 (§7.4), (c) translation-stage evaluation (§7.6) and (d) **DS-11 public Text-to-SQL references** by pipeline stage (§11). The planned counts are **unchanged**: 375 + 25 Sales, Inventory and HR ≈60 each, 192 recordings, 30–60 briefs. No fine-tuning is introduced. The TA's positive reply supports the evidence; it is not formal approval of the final form wording.

---

## 1. Principles

1. **One integrated synthetic demonstration company (Context A)** supplies all Sales, Inventory and HR data for the hub, the demos and the **primary** P2-vs-P4 study. It is labeled "synthetic" everywhere.
2. **External public data runs as separate tracks (Context B and background benchmarks).** It is never merged into Context A and never "completed" with fabricated columns.
3. **Gold labels come from humans and the database**, never from the system under test.
4. **The evaluation is frozen before the methods are tuned:** data seed, catalog version, as-of date and test split are fixed and hashed before any P2/P4 prompt iteration on the test split (there is none; only dev is used for iteration).
5. **License-unknown means no permission.** No-license resources are used only after written permission, or not at all.

## 2. Unified data map

| Component | Download and use (subject to license) | Adapt / transform | Generate synthetically | Manually annotate | Human validation required | Can be postponed? |
|---|---|---|---|---|---|---|
| **Sales (primary)** | — | (Optional) Contoso V2 small snapshot as replication DB: rename to PostgreSQL schema, add catalog | **Context A Sales generator** (6 tables) | ~400 typed questions + BIR, interpretation and decision labels | Gold SQL and results; ambiguity adjudication | Contoso replication: **yes**. Online Retail II track: **yes** |
| **Sales external validation** | UCI Online Retail II (CC BY 4.0) | Normalize to `invoices`, `invoice_lines`, `products_ors`, `customers_ors`; cancellations flagged | **Nothing** (no fake branches or costs) | ~40–60 questions incl. legitimate *Abstain* items (branch, profit) | Yes | **Yes** (optional) |
| **Inventory** | — (WWI used as design reference only) | — | **Same Context A generator**: ledger → snapshots, thresholds, transfers | ~60 acceptance questions | Invariant tests + manual spot checks | No |
| **HR** | — (test_db / AdventureWorks as reference only) | — | **Context A HR generator** | ~60 acceptance questions | Leave-day rules reviewed | No |
| **Speech, primary eval** | — | — | — | **Custom recordings**: 192 core (Sales 144, Inventory 24, HR 24; optional ≈260) | Transcripts double-checked | No (Sales core subset); size can shrink |
| **Speech, background** | Casablanca-Egypt validation (model selection) + test (final background report only) (CC BY-NC-ND, research-only) | Text normalization for WER | — | — | — | Partly (MGB-3, ArzEn: yes) |
| **Ambiguity benchmark** | — (AMBROSIA, AmbiQT, PRACTIQ, TrustSQL used for taxonomy/protocol only) | — | — | Full label set (§7) | Two annotators + adjudicator | No |
| **English equivalents (translation reference)** | — | — | — | One ambiguity-preserving English equivalent per benchmark item (§7.3 step 2b) | Second bilingual annotator verifies meaning **and** preserved ambiguity | No (part of every item) |
| **Public Text-to-SQL references (DS-11)** | Spider, BIRD Mini-Dev, Gretel synthetic Text-to-SQL, AraSpider (§11) | None (no translation into Egyptian Arabic) | — | — | — | **Yes** (reference or optional checks only) |
| **Authorization tests** | — (RBAC benchmark paper as reference) | — | Roles, users, adversarial prompts | Expected deny/allow | Yes | No |
| **Schema design (secondary)** | — | (If permitted) RSchema 30–50 record sanity subset | — | 30–60 incomplete briefs + gold design spaces | Independent reviewers | RSchema subset: **yes** |

---

## 3. Sales: Context A synthetic retail company

### 3.1 Company profile (proposal)
A fictitious Egyptian electronics-and-home retail chain, e.g. **"Nile Mart (synthetic)"**:
- **Branches:** 8–10 (Cairo ×3, Giza, Alexandria ×2, Mansoura, Tanta, Assiut), plus 1 central warehouse (inventory only). Include **confusable names** on purpose (e.g., "مدينة نصر" Nasr City vs "مصر الجديدة" Heliopolis; "إسكندرية" Alexandria vs "الإسماعيلية" Ismailia only if Ismailia is a real branch) to create genuine entity ambiguity and ASR risk.
- **Products:** 300–500 across 8–12 categories; Arabic name + English name + SKU. Include products whose names are English loanwords (code-switching).
- **Period:** 24 months (e.g., 2024-07-01 → 2026-06-30); fixed **as-of date** for evaluation (e.g., 2026-06-30); timezone Africa/Cairo; Fri/Sat weekend; Ramadan, Eid and back-to-school seasonality.
- **Volume:** ~150k–300k sales lines, enough for meaningful aggregates and small enough for laptop PostgreSQL.

### 3.2 Physical schema (canonical six tables + helpers)

```text
stores(store_id PK, store_code UNIQUE, name_ar, name_en, city, region, opened_on, closed_on NULL, is_warehouse BOOL)
product_categories(category_id PK, name_ar, name_en, parent_id FK NULL)
products(product_id PK, sku UNIQUE, name_ar, name_en, category_id FK, brand, list_price, is_active)
product_costs(product_id FK, valid_from DATE, valid_to DATE NULL, unit_cost NUMERIC, PK(product_id, valid_from))
sales_headers(sale_id PK, store_id FK, sold_at TIMESTAMPTZ, channel {in_store, online}, header_discount_amt NUMERIC DEFAULT 0, status {completed, cancelled})
sales_lines(sale_line_id PK, sale_id FK, product_id FK, quantity INT>0, unit_price NUMERIC, line_discount_amt NUMERIC DEFAULT 0)
returns(return_id PK, sale_line_id FK, returned_at, returned_qty INT>0, refund_amt NUMERIC, reason_code, restockable BOOL)
calendar(date PK, is_weekend, is_holiday, holiday_name_ar, fiscal_month, fiscal_quarter)   -- helper
```

**Business conventions** (decided in the catalog, frozen before question writing):
- **Discounts:** line-level only; `header_discount_amt` is kept but always 0 in MVP data to avoid double counting. Alternatively drop it.
- **Gross sales** = Σ qty × unit_price · **Net sales** = gross − line discounts − refunds (by return date or by sale date: **choose one and document it**; this is itself a good ambiguity item).
- **COGS** uses the cost valid on the sale date. **Gross profit** = net sales − COGS of net units. **Net profit** is **not computable** (no opex), so it's an Abstain target.
- **Cancelled** headers are excluded from all metrics.

### 3.3 Generator design
- Python, single seed, parameters in a versioned YAML; outputs CSV and a PostgreSQL load script; deterministic (same seed → byte-identical CSV hashes).
- Demand = branch size × category seasonality × weekday × holiday × random noise. Prices follow cost + margin bands (margins differ by category so that **revenue rank ≠ profit rank** for some branches/months: *engineered material ambiguity*, documented).
- Returns: category-specific rates (e.g., 2–8%), lag 1–30 days, partial quantities.
- **Two evaluation snapshots:** `S1` (seed A) and `S2` (seed B, same parameters), used to check that gold SQL is robust and to detect coincidental equal results across interpretations.
- **Acceptance tests:** row counts, FK integrity, no negative quantities, return qty ≤ sold qty, cost validity coverage for every sold product/date, metric reconciliation (manual calculation of 10 reference numbers in a spreadsheet).

### 3.4 Anti-bias controls for the primary study
1. Generator parameters and catalog are **frozen and hashed** before any benchmark question is written, and stay frozen through final method evaluation. Because the primary data is synthetic, external generalization is limited; this is reported as a limitation.
2. Question writers ≠ generator authors where team size permits; writers see the catalog and schema, not P4 internals.
3. A **Contoso V2 replication snapshot** (10K-orders release, MIT) with a small mirrored question subset is recommended (postponable) to show the P2/P4 gap isn't an artifact of our own data.

### 3.5 Context B: UCI Online Retail II (optional, separate)
Separate PostgreSQL schema `ext_online_retail`. Real-data questions only on existing fields. Branch and profit questions are labeled **ABSTAIN (data not available)**. Report separately with CC BY 4.0 attribution.

---

## 4. Inventory: unified ledger in Context A

### 4.1 Schema

```text
stock_movements(movement_id PK, product_id FK, store_id FK, moved_at TIMESTAMPTZ,
                movement_type {RECEIPT, SALE, RETURN_TO_STOCK, TRANSFER_OUT, TRANSFER_IN, ADJUSTMENT, WRITE_OFF},
                quantity INT /* signed: + in, - out */, ref_sale_line_id FK NULL, ref_return_id FK NULL,
                ref_transfer_id NULL, ref_po_id NULL)
inventory_snapshots(snapshot_date, product_id FK, store_id FK, on_hand_qty INT, PK(snapshot_date, product_id, store_id))  -- derived daily or weekly
reorder_thresholds(product_id FK, store_id FK, valid_from, valid_to NULL, reorder_point INT, reorder_qty INT, PK(product_id, store_id, valid_from))
purchase_orders(po_id PK, store_id FK, ordered_at, expected_at, received_at NULL, status)        -- optional
purchase_order_lines(po_line_id PK, po_id FK, product_id FK, qty_ordered, qty_received)           -- optional
```
`stores` and `products` are **shared master data** exposed to Inventory through approved read-only views. Inventory users don't see sales prices, costs or profit.

### 4.2 Generation order
Opening balances (as `ADJUSTMENT` with reason `OPENING`) → daily loop: receive due POs → post `SALE` movements **derived from `sales_lines`** → `RETURN_TO_STOCK` for restockable returns → transfers → occasional damage write-offs and count adjustments → trigger replenishment when on-hand < reorder point → compute snapshots. If stock is insufficient for a generated sale, the **sale is reduced or dropped before writing Sales** (single source of truth; no negative stock).

### 4.3 Tests (automated, part of M1/M2 acceptance)
The seven ledger invariants below (originally specified in §3.2 of the dataset deep-research record, which is archived in the registration package and not included in this repository):

1. `on_hand(p,b,t) = Σ movements(p,b,≤t)`.
2. `on_hand ≥ 0` unless backorders are explicitly modeled (recommend: not modeled).
3. Every `SALE` movement maps 1:1 to a `sales_lines` row (same date, branch, product and quantity).
4. `RETURN_TO_STOCK` ≤ returned qty of the linked sale line and only for `restockable = true`.
5. Each `TRANSFER_OUT` has a matching `TRANSFER_IN` (same qty; in-transit lag explicit).
6. Snapshots equal ledger roll-ups exactly.
7. A threshold is chosen by the validity date, never "latest".

Plus: no product sold in a branch before it was first received there; the snapshot on the as-of date equals the ledger sum.

### 4.4 Link to the Schema Design → Admin → Analytics demo
The designer's brief ("I need to track stock across branches…") goes through the AI proposal, Admin approval and **operator** provisioning of the *approved* tables in an isolated demo schema. The operator then loads the **pre-generated Context A inventory CSVs** through the controlled loader. If the approved design differs from §4.1, the operator uses a documented mapping script; the mapping and its approval are recorded. That keeps "AI proposed it" separate from "humans provisioned and loaded it".

---

## 5. HR: Context A synthetic HR

### 5.1 Minimum schema (recommended)

```text
departments(department_id PK, name_ar, name_en, parent_department_id FK NULL, store_id FK NULL)   -- HQ depts + branch teams
job_titles(job_title_id PK, name_ar, name_en, level)
employees(employee_id PK, employee_code UNIQUE, full_name_ar /* invented */, full_name_en, gender,
          department_id FK, job_title_id FK, manager_id FK NULL, hire_date, termination_date NULL,
          employment_status {ACTIVE, ON_LEAVE, TERMINATED}, employment_type {FULL_TIME, PART_TIME, CONTRACT})
leave_types(leave_type_id PK, code {ANNUAL, SICK, CASUAL, UNPAID, MATERNITY}, name_ar, name_en, counts_working_days BOOL)
leave_requests(leave_request_id PK, employee_id FK, leave_type_id FK, start_date, end_date, requested_at,
               status {PENDING, APPROVED, REJECTED, CANCELLED}, decided_at NULL, decided_by FK NULL,
               working_days NUMERIC /* precomputed with calendar */)
public_holidays(date PK, name_ar)          -- or reuse `calendar`
```
Optional, only if needed: `employment_events` (hire, transfer, termination history) and `leave_balances`.
**Excluded by design:** salary, national ID, phone, address, performance, health details. Restrict even invented names to a column-masked view for `hr_analyst`, so aggregate-first analytics doesn't expose row-level names unless explicitly approved.

### 5.2 Generation
- ~250–400 employees over 24 months; realistic hires and terminations; department sizes tied to branches.
- Names are composed from **separate first-name and family-name lists** combined at random. They are *not* real employee records. State this in the data card.
- Leave: annual, sick and casual mixes; some **overlapping** and cancelled requests; pending requests near the as-of date; requests spanning month boundaries and public holidays (natural ambiguity: "إجازات الشهر ده" — leave this month — means overlap with the month vs started in the month; calendar vs working days).
- **Tests:** end_date ≥ start_date; no approved overlapping leave per employee (or explicitly allowed and documented); `working_days` recomputation matches; no leave for terminated employees after termination.

### 5.3 HR metrics catalog (initial)
Active headcount (as of date) · headcount by department · new hires in period · terminations and turnover rate in period (definition frozen) · approved leave days in period (working days, overlap-prorated) · pending requests count · approval rate. **Not supported (Abstain):** salary, performance, anything payroll.

### 5.4 HR acceptance set (target ~60 typed + 24 voice recordings, 20 test)
Clear (headcount by dept), ambiguous ("مين واخد أجازات أكتر؟" "who took the most leave?": days vs requests; employee vs department), unanswerable ("متوسط المرتبات" "average salaries": salary not in scope → Abstain), and **authorization** (HR user asks for sales revenue → deny; Sales user asks for leave → deny; prompt-injection "تجاهل الصلاحيات" "ignore the permissions" → deny).

---

## 6. Egyptian-Arabic speech: custom recordings plus background benchmark

### 6.1 Roles of each speech resource
| Resource | Role | Use |
|---|---|---|
| **Custom business-question recordings** | **Primary voice evaluation** of H-A (voice vs text delta, ASR-induced decision errors) | Required |
| Casablanca-Egypt **validation** split | ASR model, normalization and biasing selection (together with our dev recordings) | Evaluation only, no redistribution, research-only |
| Casablanca-Egypt **test** split | Background dialect WER, run **once** after the ASR configuration is frozen; reported, never used for selection | Evaluation only, no redistribution, research-only |
| MGB-3 (official source only) | Second background benchmark | Only if official access terms permit |
| ArzEn | Code-switching robustness | Only if access is granted |
| FLEURS `ar_eg` | MSA read-speech control (optional) | Never reported as Egyptian |

**No ASR fine-tuning in the MVP.** Use pretrained ASR zero-shot, with optional vocabulary biasing from the approved catalog (branch, product and metric names). Choose the ASR, normalization and biasing on Casablanca-Egypt **validation** + **our dev recordings only**, freeze the configuration (hash), then run Casablanca-Egypt **test** and our **test** recordings once. Evaluating real Egyptian-Arabic speech remains mandatory.

### 6.2 Recording design (DS-6 approved as corrected)
- **Speakers:** 12 consenting adult native Egyptian-Arabic speakers (spec minimum 10): **4 development + 8 test**, never overlapping. Balance gender; ages 18–60; regions: Greater Cairo, Alexandria, Delta, Upper Egypt (≥2 each where feasible); include some non-students (family members or staff) to avoid a student-only accent and register.
- **Core plan: 192 recordings.**

  | Workspace | Dev | Test | Total |
  |---|---|---|---|
  | Sales | 12 items × 2 dev speakers = 24 | 40 items × 3 test speakers = 120 (2 read + 1 paraphrase per item) | 144 |
  | Inventory | 2 × 2 = 4 | 10 × 2 = 20 | 24 |
  | HR | 2 × 2 = 4 | 10 × 2 = 20 | 24 |
  | **Total** | **32** | **160** | **192** |

  Each dev speaker records 8 utterances; each test speaker records 20 (15 Sales + 5 Inventory/HR), roughly a 15–20 minute session.
  Sales test items: 18 clear, 12 ambiguous (5 metric, 4 time, 3 entity), 6 unanswerable, 2 out-of-scope, 2 authorization/security (scored in the Security suite, §7.4); about 10 are tagged ASR-sensitive (confusable entities or numbers). Inventory and HR test items: 5 clear, 2 ambiguous, 2 unanswerable, 1 authorization each.
- **Optional expansion (+68 → ≈260):** Sales +12 test items × 3 speakers (+36), Inventory +8 × 2 (+16), HR +8 × 2 (+16).
- **Two elicitation modes:**
  - (a) **Read**: the exact benchmark text, for clean pairing.
  - (b) **Intent-prompted paraphrase**: one of the three test recordings of each Sales test item (40 utterances). The speaker sees a *scenario card* ("you want to know which branch sold most last month") and says it their own way. Each paraphrase gets its own manual transcript and is **re-checked** to confirm the intent label still holds; if it doesn't, it is relabeled. Read and paraphrase results are reported separately.
- **Statistical limits:** the unit of analysis is the item (40 Sales test items), with utterances clustered by item and speaker. A ~10% decision-change rate on 120 utterances has a 95% CI of roughly ±5.4 pp without clustering and about ±7 pp with a design effect of 1.5–2, so only large effects are detectable. The primary P2-vs-P4 comparison runs on the typed test split; voice results are a descriptive voice-vs-text delta with clustered CIs. Inventory/HR voice sets are functional acceptance only, and 8 test speakers do not support subgroup (gender or region) claims.
- **Controlled variation:** device (phone mic vs laptop mic), environment (quiet room vs office/café noise, logged), speaking rate (natural). Each utterance stores condition metadata.
- **Content rules:** speakers never say real personal data; numbers, dates and branch/product names come from the benchmark item.

### 6.3 Ethics and consent
- Supervisor/TA approval of the protocol and consent form **before** recording; check whether MIU requires a formal research-ethics review.
- Written informed consent: purpose, voluntary participation, right to withdraw and have recordings deleted, storage location and retention period, who can access the audio, and whether recordings may be shared publicly (**separate opt-in**). No payment coercion; no minors.
- Pseudonymous speaker IDs; the consent forms and the ID↔name key are stored separately and offline. Audio is stored in an access-controlled team drive, **not** a public repo.

### 6.4 Transcription and annotation
- Transcript conventions written first: Egyptian orthography guide (e.g., "عايز", "دلوقتي"), English loanwords in Latin script *or* Arabic (choose one; recommend keeping Latin for code-switched terms and recording both forms), numbers as spoken words in the reference plus a normalized digits field.
- Annotator 1 transcribes; annotator 2 verifies; disagreements are adjudicated. Each transcript is linked to `item_id`, `speaker_id`, `mode`, `device` and `environment`.
- Metrics: WER and CER after a fixed normalization (remove diacritics; unify alef/ya/ta-marbuta; normalize digits), **Entity Error Rate** on catalog entities, and the **decision-change rate** (ANSWER/CLARIFY/ABSTAIN differs from the text condition) and **answer-change rate**.

### 6.5 Leakage prevention
- Splits are by **template family** (all paraphrases and recordings of one underlying question share a split).
- Any component tuned on recordings (e.g., biasing vocabulary, normalization rules) is tuned on **dev speakers only**. The 8 test speakers are held out entirely: the recordings are speaker-disjoint **and** template-family-disjoint between development and test.
- The ASR model, normalization and biasing are frozen (configuration hash) before Casablanca-Egypt test or our test recordings are run.
- Both P2 and P4 consume the **same** ASR transcripts in the voice condition.
- *Translation (23 Oct 2026):* the translation model, prompt and glossary are chosen on dev items only and frozen (configuration hash) together with ASR. Each frozen Arabic input (typed text, or each ASR transcript) is translated **once**, and the cached English output is shared by every pipeline. Human-reviewed English equivalents are evaluation references only and never enter a prompt.

---

## 7. Ambiguity-aware Egyptian-Arabic business-question benchmark

### 7.1 Composition (DS-7 approved as corrected: 400 items = 375 semantic + 25 security)
| Category | Items | Share of 400 | Expected outcome | Gold content |
|---|---|---|---|---|
| Clear answerable | 180 | 45.00% | ANSWER | BIR, question-specific gold SQL, result on S1 and S2 |
| Ambiguous metric (revenue / net sales / gross profit / units) | 50 | 12.50% | CLARIFY | Interpretation set (each with BIR + gold SQL + results), clarification target, scripted user reply → resolved gold |
| Ambiguous time ("الشهر اللي فات" last month, "السنة دي" this year, "الموسم" the season, fiscal vs calendar) | 30 | 7.50% | CLARIFY | As above |
| Ambiguous entity (confusable branches/products, "الفرع الكبير" the big branch) | 30 | 7.50% | CLARIFY | As above |
| Unanswerable: data absent (net profit, stock in Sales workspace, customer age) | 45 | 11.25% | ABSTAIN | Reason code; **no gold SQL** |
| Unanswerable: unsupported analytics (forecast next year, causal "why") | 25 | 6.25% | ABSTAIN | Reason code |
| Out-of-scope / chit-chat | 15 | 3.75% | ABSTAIN | Reason code |
| **Semantic-eligible subtotal (P2-vs-P4)** | **375** | **93.75%** | ANSWER 180 · CLARIFY 110 · ABSTAIN 85 | |
| Authorization / security (Security suite, §7.4) | 25 | 6.25% | DENY at the gate, or a safe scoped Abstain where allowed | Role, workspace, scenario type, expected safe outcome |
| **Total** | **400** | **100%** | | |

- **Every item (all categories, including security cases) also carries a human-reviewed English equivalent** (`question_en_reference`) that preserves the item's ambiguity, or its lack of ambiguity. It is used to evaluate the translation stage (§7.6) and never as system input in the main runs.
- If the catalog policy already resolves a phrase (e.g., "last month" = previous calendar month), the item is authored as **clear**, not ambiguous.
- "ASR-sensitive" is a **tag on voice items** (minimal-pair entities and numbers), not a category of the 400.
- Security cases: 10 gate-level (unauthorized workspace, tampered `workspace_id` or role), 10 cross-department requests inside an authorized workspace, 5 prompt/SQL-injection attempts. All are **test-only**; engineering unit tests are used during development.
- **Splits:** semantic items ≈25% dev (~94) / ≈75% test (~281) by template family, stratified by category (test ≈ ANSWER 135 · CLARIFY 83 · ABSTAIN 63).
- **Gold SQL:** every answerable item gets its own **question-specific** gold SQL instance, because slot values such as branch, period and LIMIT differ within a template family: ≈180 for clear items plus ≥2 interpretations × 110 ambiguous items ≈ **400 instances** from ~120 parameterized templates. Each instance passes (1) an automated BIR-slot ↔ SQL-literal check, (2) review by a second person against **that exact question**, and (3) execution on S1 and S2. A stratified ≥10% sample (≥40) is also recomputed by hand. This far exceeds the university minimum of 50 manually verified queries.
- **Annotation:** all 400 items are labeled by two independent annotators, blind to each other and to P2/P4 outputs. Cohen's κ is reported before adjudication.
- **Independence:** generator author, question authors, gold-label reviewers and the P4 developer are different people wherever practical; any role overlap is recorded as a limitation.

### 7.2 Item record (JSONL, one per item)
```json
{
  "item_id": "SAL-0123", "template_family": "TF-041", "split": "test",
  "workspace": "sales", "role": "sales_analyst", "as_of_date": "2026-06-30",
  "question_ar": "مين أكتر فرع كسبان الشهر اللي فات؟",
  "question_en_reference": "Which branch earned the most last month?",
  "en_preserves_ambiguity": true,
  "code_switch": false, "category": "AMBIGUOUS_METRIC",
  "taxonomy_map": {"practiq": "Ambiguous SELECT Column", "ambrosia": "vagueness"},
  "expected_decision": "CLARIFY",
  "interpretations": [
    {"id": "I1", "bir": {"metric": "net_sales", "dims": ["store"], "time": "2026-05", "rank": 1},
     "sql": "...", "result": {"S1": "...", "S2": "..."}},
    {"id": "I2", "bir": {"metric": "gross_profit"}, "sql": "...", "result": {"S1": "...", "S2": "..."}}
  ],
  "clarification_target": "metric",
  "scripted_user_reply": {"I1": "صافي المبيعات", "I2": "إجمالي الربح"},
  "resolved_gold": "I1",
  "abstain_reason": null,
  "author": "A2", "annotations": {"ann1": "CLARIFY", "ann2": "CLARIFY"}, "adjudicated": true,
  "interpretations_differ_on": ["S1"]
}
```

### 7.3 Annotation procedure
1. **Catalog freeze**: metric definitions, aliases, time policy and as-of date.
2. **Writing**: question writers produce template families; each family has 2–4 natural paraphrases (Egyptian, some code-switched, some Latin "Franco" if it's in scope; decide).
2b. **English equivalent (23 Oct 2026)**: a bilingual annotator writes one English equivalent per item that keeps every ambiguity (e.g., "earned the most", not "most profitable") and keeps catalog entity names as `name_en`. A second bilingual annotator verifies meaning and preserved ambiguity, and disagreements are adjudicated. This adds bilingual work per item; the item counts are unchanged.
3. **Independent labeling**: two annotators label category and expected decision **without seeing each other**. Report agreement (Cohen's κ) before adjudication.
4. **Gold SQL**: written by a third person, executed on S1 and S2, results checked by hand on 10% of items (spreadsheet recomputation).
5. **Ambiguity validation**: every ambiguous item must have ≥2 interpretations that are *each* reasonable under the catalog. Record whether they differ numerically on S1/S2. Ambiguity is defined by meaning, not numbers.
6. **Adjudication log** with rationale for every disagreement.

### 7.4 Fair P2-vs-P4 protocol and metrics (DS-7 approved as corrected)
- **Identical for P2 and P4:** LLM model and version, temperature, authorized views, catalog text, as-of date, snapshot and items, **the same confirmed Arabic input (typed text or the same frozen ASR transcript) and the same cached English translation** (23 Oct 2026), plus the same authorization gate and SQL guard (shared infrastructure, not part of either method). P4's Arabic-anchored BIR and BIR↔SQL consistency check are part of the method under test.
- **Matched clarification:** both P2 and P4 may ask **one** clarification. A deterministic simulated user answers from `scripted_user_reply` when the clarification targets the labeled ambiguity; any other clarification gets the fixed reply "مش فاهم قصدك" ("I don't get what you mean") and counts as a false positive.
- **Prompt-iteration budget:** both methods iterate only on the **dev** split, with the same logged number of iterations. The test split is hashed and frozen before any final run.
- **Metric definitions.** These use semantic-eligible test items `E` only; security cases are excluded.
  - `A*` answerable = clear + ambiguous; `C*` clarification-required = ambiguous; `U*` should-abstain = unanswerable + out-of-scope; `Ans` = items with a delivered final answer.
  - **End-to-end BAA** = answerable items with a correct final answer (after at most one clarification) / |A*|. **Policy-compliant BAA** also counts every unsafe direct answer as a failure.
  - **Unsafe Direct Answer Rate** = items in C* answered directly without the necessary clarification / |C*|. This is recorded as a **policy violation even when the chosen interpretation coincidentally matches the intended answer**. It is reported separately from numerical correctness and is never credited as ambiguity handling.
  - **Clarification precision** = correct clarifications (on C*, with the correct target) / all clarification requests on E. **Recall** = correct clarifications / |C*|. An unnecessary clarification on a clear (or unanswerable) item, or one with the wrong target, is a false positive.
  - **Coverage** = |Ans| / |E|. **Selective accuracy / risk** = correct / incorrect delivered answers ÷ |Ans|. An answer to an unanswerable item is incorrect.
  - **SER_direct** = numerically incorrect direct answers / |E| (the spec's `W_A / N` with N = |E|). **SER_final** = all numerically incorrect delivered answers / |E|.
  - **Abstention** precision and recall over U*, plus the mistaken-abstention rate on A*.
  - Risk–coverage curves use E only. If a method has no threshold to sweep, compare operating points at similar coverage. Execution accuracy and a TrustSQL-style penalty score are secondary views. Use paired tests (McNemar) and bootstrap CIs clustered by template family.
- **Security suite (25 Sales cases + Inventory/HR denial tests), reported separately:**
  - Unauthorized workspace access, or tampered workspace/role claims → **DENY before any LLM invocation** (the audit shows zero model calls).
  - Cross-department questions inside an otherwise authorized workspace → a **safe scoped Abstain or a DENY is acceptable**, provided no restricted metadata reaches the model, no unauthorized SQL executes and no data is disclosed. Not every scenario must produce the same DENY outcome.
  - Prompt/SQL-injection attempts → zero disclosure and a guard block.
  - Metrics: gate-DENY correctness, pre-deny LLM invocations (must be 0), restricted-metadata exposures (0), unauthorized SQL executed (0), and attempted-unauthorized-SQL rate per method (diagnostic).
  - DENY is an authorization-gate outcome, **not a fourth model decision**. The user-facing semantic decisions remain Answer, Clarify and Abstain.

### 7.5 Splits
Dev ~25% / Test ~75% by **template family**. The voice subset mirrors the split. Inventory and HR acceptance sets are **test-only** (not used for tuning) except a 10-item dev slice each.

### 7.6 Translation-stage evaluation (added 23 Oct 2026)
- **References:** the human-reviewed `question_en_reference` of each item. No public Egyptian-Arabic→English business-question corpus was verified, so these references are the translation ground truth.
- **Metrics:** meaning preservation (human judgment on a stratified sample, plus an automatic score such as chrF as secondary), entity preservation on catalog entities, **Ambiguity-Preservation Rate** on clarification-required items and its complement, the **Translation Ambiguity-Collapse Rate**.
- **Conditions:** text (typed benchmark text → translation) and voice (frozen ASR transcript → translation), reported separately, so ASR and translation errors can be attributed.
- **Optional oracle ablation:** P2/P4 given the human English reference instead of the model translation, reported only as an upper-bound diagnostic, never as the main result.
- Full protocol: `docs/EVALUATION_PLAN.md`, Part B.

---

## 8. AI Schema Design: secondary evaluation set

### 8.1 Custom incomplete-brief set (target 30–60 briefs; start at 30)
- **Domains:** ≥ 5 (inventory/stock, HR leave, clinic appointments, library, course registration, small e-commerce, maintenance tickets). Inventory and HR briefs **must not** be copies of Context A's schema text (to avoid self-confirmation in the integrated demo).
- **Degradation protocol** (prevents gold leakage):
  1. Author A writes a **complete reference specification** (actors, workflows, rules).
  2. Author B (different person) designs the **gold design space** from it: *required core* (entities, PK/FK, key cardinalities), *acceptable alternatives* (e.g., lookup table vs enum), *optional* elements, and **must-ask questions**.
  3. Author A writes the **incomplete brief** by deliberately omitting or blurring 2–5 facts. Each omission is labeled `INFERABLE` (a reasonable default exists), `MUST_ASK` (high-impact; the system should ask) or `OUT_OF_SCOPE`.
  4. A reviewer checks that the brief alone doesn't trivially encode the gold structure.
- Briefs in English, with a subset in Egyptian Arabic (text) if Q06 permits.

### 8.2 Metrics (per spec §15.3)
Requirement coverage (explicit requirements satisfied), entity/table F1 and attribute F1 with **semantic matching** (synonym map + reviewer confirmation, not exact strings), PK correctness, FK correctness (source, target, direction), cardinality accuracy (where gold specifies it), **unsupported assumption rate** (invented high-impact requirements), **MUST_ASK recall** (did it ask the critical questions), DDL validity (parse plus a sandbox `CREATE` in a throwaway DB, no data), reviewer effort (edits and minutes to acceptable), and **inter-reviewer agreement** (κ on accept/revise).

### 8.3 Bias control
- S0, S1 and S2 use the same LLM and the same brief.
- Reviewers are **blind to condition** (outputs rendered in a uniform format and shuffled).
- At least one reviewer from outside the schema workstream (TA or another student).
- **The Admin Review demo is not the evaluation:** evaluation scores are computed on proposals *before* any human revision, plus a separate bounded-time revision study if time permits.

### 8.4 External sanity check (optional, permission-gated)
RSchema (`hnuGraph/LLM4DBdesign`): **email the authors** for reuse permission (the repo has no license). If granted, sample 30–50 records and report entity, attribute and PK/FK F1 for S0/S1/S2. Note that RSchema requirements are fully specified, so this checks structure extraction, not incompleteness handling.

---

## 9. Decision status (updated 22 Oct 2026; DS-11 status updated 23 Oct 2026, D-31)

| ID | Decision | Status |
|---|---|---|
| DS-1 | Primary Sales data = Context A custom seeded synthetic Egyptian retail company | **Approved** |
| DS-2 | Online Retail II = optional, separately reported real-data check (Context B); never augmented | **Approved** |
| DS-3 | Contoso V2 = optional replication snapshot (MIT) and design reference | **Approved** |
| DS-4 | Inventory = unified ledger-based synthetic data consistent with Sales | **Approved** |
| DS-5 | HR = synthetic-only (§5.1), with meaningful analytics and access-control tests; no salary or PII | **Approved** |
| DS-6 | Voice = 192 core consented recordings (optional ≈260), speaker- and template-family-disjoint; ASR selection on development data only (Casablanca-Egypt validation + our dev recordings); Casablanca test and our test recordings used once after freeze; no mandatory ASR fine-tuning | **Approved as corrected** |
| DS-7 | Benchmark of 400 items = 375 semantic + 25 security; corrected metric definitions, including unsafe direct answers and a separate Security suite (§7) | **Approved as corrected** |
| DS-8 | Schema secondary set = 30–60 incomplete briefs (degradation protocol), independent condition-blind review, S0/S1/S2 compared before human correction; RSchema only with written permission | **Approved** |
| DS-9 | Synchronize dataset wording: Form Field 5 (concise version), spec §14.2–§14.5, §15.2/§15.4 metrics, references R6/R14, the research guardrails and the provenance plan. *Correction of an earlier draft of this row:* the pre-sync Field 5 did **not** contain the Text2Schema counts, Casablanca or FLEURS; those references were in spec §14 and the guardrails file. | **Executed 22 Oct 2026** (user-authorized) |
| DS-10 | Add the approved diagram and the four research files to the manifest; correct stale diagram-status statements; add changelog entries D-14–D-17 | **Executed 22 Oct 2026** (user-authorized) |
| DS-11 | TA-clarified translation pipeline: human-reviewed English equivalents per item; matched cached translations for P2/P4; translation-stage evaluation; public Text-to-SQL references by stage (Spider, BIRD Mini-Dev, Gretel, AraSpider; Casablanca for ASR) with no merging, no translation into the test set and no fine-tuning (§7, §11) | **Documentation synchronized 23 Oct 2026** (user-authorized final registration sync). The TA replied positively to the dataset evidence (support for the evidence, not approval of the wording). The final Field 4 and Field 5 wording was **student-confirmed final on 23 Oct 2026 (D-30)** |

All approvals above are **team** decisions, not university committee approval.

## 10. Feasibility priorities (proposed order)

1. **P0, before coding:** approve DS-1…DS-8; write the catalog v0 (metrics and conventions); write the consent form; send permission emails (RSchema authors; ArzEn; confirm MGB-3 official terms).
2. **P1:** Context A generator (Sales → Inventory ledger → HR) with invariant tests; freeze seed S1/S2 → load PostgreSQL with read-only views per workspace.
3. **P2:** benchmark writing and double annotation (Sales first), gold SQL; dev/test freeze.
4. **P3:** voice recordings (Sales core subset first), transcription, Casablanca-Egypt validation run for ASR selection; Casablanca-Egypt test run once after the freeze.
5. **P4:** Inventory and HR acceptance sets + authorization suite.
6. **P5:** schema-design brief set and reviewers.
7. **Postponable without hurting the MVP or the primary evaluation:** Online Retail II track, Contoso replication, MGB-3/ArzEn, RSchema subset, BIRD Mini-Dev PostgreSQL check, Spider/Gretel exemplar or sanity runs, paraphrase-mode recordings beyond the core subset.

---

## 11. Public Text-to-SQL references by pipeline stage (DS-11, 23 Oct 2026)

Sources: an independent Text-to-SQL dataset research package (not modified) and the team's independent dataset review, both kept as local research records outside the registration package and this repository. Licenses and sizes were re-checked on the Hugging Face API on 23 Oct 2026 and recorded in the registration package's dataset verification log (23 Oct addendum; not included in this repository); the resulting links and licenses are given in the table below.

| Stage | Dataset | Link | License | Role in this project | Not used for |
|---|---|---|---|---|---|
| English question → SQL | **Spider** | https://huggingface.co/datasets/xlangai/spider | CC BY-SA 4.0 | English-to-SQL reference benchmark; optional generic exemplars | Primary P2-vs-P4 evaluation; training |
| English question → SQL (PostgreSQL) | **BIRD Mini-Dev** | https://huggingface.co/datasets/birdsql/bird_mini_dev | CC BY-SA 4.0 | Reference; **optional** PostgreSQL check of the English-to-SQL component (its `evidence` field resembles our catalog definitions) | Primary evaluation; training |
| English question → SQL (business domains) | **Gretel synthetic_text_to_sql** | https://huggingface.co/datasets/gretelai/synthetic_text_to_sql | Apache 2.0 | Additional English-to-SQL reference (105,851 synthetic pairs, 100 domains incl. retail and HR), recommended by the team's independent review | Translation into Egyptian Arabic (**no commitment** to translate 60,000–89,000 questions); fine-tuning; primary evaluation. Its SQL is generic, not PostgreSQL-specific |
| Arabic ↔ English ↔ SQL | **AraSpider** | https://huggingface.co/datasets/ahmedheakl/araspider | HF repository declares **MIT**; the underlying **Spider** data declares **CC BY-SA 4.0**. Redistribution terms of the derived content are **uncertain**, so it is not treated as covered by only one license | Reference for cross-language alignment in translation-based Text-to-SQL | Egyptian-dialect or business claims (it is MSA, translated Spider) |
| Egyptian-Arabic speech → text | **Casablanca (Egypt)** | https://huggingface.co/datasets/UBC-NLP/Casablanca | CC BY-NC-ND 4.0, research only | ASR model selection (validation) and final background report (test), §6 | Redistribution of modified data; translation (English translations not verified) |
| Ambiguity research | **AMBROSIA**, **AmbiQT** | https://ambrosia-benchmark.github.io/ · https://github.com/testzer0/AmbiQT | see verification logs | Taxonomy and related work | Implementation datasets |
| Optional retail | UCI Online Retail II, Contoso V2 | §3.4–§3.5 | CC BY 4.0 / MIT | Optional, separately reported | Main benchmark |
| **Not confirmed** | AceMB | — | gated | — | Any use until its gated content is independently inspected |

**Rules:** no public dataset is merged with Context A, translated into the test set, or used to train or fine-tune a model. Public English/MSA benchmarks are likely in LLM training data and are not Egyptian business questions, so the primary evaluation stays on the custom benchmark. Any redistributed derivative of Spider or BIRD must stay CC BY-SA 4.0. **AraSpider** carries an MIT declaration on its HF repository but derives from CC BY-SA 4.0 Spider data. Its redistribution terms are uncertain, so the project uses it for reference only and does **not** redistribute it or any derivative of it; if that ever changed, the stricter ShareAlike terms would be assumed and verified first.
<!-- END AMENDED DERIVATIVE source="06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md" -->
