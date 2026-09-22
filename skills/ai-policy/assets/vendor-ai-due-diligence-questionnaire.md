# AI Vendor Due Diligence Questionnaire — {{Vendor / product}}

<!-- Send to the vendor (or complete from their documentation) before approving any external AI tool, model, API, plugin, MCP server, marketplace agent, or AI feature in existing SaaS. Vendor tier V1 = all sections; V2 = all sections, lighter evidence; V3 = Section A + B + E only. Built from references/vendor-and-procurement.md. Remove guidance comments. -->

| | |
|---|---|
| Requesting System Owner (role) | {{…}} · Register ID: {{AI-###}} |
| Proposed vendor tier | V1 Critical / V2 Significant / V3 Standard |
| Intended use, data classes, autonomy level | {{…}} |
| Reviewer roles | Procurement · Security · Privacy · Legal · AI Governance Lead |
| Tags | `[NIST GOVERN 6.1–6.2, MAP 4.1–4.2, MANAGE 3.1–3.2 · ISO 42001 A.10.2–A.10.3 · EU AI Act Art. 25, 53 · OWASP ASI04]` |

Answer format: **Yes / No / Partial** + evidence (document name, clause, URL, screenshot). "Roadmap" answers count as **No**.

## A. Company and regulatory posture

| # | Question | Answer | Evidence |
|---|---|---|---|
| A1 | Legal entity, ownership, headquarters, data-centre regions | | |
| A2 | Under the EU AI Act, are you a provider of an AI system, a GPAI model provider, or infrastructure only? Any high-risk classification of this product? | | |
| A3 | Do you provide the downstream documentation required of GPAI providers (Art. 53) or instructions for use (Art. 13) where applicable? | | |
| A4 | Certifications and attestations: SOC 2 Type II, ISO/IEC 27001, ISO/IEC 42001, HITRUST, FedRAMP, other — with dates and scope | | |
| A5 | Cyber / tech E&O insurance in place? Limits? | | |
| A6 | Any regulatory actions, material breaches or AI-related incidents in the last 3 years? | | |

## B. Data use, retention and privacy

| # | Question | Answer | Evidence |
|---|---|---|---|
| B1 | Are customer inputs, outputs, embeddings or fine-tunes used to train or improve your or any third party's models? Default setting and contractual position for our plan | | |
| B2 | Retention period for prompts, outputs, files, logs; zero-data-retention option; configurable by tenant? | | |
| B3 | Do humans (yours or sub-processors') review customer content, e.g. for abuse monitoring? Under what conditions and notice? | | |
| B4 | Sub-processors incl. underlying model providers; change-notice process | | |
| B5 | Hosting regions and residency options; cross-border transfer mechanisms (DPF, SCCs) | | |
| B6 | Data Processing Agreement offered? BAA for PHI? Standard clauses accepted? | | |
| B7 | Deletion on termination and on request; deletion certificate; support for data-subject requests incl. data in logs and memory | | |
| B8 | Tenant isolation architecture for prompts, memory/vector stores, fine-tunes | | |
| B9 | Encryption in transit and at rest; key management; customer-managed keys? | | |

## C. Security

| # | Question | Answer | Evidence |
|---|---|---|---|
| C1 | SSO (SAML/OIDC), SCIM, role-based admin controls, tenant-wide policy settings (e.g. disable training, restrict features) | | |
| C2 | Audit logs available to customer: what events, export/API, retention | | |
| C3 | Penetration testing cadence; latest summary; bug-bounty / vulnerability disclosure | | |
| C4 | AI-specific security testing: prompt injection (direct and indirect), jailbreak, data exfiltration, tool misuse — methods and results | | |
| C5 | Supply chain: how models, plugins, tools and MCP servers you ship are vetted, pinned and updated | | |
| C6 | Incident notification SLA to customers; contacts; cooperation commitments | | |
| C7 | Secure development lifecycle; segregation of environments; secrets management | | |

## D. Model and performance

| # | Question | Answer | Evidence |
|---|---|---|---|
| D1 | Models used (names, versions, first-party or third-party), hosting path; can we pin versions? | | |
| D2 | Advance notice of model changes, deprecations, default-setting changes, new features (days)? Opt-out or delay option? | | |
| D3 | Evaluation results relevant to our use: accuracy, robustness, safety, bias — datasets, metrics, dates; known limitations | | |
| D4 | Model documentation (model card / system card / instructions for use) | | |
| D5 | Customer-configurable guardrails: system prompts, content filters, output validation, refusal settings | | |
| D6 | Content provenance and marking of generated outputs (metadata, watermark, C2PA) for EU AI Act Art. 50(2) and equivalents | | |
| D7 | Explainability features sufficient for adverse-action reasons / individual explanations | | |
| D8 | Support for customer bias audits (e.g. NYC LL 144): data exports, methodology cooperation | | |

## E. Agent capabilities (complete if the product can take actions)

| # | Question | Answer | Evidence |
|---|---|---|---|
| E1 | What actions can the agent take? Which are on by default? | | |
| E2 | Can we restrict tools, connectors, methods and parameters via allowlists? Enforced server-side? | | |
| E3 | Per-agent identity and credentials; on-behalf-of propagation; no shared accounts | | |
| E4 | Human approval gates configurable by action type and threshold; approval logging | | |
| E5 | Quantitative limits (spend, actions, messages, runtime); hard stop on breach | | |
| E6 | Kill switch available to the customer without vendor involvement; time to halt | | |
| E7 | Complete action logs (tool, parameters, target, result, approver) exportable in near real time | | |
| E8 | Memory: scope, tenant isolation, purge on request, review of persistent writes | | |
| E9 | Inter-agent communication: authentication, validation, delegation controls | | |
| E10 | Prompt-injection defences for content the agent retrieves (email, web, documents, tool outputs); test evidence | | |
| E11 | Disclosure features: AI identity and principal shown to end users; configurable text | | |
| E12 | Liability position for actions taken outside configured scope | | |

## F. Fairness, transparency and responsible AI

| # | Question | Answer | Evidence |
|---|---|---|---|
| F1 | Responsible AI policy / governance program; alignment to NIST AI RMF or ISO/IEC 42001 | | |
| F2 | Bias testing methodology and cadence for people-affecting features | | |
| F3 | Training-data provenance statement; copyright policy (Art. 53(1)(c)) | | |
| F4 | End-user disclosure capabilities (AI interaction notice) | | |

## G. Intellectual property

| # | Question | Answer | Evidence |
|---|---|---|---|
| G1 | Ownership / licence of outputs to customer | | |
| G2 | IP indemnity for third-party claims arising from outputs and from your training data; scope and caps | | |
| G3 | Restrictions on our use of outputs beyond law | | |

## H. Continuity and exit

| # | Question | Answer | Evidence |
|---|---|---|---|
| H1 | Uptime SLA and credits; status page; DR/BCP summary | | |
| H2 | Export of prompts, outputs, fine-tunes, embeddings, configurations; transition assistance | | |
| H3 | Financial stability indicators (funding, profitability, customer concentration) | | |

## Reviewer assessment

| Area | Rating (Pass / Conditional / Fail) | Conditions / contract clauses required | Reviewer |
|---|---|---|---|
| A Regulatory | | | Legal |
| B Data & privacy | | | Privacy |
| C Security | | | Security |
| D Model | | | Technical Owner |
| E Agent | | | Security + AI Governance Lead |
| F Responsible AI | | | AI Governance Lead |
| G IP | | | Legal |
| H Continuity | | | Procurement |

**Approved classification ceiling**: Public / Internal / Confidential / Restricted (with exception ref) · **Vendor tier**: V1/V2/V3 · **Approved uses / prohibited uses**: {{…}} · **Contract clauses to secure** (from `vendor-and-procurement.md` §3): {{list}} · **Review date**: {{…}} · **Decision & approver (role, date)**: {{…}}
