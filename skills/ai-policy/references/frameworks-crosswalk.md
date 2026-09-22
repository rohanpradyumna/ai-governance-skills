# Frameworks crosswalk

**Read this when:** tagging clauses, building the coverage matrix (SKILL.md step 6), mapping an existing policy to frameworks, or producing an ISO/IEC 42001 Statement-of-Applicability appendix.

Organised by **policy section** so each drafted section can be tagged directly. IDs: NIST AI RMF 1.0 subcategories (`GOVERN 1.1` …), ISO/IEC 42001:2023 Annex A controls (`A.2.2` …) and clauses (`Cl. 5.2`), EU AI Act articles, IMDA Agentic Framework dimensions (`D1` bound risks · `D2` human accountability · `D3` technical controls & processes · `D4` end-user responsibility), OWASP Agentic (`ASI0x`) and LLM (`LLM0x`) Top 10.

Tag format in documents: `[NIST GOVERN 1.1 · ISO 42001 A.2.2 · EU AI Act Art. 4]`. Omit frameworks that don't apply; never invent an ID that isn't in this file.

---

## 1. Full ID lists (for reference)

### NIST AI RMF 1.0 subcategories

| Function / category | Subcategories (short) |
|---|---|
| **GOVERN 1** Policies & processes | 1.1 legal/regulatory requirements understood & documented · 1.2 trustworthiness characteristics integrated into policies · 1.3 risk-based level of risk management determined · 1.4 transparent risk management policies/procedures · 1.5 ongoing monitoring & periodic review of the risk process · 1.6 **AI system inventory** resourced by risk priority · 1.7 decommissioning/phase-out processes |
| **GOVERN 2** Accountability | 2.1 roles, responsibilities, communication lines documented · 2.2 personnel & partners trained in AI risk management · 2.3 executive leadership accountable |
| **GOVERN 3** Workforce | 3.1 diverse team informs decisions · 3.2 roles for human-AI configuration & oversight defined |
| **GOVERN 4** Culture | 4.1 safety-first, critical-thinking practices · 4.2 risks & impacts documented and communicated · 4.3 testing, incident identification, information sharing |
| **GOVERN 5** Engagement | 5.1 feedback from external stakeholders collected · 5.2 feedback incorporated |
| **GOVERN 6** Third parties | 6.1 third-party risk policies incl. IP · 6.2 contingency for third-party failure/incident |
| **MAP 1** Context | 1.1 purpose, context, assumptions documented · 1.2 interdisciplinary team · 1.3 mission/goals · 1.4 business value · 1.5 risk tolerances · 1.6 socio-technical requirements |
| **MAP 2** Categorisation | 2.1 tasks & methods defined · 2.2 knowledge limits & human oversight documented · 2.3 scientific integrity / TEVV |
| **MAP 3** Capabilities & scope | 3.1 benefits · 3.2 costs · 3.3 application scope · 3.4 operator proficiency · 3.5 human oversight processes |
| **MAP 4** Component risks | 4.1 legal risks incl. third-party IP · 4.2 internal controls for third-party components |
| **MAP 5** Impacts | 5.1 likelihood & magnitude of impacts · 5.2 engagement with affected communities |
| **MEASURE 1** Methods | 1.1 metrics selected · 1.2 metrics appropriateness · 1.3 internal experts / independent assessors |
| **MEASURE 2** Evaluation | 2.1 test sets & metrics documented · 2.2 human-subject evaluation · 2.3 performance in deployment-like conditions · 2.4 production monitoring · 2.5 valid & reliable · 2.6 safety · 2.7 security & resilience · 2.8 transparency & accountability · 2.9 explainability · 2.10 privacy · 2.11 fairness & bias · 2.12 environmental · 2.13 TEVV effectiveness |
| **MEASURE 3** Tracking | 3.1 emergent risks · 3.2 hard-to-assess risks tracked · 3.3 end-user feedback |
| **MEASURE 4** Feedback | 4.1 measurement tied to deployment context · 4.2 results inform decisions · 4.3 measurable improvement |
| **MANAGE 1** Prioritise & respond | 1.1 purpose achievement determined · 1.2 treatment prioritised · 1.3 responses to high-priority risks · 1.4 residual risk documented |
| **MANAGE 2** Benefit/impact | 2.1 resources · 2.2 sustain value · 2.3 unknown-risk response · 2.4 **supersede/disengage/deactivate** mechanisms |
| **MANAGE 3** Third parties | 3.1 third-party resources monitored · 3.2 pre-trained models monitored |
| **MANAGE 4** Treatments monitored | 4.1 post-deployment monitoring, appeal, decommissioning, change management · 4.2 continual improvement · 4.3 incidents communicated |

### ISO/IEC 42001:2023 — clauses and Annex A controls (38)

Clauses: 4 context · 5 leadership (5.2 **AI policy**, 5.3 roles) · 6 planning (6.1.2 risk assessment, 6.1.3 risk treatment + **Statement of Applicability**, 6.1.4 impact assessment, 6.2 objectives) · 7 support (7.2 competence, 7.3 awareness, 7.4 communication, 7.5 documented information) · 8 operation · 9 performance evaluation (9.1 monitoring, 9.2 **internal audit**, 9.3 management review) · 10 improvement (10.1 continual improvement, 10.2 nonconformity & corrective action).

| Objective | Controls |
|---|---|
| **A.2** Policies related to AI | A.2.2 AI policy · A.2.3 alignment with other organisational policies · A.2.4 review of the AI policy |
| **A.3** Internal organisation | A.3.2 AI roles & responsibilities · A.3.3 reporting of concerns |
| **A.4** Resources | A.4.2 resource documentation · A.4.3 data resources · A.4.4 tooling resources · A.4.5 system & computing resources · A.4.6 human resources |
| **A.5** Impact assessment | A.5.2 impact assessment process · A.5.3 documentation of assessments · A.5.4 impact on individuals/groups · A.5.5 societal impacts |
| **A.6** Lifecycle | A.6.1.2 objectives for responsible development · A.6.1.3 processes for responsible design & development · A.6.2.2 requirements & specification · A.6.2.3 design & development documentation · A.6.2.4 verification & validation · A.6.2.5 deployment · A.6.2.6 operation & monitoring · A.6.2.7 technical documentation · A.6.2.8 **event logs** |
| **A.7** Data | A.7.2 data for development & enhancement · A.7.3 acquisition · A.7.4 quality · A.7.5 provenance · A.7.6 preparation |
| **A.8** Information for interested parties | A.8.2 system documentation & user information · A.8.3 external reporting · A.8.4 communication of incidents · A.8.5 information for interested parties |
| **A.9** Use | A.9.2 processes for responsible use · A.9.3 objectives for responsible use · A.9.4 intended use |
| **A.10** Third parties & customers | A.10.2 allocating responsibilities · A.10.3 suppliers · A.10.4 customers |

---

## 2. Crosswalk by policy section

### 2.1 Purpose, scope, principles, definitions

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Top-management-approved AI policy, aligned with other policies, reviewed periodically | GOVERN 1.2, 1.4, 1.5 | Cl. 5.2; A.2.2, A.2.3, A.2.4 | — | — | — |
| Principles (trustworthiness characteristics) | GOVERN 1.2 | Cl. 5.2 (b) objectives; A.6.1.2, A.9.3 | Recital 27 (ethics guidelines) | D2 | — |
| Legal & regulatory register; jurisdiction review | GOVERN 1.1 | Cl. 4.2 interested parties; A.2.4 | Art. 4 (literacy of context) | — | — |
| Definitions (AI system, agent, autonomy, high-impact decision…) | MAP 1.1 | Cl. 3 terms | Art. 3 | D1 | — |

### 2.2 Governance, roles, accountability

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Executive accountability; board/committee oversight | GOVERN 2.3 | Cl. 5.1, 5.3 | Art. 26 (deployer as legal person) | D2 | — |
| Governance committee charter, decision rights, cadence | GOVERN 1.4, 2.1 | Cl. 5.3, 9.3 | — | D2 | — |
| RACI: system owner, model owner, agent owner/operator, oversight roles | GOVERN 2.1, 3.2 | A.3.2 | Art. 26(2) competent oversight persons | D2 | ASI03 |
| Independent assurance (internal audit / second line) | MEASURE 1.3 | Cl. 9.2 | Art. 17 QMS (providers) | — | — |
| Reporting concerns / whistleblowing | GOVERN 4.3 | A.3.3 | Art. 87 (reporting infringements) | D4 | — |
| Culture, safety-first, documentation of risks | GOVERN 4.1, 4.2 | Cl. 7.3 awareness | — | — | — |

### 2.3 AI system inventory / register

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Inventory of all AI systems incl. shadow AI, resourced by risk | **GOVERN 1.6** | Cl. 8.1; A.4.2, A.6.2.7 | Art. 49 (EU database, high-risk); Art. 26(8) | D1 | ASI04 (dynamic tools inventory) |
| Register fields: purpose, owner, data, autonomy, tier, legal class, evidence location | MAP 1.1, 2.1, 3.3 | A.4.2–A.4.5, A.9.4 | Art. 6, Annex III | D1 | — |
| Decommissioning recorded | GOVERN 1.7 | A.6.2.6 | — | — | — |

### 2.4 Risk tiering and assessment

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Risk-based tiering; risk tolerance | GOVERN 1.3; MAP 1.5 | Cl. 6.1.2 | Art. 6 classification | D1 | — |
| Per-system risk / impact assessment before use | MAP 1–5; MEASURE 1 | Cl. 6.1.4; A.5.2–A.5.5 (+ ISO/IEC 42005) | Art. 9 (providers); Art. 27 FRIA (deployers in scope); GDPR Art. 35 DPIA | D1 | — |
| Impacts on individuals, groups, society | MAP 5.1, 5.2 | A.5.4, A.5.5 | Art. 27 | D1 | — |
| Risk treatment & residual risk acceptance | MANAGE 1.2–1.4 | Cl. 6.1.3; SoA | Art. 9(5) | D1 | — |
| Re-assessment on change / cadence | GOVERN 1.5; MANAGE 4.1 | Cl. 8.1, 9.1 | Art. 27(2), Art. 25 substantial modification | D1 | ASI04 |

### 2.5 Data, privacy and IP

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Data classification × tool permission matrix | MAP 4.1 | A.7.2–A.7.6; A.4.3 | Art. 10 (providers) | D1 | LLM02 sensitive info disclosure |
| Personal data lawful basis; DPIA; data-subject rights incl. automated decisions | MEASURE 2.10 | A.7.3 | GDPR Art. 5, 6, 13/14, 22, 35; AI Act Art. 26(9) | — | — |
| Training-use restrictions & retention in vendor terms | GOVERN 6.1; MANAGE 3.1 | A.10.3 | Art. 53 (GPAI copyright) | — | LLM02, LLM04 poisoning |
| Prompts/outputs as records: retention, eDiscovery, privilege | GOVERN 1.4 | Cl. 7.5; A.6.2.8 | Art. 12, 26(6) logs | D3 | — |
| Data quality & provenance | MEASURE 2.5 | A.7.4, A.7.5 | Art. 10 | — | ASI06 |
| IP: rights in inputs/outputs, human authorship, third-party IP | MAP 4.1; GOVERN 6.1 | A.10.3 | Art. 53(1)(c),(d) GPAI | — | — |

### 2.6 Human oversight and decision rights

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Human oversight design per tier; meaningful-oversight test | GOVERN 3.2; MAP 2.2, 3.5 | A.9.2, A.6.2.2 | Art. 14 (providers), Art. 26(2) (deployers) | D2 | ASI09 |
| No solely automated consequential decisions without review/appeal | MANAGE 4.1 (appeal) | A.9.2 | GDPR Art. 22; CCPA ADMT; CO SB 26-189 | D2 | — |
| Automation-bias countermeasures | GOVERN 4.1 | A.4.6 | Art. 14(4)(b) | D2 (May 2026) | ASI09 |
| Ability to override, halt, deactivate | **MANAGE 2.4** | A.6.2.6 | Art. 14(4)(e) | D3 | ASI10 |

### 2.7 Transparency and disclosure

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Tell people they interact with AI; principal disclosed for agents | MEASURE 2.8 | A.8.2, A.8.5 | **Art. 50(1)** + 2026 guidelines | D4 | ASI09 |
| Mark synthetic content; label deepfakes; public-interest text | MEASURE 2.8 | A.8.2 | **Art. 50(2), 50(4)**; CA SB 942; China labelling; KR AI Basic Act | — | — |
| Notice to affected persons / employees of AI-driven decisions | MAP 5.2 | A.8.5 | Art. 26(7), 26(11); NYC LL144; IL HB 3773; CCPA ADMT; CO SB 26-189 | D4 | — |
| Explainability sufficient for reasons/adverse-action notices | MEASURE 2.9 | A.8.2 | Art. 13, 86 (right to explanation); ECOA/Reg B | — | — |
| External reporting & public statements about AI | GOVERN 5.1 | A.8.3 | — | — | — |

### 2.8 Security

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| AI-specific threat model; secure development | MEASURE 2.7 | A.6.1.3; ISO 27001 cross-ref | Art. 15 | D3 | LLM01–10, ASI01–10 |
| Prompt-injection & untrusted-content handling | MEASURE 2.7 | A.6.2.4 | Art. 15(5) | D3 | **ASI01**, LLM01 |
| Identity & least privilege for agents/tools | GOVERN 1.3; MANAGE 1.3 | A.3.2, A.9.2 | — | D3 | **ASI03** |
| Tool/plugin/MCP supply chain | MAP 4.2; MANAGE 3.1 | A.10.3 | Art. 25 (value chain) | D3 | **ASI04**, LLM03 |
| Sandboxing / code execution controls | MEASURE 2.6 | A.6.2.5 | — | D3 | **ASI05** |
| Memory/RAG integrity | MEASURE 2.7 | A.7.4, A.7.5 | Art. 10 | D3 | **ASI06**, LLM08 |
| Inter-agent auth & message validation | MEASURE 2.7 | A.6.2.2 | — | D3 | **ASI07** |
| Caps, rate limits, blast-radius limits | MANAGE 2.3 | A.6.2.6 | — | D1 | **ASI08**, LLM10 |
| Red-teaming / adversarial testing before release | MEASURE 2.6, 2.7 | A.6.2.4 | Art. 55 (GPAI systemic); Art. 15 | D3 | all |

### 2.9 Lifecycle, change control, monitoring

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Pre-deployment approval by tier | MAP 1–3; MANAGE 1.1 | A.6.2.5 | Art. 26(1), 43 conformity (providers) | D1 | — |
| Verification & validation; acceptance criteria; bias testing | MEASURE 2.1–2.13 | A.6.2.4 | Art. 9(6)–(8), 10(2)(f), 15 | D3 | — |
| Production monitoring, drift, performance thresholds | MEASURE 2.4, 3.1; MANAGE 4.1 | A.6.2.6 | Art. 26(5), 72 post-market monitoring | D3 | ASI08 |
| Event logging & retention | MEASURE 2.4 | **A.6.2.8** | Art. 12, **26(6)** ≥ 6 months | D3 | ASI10 |
| Change management; scope change = re-approval; vendor model updates | MANAGE 4.1 | A.6.2.6 | Art. 25 (substantial modification) | D1 | ASI04 |
| Decommissioning | GOVERN 1.7; MANAGE 2.4 | A.6.2.6 | — | — | — |
| Technical documentation | — | A.6.2.3, A.6.2.7 | Art. 11, Annex IV | — | — |

### 2.10 Third parties, procurement, customers

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Vendor due diligence; contract clauses; monitoring | GOVERN 6.1, 6.2; MANAGE 3.1, 3.2 | **A.10.2, A.10.3** | Art. 25 (value-chain responsibilities); DORA (finance) | D1 (third-party agents, May 2026) | ASI04 |
| Pre-trained / foundation model risks | MAP 4.1, 4.2; MANAGE 3.2 | A.10.3 | Art. 53 (GPAI info to downstream) | — | LLM03 |
| Customer-facing obligations (if provider): documentation, instructions, incident comms | GOVERN 5.1 | **A.10.4**, A.8.2, A.8.4 | Art. 13, 16, 73 | D4 | — |
| Contingency for vendor failure | GOVERN 6.2 | A.10.3 | — | — | ASI08 |

### 2.11 Incidents and continual improvement

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| AI incident definition, reporting channel, severity | GOVERN 4.3; MANAGE 4.3 | A.3.3, A.8.4 | Art. 3(49) serious incident; Art. 73 (providers), 26(5) (deployers) | D3 | ASI10 |
| Response: halt, contain, preserve logs, notify | MANAGE 2.4, 4.3 | A.6.2.6, A.8.4 | Art. 73 timelines (15 days; 2 days widespread; 10 days death); GDPR 72h breach | D3 | ASI08 |
| Lessons learned → policy/standard update | MANAGE 4.2 | Cl. 10.1, 10.2 | — | — | — |
| Management review; internal audit | GOVERN 1.5 | Cl. 9.2, 9.3 | — | — | — |

### 2.12 Training and literacy

| Element | NIST | ISO 42001 | EU AI Act | IMDA | OWASP |
|---|---|---|---|---|---|
| Role-based AI literacy for all staff using AI | GOVERN 2.2 | Cl. 7.2, 7.3; A.4.6 | **Art. 4** | D2, D4 | ASI09 |
| Enhanced training for oversight roles, developers, approvers | GOVERN 2.2, 3.2 | A.4.6 | Art. 26(2) competence | D2 | — |
| Training records | GOVERN 2.2 | Cl. 7.2(d), 7.5 | Art. 4 (best-extent evidence) | — | — |

---

## 3. Statement of Applicability skeleton (Comprehensive depth)

For ISO-ready output, append to the governance policy:

| Annex A control | Applicable (Y/N) | Justification if N | Implemented in (document § / system) | Status |
|---|---|---|---|---|
| A.2.2 AI policy | Y | | Governance Policy §1–3 | Implemented |
| … all 38 … | | | | |

Rule: every "N" needs a reason tied to scope (e.g. "A.7.2 not applicable — Company does not develop or train models"); every "Y" points at a clause or artefact that exists.

## 4. Coverage matrix format (all depths)

| Framework requirement | Document | Clause / section | Status | Note |
|---|---|---|---|---|
| NIST GOVERN 1.6 inventory | ai-system-register.md | whole | Met | |
| EU AI Act Art. 50(1) | ai-agent-standard.md | §7.1 | Met | banner text in assets |
| ISO 42001 A.3.3 reporting of concerns | ai-governance-policy.md | §9.2 | Partial | needs anonymous channel — handoff |

Status values: **Met · Partial · Planned · N/A** (N/A requires reason). Rows come from the sections triggered at intake: all of §2.1–2.4, 2.6, 2.9, 2.11, 2.12 always; §2.5 when any personal/confidential data; §2.7 when any external-facing AI; §2.8 when any GenAI or agent; §2.10 when any third-party AI (nearly always).
