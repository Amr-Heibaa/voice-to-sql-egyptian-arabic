# Documentation Index — ClearQuery: Ambiguity-Aware Voice-to-SQL in Egyptian Arabic (V3.1)

There is exactly **one canonical document per topic**. Each embeds approved text from the final registration package in a marked block, so its origin can be checked mechanically.

| Document | Topic | Block type |
|---|---|---|
| [SPECIFICATION.md](SPECIFICATION.md) | Full V3.1 specification: scope, modules M1–M10, processing order, SQL safety, Schema Design, hub, requirements, data, evaluation, risks, open decisions. **Source of truth** | Amended derivative (D-31, D-33) |
| [ARCHITECTURE.md](ARCHITECTURE.md) | v6 overview; three-workspace architecture and demonstration contract; RBAC; read-only / Admin governance contract (R1–R5) | Two amended derivatives (D-31) |
| [DATASET_STRATEGY.md](DATASET_STRATEGY.md) | Synthetic company design, benchmark composition, recordings, annotation, schema briefs, public references (DS-1–DS-8, DS-11) | Amended derivative (D-31) |
| [EVALUATION_PLAN.md](EVALUATION_PLAN.md) | Part A: evaluation at a glance (navigation only). Part B: translation pipeline, P2/P4 fairness, leakage, error separation. Normative definitions stay in SPECIFICATION.md §15 and DATASET_STRATEGY.md §6–§8 | Part B verbatim |
| [REGISTRATION_FORM_FIELDS.md](REGISTRATION_FORM_FIELDS.md) | Final text of the six MIU registration-form fields (**NOT SUBMITTED**) | Amended derivative (D-31 outside the boxes; D-33 header line and Field 1 title); Field 2–6 boxes byte-identical |
| [CHANGE_RECORD_D-31.md](CHANGE_RECORD_D-31.md) | Every D-31 correction with reason and exact before/after text | Record |
| [CHANGE_RECORD_D-32.md](CHANGE_RECORD_D-32.md) | Private GitHub repository creation (no content change) | Record |
| [CHANGE_RECORD_D-33.md](CHANGE_RECORD_D-33.md) | TA-approved official title update (D-33), exact before/after text | Record |
| [CHANGE_RECORD_D-34.md](CHANGE_RECORD_D-34.md) | GitHub collaborator status (D-34; no content change) | Record |

**If two documents ever disagree,** SPECIFICATION.md wins for scope and design, [PROJECT_STATUS.md](../PROJECT_STATUS.md) wins for current status, and the conflict must be reported (AGENTS.md §1).

## Provenance

Source package: `MIU_VoiceToSQL_V3_1_FINAL_REGISTRATION_READY_2026-10-23.zip` (ZIP SHA-256 `dafe169e233a582745023331264e92fe20010cff2a7ab3bcbfea2a0c3b4f027b`; internal manifest SHA-256 `a5976cd1e639a2cff3a1e1a45c3e9208b275a411485bf2c0da9cb65d9d858684`; 33/33 files verified on 23 Oct 2026). Package paths are relative to its root folder `MIU_VoiceToSQL_V3_1_Team_Scope_Freeze_2026-10-22/`. **The package was not modified.**

### Block types

- **`BEGIN VERBATIM` … `END VERBATIM`**: byte-identical to the package source; `sha256` is the source hash.
- **`BEGIN AMENDED DERIVATIVE` … `END AMENDED DERIVATIVE`**: package text changed by repository amendments; the `amendment` attribute lists them (`D-31`, or `D-31,D-33`). `source_sha256` is the **original** package hash (kept for provenance); `derivative_sha256` is the hash of the amended text. **An amended block is not byte-identical to its source.** Every change is listed in [CHANGE_RECORD_D-31.md](CHANGE_RECORD_D-31.md) and [CHANGE_RECORD_D-33.md](CHANGE_RECORD_D-33.md).

| Repository location | Package source | Original source SHA-256 | Block type and SHA-256 in this repository |
|---|---|---|---|
| `docs/SPECIFICATION.md` | `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md` | `5116f13cfe3909dcb37cb95cef0301e203ab6fbe45541292c23e6030c1c82fc6` | Amended derivative (D-31, D-33): `ce28cdbff729b1d38bb69ce296efc572f492d406368ed8a507cd666ccc48a1f0` (after D-31 only: `0032b8c945a81857d30c82a2075b97f5ecd90d151ab8bd336321187cdf312743`) |
| `docs/ARCHITECTURE.md` Part A | `03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md` | `78b9b9d456ed6ec251c576e0afc5f8e884a82c2f0e72091a8caec2d1843d043a` | Amended derivative (D-31): `b7e3d2ca37670a5121e7f5635619f3628f2426a60f875b3d596b9fa73678aba8` |
| `docs/ARCHITECTURE.md` Part B | `03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md` | `ce1384180d0a180ed15a03266356ad7c1bb80774ef5cf385ac2841ff7d15a0ba` | Amended derivative (D-31): `aacf664ed7eb2af4d1adb6d4c544e707e0a997f70c291fd6b8b2c71ad6745c9d` |
| `docs/DATASET_STRATEGY.md` | `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md` (+ invariants 1–7 quoted unchanged from `06_RESEARCH_AND_DATA/V3_1_DATASET_DEEP_RESEARCH.md` §3.2, original SHA-256 `2a4d675acd55a8a5189279152f7f5e47bf7bdac1851c3ca7438d755b7001abec`) | `724ac0b92b82ec1ddcfbe93bf596683e6c1481e7104e151112ac3150a62adf05` | Amended derivative (D-31): `a29aa0926496f2823682cf4b2498c70a3505fae270f51dbfc6b3b229af9d8038` |
| `docs/EVALUATION_PLAN.md` Part B | `06_RESEARCH_AND_DATA/V3_1_EVALUATION_NOTES_TRANSLATION_PIPELINE.md` | `08cf6917d1331227b2c21cec34dffe90f436f05fd8297c18901c0520a4621b9c` | **Verbatim** (unchanged) |
| `docs/EVALUATION_PLAN.md` Part A | — | — | Written for this repository; summary only, no new decisions |
| `docs/REGISTRATION_FORM_FIELDS.md` | `FINAL_FORM_COPY_PASTE.md` (final export folder; generated unchanged from the package form draft) | `157d641e856a4602f2f717f306865c1eb8fef2fb773f6a7fe9a362c20a36f804` | Amended derivative (D-31: two lines outside the field boxes; D-33: header line and Field 1 title): `9a5eb9b44459c1330baff9b3a3eb698f263f7d2e03a9a56148f06f9edb28233f` (after D-31 only: `ec89264912b95773804fb366c83ef207db33b50fb5e59826f3fc8aa91e379a61`). **Field boxes 2–6 byte-identical**; Field 1 = TA-approved title (D-33) |
| `README.md` Abstract | Form Field 2 | `00a3a29930ee0382c511fd59cb7df89b76ecb5e13dabe75386546ed9ab80bba0` (text without its final newline; same value as changelog D-26) | **Verbatim** |
| `assets/System-Overview-3840x2160-v6.png` | `03_ARCHITECTURE_AND_FIGMA/System-Overview-3840x2160-v6.png` | `62d3743e297e5eba7c0ea0e062643c7f756291777911942b73e1e2bddd280653` | **Byte-identical** copy (3840 × 2160 PNG, 688,043 bytes) |

### How to verify

- **Any block:** extract the lines strictly between its `BEGIN` and `END` markers and hash them. A `VERBATIM` block must equal its `sha256`; an `AMENDED DERIVATIVE` block must equal its `derivative_sha256`. Example (Git Bash):

  ```bash
  sed -n '/^<!-- BEGIN AMENDED DERIVATIVE source="02_CURRENT/,/^<!-- END AMENDED DERIVATIVE/p' docs/SPECIFICATION.md | sed '1d;$d' | sha256sum
  ```

- **Amended derivatives against the package:** applying the before → after replacements in [CHANGE_RECORD_D-31.md](CHANGE_RECORD_D-31.md), and then for `D-31,D-33` blocks those in [CHANGE_RECORD_D-33.md](CHANGE_RECORD_D-33.md), to the original package file must reproduce the block exactly.
- `.gitattributes` forces LF line endings so these hashes survive checkout on Windows.

## Package path map

After D-31, every package path inside the canonical documents is either re-pointed to a repository file or explicitly labelled as part of the registration package and not included in this repository. Summary:

| Package path | In this repository |
|---|---|
| `02_CURRENT_SPECIFICATION/VOICE_TO_SQL_V3_1_TEAM_APPROVED_SPEC.md` | [docs/SPECIFICATION.md](SPECIFICATION.md) |
| `03_ARCHITECTURE_AND_FIGMA/ARCHITECTURE_V3_1.md` | [docs/ARCHITECTURE.md](ARCHITECTURE.md), Part A |
| `03_ARCHITECTURE_AND_FIGMA/READ_ONLY_AND_ADMIN_GOVERNANCE_CONTRACT.md` | [docs/ARCHITECTURE.md](ARCHITECTURE.md), Part B |
| `03_ARCHITECTURE_AND_FIGMA/System-Overview-3840x2160-v6.png` | [assets/System-Overview-3840x2160-v6.png](../assets/System-Overview-3840x2160-v6.png) |
| `06_RESEARCH_AND_DATA/V3_1_PROPOSED_DATASET_STRATEGY.md` | [docs/DATASET_STRATEGY.md](DATASET_STRATEGY.md) |
| `06_RESEARCH_AND_DATA/V3_1_EVALUATION_NOTES_TRANSLATION_PIPELINE.md` | [docs/EVALUATION_PLAN.md](EVALUATION_PLAN.md), Part B |
| `04_FORM_PREPARATION_NOT_SUBMITTED/` (form draft, checklist, readiness report) | Final field text in [docs/REGISTRATION_FORM_FIELDS.md](REGISTRATION_FORM_FIELDS.md); live status in [PROJECT_STATUS.md](../PROJECT_STATUS.md) |
| `02_CURRENT_SPECIFICATION/V3_TO_V3_1_DECISION_CHANGELOG.md` | Condensed in [PROJECT_EVOLUTION.md](../PROJECT_EVOLUTION.md#5-decision-index) |
| `00_START_HERE/` (README_FIRST, manifest, verification report) | Replaced by the root [README.md](../README.md), this provenance section and [PROJECT_STATUS.md](../PROJECT_STATUS.md) |
| `05_TEAM_AI_ONBOARDING/` | Replaced by [AGENTS.md](../AGENTS.md) and [CLAUDE.md](../CLAUDE.md) |
| `07_DELIVERY_PLAN/IMPLEMENTATION_ROADMAP.md` | Covered by SPECIFICATION.md §20; next steps in PROJECT_STATUS.md |
| `06_RESEARCH_AND_DATA/` research records (verification log, deep research, shortlist, provenance plan, novelty guardrails) | **Not included** (registration package only). The conclusions the project relies on are in SPECIFICATION.md §14.5, §16 and §24 and DATASET_STRATEGY.md §11; the ledger invariants are inlined in DATASET_STRATEGY.md §4.3 |
| `03_ARCHITECTURE_AND_FIGMA/` Figma Make prompt, adaptation notes, style-reference image | **Not included** (historical inputs to v6; the reference image depicts a different project) |
| `01_READ_ONLY_V2_BASELINE/`, `01B_READ_ONLY_V3_DRAFT_BASELINE/` | **Not included** (historical archives; summarized in [PROJECT_EVOLUTION.md](../PROJECT_EVOLUTION.md)) |
| Independent Text-to-SQL research folder and team dataset review (local research records) | **Not included**; outside both the package and this repository |
