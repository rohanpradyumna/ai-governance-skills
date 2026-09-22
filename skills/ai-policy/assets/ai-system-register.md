# {{Company}} AI System Register

<!-- The inventory every other control depends on. Companion CSV: ai-system-register.csv (same fields; import into a spreadsheet or GRC tool). Include suspected shadow AI with status "Suspected". T3 entries need only the Core fields. -->

| Document control | |
|---|---|
| Owner | {{AI Governance Lead}} — System Owners maintain their rows |
| Update trigger | Before any AI system is used; on any scope change; on decommission |
| Attestation | System Owners confirm rows {{quarterly}}; AI Governance Lead reports register health to the Committee |
| Classification | Confidential |
| Tags | `[NIST GOVERN 1.6, MAP 1.1 · ISO 42001 A.4.2, A.6.2.7, Cl. 8.1 · EU AI Act Art. 6, 49 · IMDA D1]` |

## Field guide

### Core (all tiers)

| Field | Values / guidance |
|---|---|
| `id` | AI-### |
| `name`, `purpose` | Plain description of the use, not the product name alone |
| `status` | Proposed · Pilot · Approved · Suspected (shadow) · Restricted · Decommissioned |
| `system_owner_role`, `technical_owner_role`, `business_unit` | Roles; current holders in {{HR system / annex}} |
| `vendor_or_model`, `hosting_path` | e.g. "Claude via Bedrock", "OpenAI API direct", "self-hosted Llama"; matters for data terms |
| `company_role` | Deployer · Provider · Both (flag substantial modification / rebranding) |
| `data_classes` | Public / Internal / Confidential / Restricted (highest touched) |
| `personal_data`, `special_category_data` | Y/N |
| `users_audience`, `jurisdictions` | Who uses it; where users/affected persons are |
| `risk_score_A_to_G`, `risk_tier` | Per Risk Tiering Standard; tier drives everything below |
| `legal_classification` | EU: Prohibited / High-risk (Annex III item) / Limited (Art. 50) / Minimal / GPAI. US: CCPA ADMT · CO ADMT · IL HB 3773 · NYC AEDT · none |
| `approval_authority`, `approval_date` | Per Schedule A |
| `last_review`, `next_review`, `evidence_location` | |

### Decision & people impact (T1/T2)

`affected_persons` · `decision_type` · `consequential_decision` (Y/N) · `employment_ai_flag` · `human_oversight_role` · `art50_disclosure_trigger` (chatbot / synthetic content / deepfake / emotion-biometric / none) · `disclosure_implemented` · `dpia_ref` · `fria_ref`

### Agent fields (any autonomy ≥ 1)

`autonomy_level` (0–5) · `agent_owner_role` · `agent_operator_role` · `principal` · `tools_integrations` (allowlist ref) · `action_classes` · `limits` · `kill_switch_last_test` · `logging_location` · `log_retention_months` · `last_scope_change`

### Vendor & assurance

`training_optout_confirmed` (how — order form clause, tenant setting screenshot) · `dpa_baa_on_file` · `vendor_tier` (V1/V2/V3) · `risk_assessment_ref` · `evaluation_report_ref` · `notes`

## Register (summary view)

<!-- Keep the full data in the CSV/spreadsheet; this table is the human-readable summary embedded in the policy pack. -->

| ID | System | Owner (role) | Vendor / model | Role | Autonomy | Data | Tier | Legal class | Oversight role | Disclosure | Approval | Next review | Status |
|---|---|---|---|---|---|---|---|---|---|---|---|---|---|
| AI-001 | {{Enterprise chat assistant}} | {{Head of IT}} | {{Vendor X Enterprise}} | Deployer | 0 | Confidential | Elevated | Minimal | User | N/A | {{Gov Lead, date}} | {{date}} | Approved |
| AI-002 | {{Support refund agent}} | {{Head of Support}} | {{Claude via platform Y}} | Deployer | 2 | Confidential | High | Limited (Art. 50) | {{Support Ops Mgr}} | Banner v1 | {{Committee, date}} | {{date}} | Pilot |
| AI-003 | {{Suspected: personal meeting notetaker}} | Unknown | Consumer app | Deployer | 0 | Confidential? | Elevated | — | None | No | — | — | Suspected |
| … | | | | | | | | | | | | | |

## Discovery sources for shadow AI

Expense reports and card statements · SSO/IdP app catalogue and OAuth grants · network/DNS logs for AI domains · browser-extension inventories · SaaS admin consoles (AI features toggled on) · code repos (SDK imports, API keys) · staff survey/amnesty · procurement requests · marketplace/MCP installs. Add findings as `Suspected`, assign an owner within {{10}} working days, then tier.

## Register health metrics (report to Committee)

Total systems by tier and status · % rows attested on time · # Suspected > 30 days · # T1 without current risk assessment · # agents without kill-switch test in {{90}} days · # vendors without training opt-out evidence · # rows with review overdue.
