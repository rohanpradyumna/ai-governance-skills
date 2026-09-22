# Data, privacy and IP rules for AI use

**Read this when:** drafting the data-handling section of the AUP, the Data & Privacy for AI standard, retention/logging clauses, DPIA/FRIA sections, or IP rules for AI-generated work.

---

## 1. Data classification × AI tool permission matrix

Reuse the company's existing classification labels if they exist (map them to the four below). Put this matrix in the AUP — it is the single most-used rule.

| Class | Examples | Consumer / personal AI accounts | Approved enterprise AI tools (no-training, DPA, SSO) | Approved AI inside contracted SaaS (CRM/helpdesk AI) | Self-hosted / VPC models | Agents (autonomous) |
|---|---|---|---|---|---|---|
| **Public** | Published content, marketing, open-source code | ✔ | ✔ | ✔ | ✔ | ✔ |
| **Internal** | Non-sensitive internal docs, general business data | ✘ | ✔ | ✔ | ✔ | ✔ (allowlisted stores) |
| **Confidential** | Customer data (non-sensitive PII), contracts, financials, source code, product plans, employee data | ✘ | ✔ only tools approved *for Confidential* | ✔ if in the system that already holds the data | ✔ | ✔ with data allowlist, T2+ controls |
| **Restricted** | Special-category personal data (health, biometrics, protected traits, children), payment card data, credentials/secrets, privileged legal material, trade secrets, M&A, export-controlled, regulated data (HIPAA/GLBA/PCI) | ✘ | ✘ unless specifically approved per tool *and* per use with Legal/Privacy sign-off (BAA where PHI) | Only within the regulated system's own approved AI features | ✔ with T1 controls | ✘ by default; exception via committee |

Notes to include:
- "Approved" means listed in the Approved AI Tools register with the classification it is approved for. Anything not listed is treated as a consumer tool.
- Pasting, uploading, connecting via API, granting a plugin/connector access, and letting an agent read a store are all "entering data into a tool".
- Anonymisation/pseudonymisation may lower the class only if the Privacy Lead has approved the method.
- Secrets (API keys, passwords, tokens) never go into any prompt, including approved tools.

## 2. Vendor terms that change the class a tool can handle

Minimum for "Confidential"-approved tools: no training on customer inputs/outputs (contractual, not just a toggle); data processing agreement with sub-processor list; retention of prompts/outputs disclosed and configurable (zero-data-retention or ≤ 30 days abuse-monitoring preferred); enterprise SSO and admin controls; region/residency options where required; security attestation (SOC 2 Type II / ISO 27001); breach notification ≤ 72 h; deletion on termination. See `vendor-and-procurement.md`.

## 3. Personal data in AI systems

| Requirement | Detail | Tags |
|---|---|---|
| Lawful basis per use | Each AI use processing personal data has a documented basis (GDPR Art. 6/9; UK GDPR; PDPA; state privacy laws). Consumer-facing profiling and employee monitoring need particular care; legitimate-interest assessments documented. | GDPR 5, 6, 9 · ISO A.7.3 |
| Purpose limitation & minimisation | Don't feed more data than the task needs; agents get field-level, not table-level, access; no repurposing customer data for model training without basis and notice. | GDPR 5(1)(b),(c) |
| Transparency | Privacy notices describe AI processing, automated decisions, logic and consequences; CCPA ADMT pre-use notice; employee notices for workplace AI. | GDPR 13/14 · CCPA ADMT · IL HB 3773 |
| Automated decisions | No solely automated decision with legal/similarly significant effect without: legal basis (contract/consent/law), human intervention route, right to contest and explanation; *SCHUFA*: a score that materially influences counts. CCPA ADMT opt-out; CO SB 26-189 adverse-outcome disclosure and human review (2027). | GDPR 22 · CCPA · CO |
| DPIA | Required for high-risk processing — practically all T1 and most T2 systems with personal data. Use the risk assessment template's DPIA section; combine with FRIA where Art. 27 applies. | GDPR 35 · AI Act 26(9), 27(4) |
| Data-subject rights | DSARs cover data held in AI systems, logs, vector stores and vendor retention; design for retrieval and deletion; agent memory must be purgeable. | GDPR 15–17 · ISO A.6.2.8 |
| International transfers | US-hosted models processing EU data need a transfer mechanism (DPF certification, SCCs) and, for Restricted data, residency options. | GDPR Ch. V |
| Children & vulnerable persons | Higher bar; age-appropriate design; no profiling of minors for ads; companion-chatbot rules (CA SB 243). | Various |
| Employee monitoring | AI analysis of employee communications, productivity or sentiment requires HR + Legal + works-council review; emotion recognition at work is prohibited (EU); monitoring policy cross-referenced. | AI Act Art. 5 · national labour law |
| Biometrics | BIPA-style consent, retention schedule, and legal review before any biometric AI. | BIPA · GDPR 9 |

## 4. Prompts, outputs and logs are records

| Rule | Why |
|---|---|
| Treat prompts, uploaded files, agent traces and outputs as **company records** subject to the retention schedule, legal hold, eDiscovery and DSARs. | They are discoverable; they contain the data classes above. |
| Define retention per tier: T3 tool defaults; T2 action logs ≥ {{6}} months; T1 full logs & traces ≥ {{12}} months (EU Art. 26(6) minimum 6 months; financial-sector rules may require 5–7 years). | Balance evidence needs vs. minimisation. |
| Redact Restricted data in logs while preserving enough for reconstruction (hashes, references). | Logging can itself breach the matrix. |
| Privileged material: legal teams use only tools approved for Restricted with privilege-preserving terms; label prompts; avoid sharing outputs beyond privilege circle. | Waiver risk. |
| Vendor retention documented in the register (zero-retention / 30-day / indefinite). | Needed for DSARs and breach scoping. |

## 5. Intellectual property

| Topic | Rule to write |
|---|---|
| **Inputs** | Only use data/content the company has rights to use for the purpose (licences, terms of service, TDM opt-outs, third-party confidentiality). No uploading third-party copyrighted works beyond licence. |
| **Outputs — ownership** | Vendor terms must assign output rights to the company. Purely AI-generated material may not be copyrightable (US Copyright Office 2025; similar elsewhere): for deliverables where IP matters (brand assets, code, publications), document **substantial human authorship** (edits, selection, arrangement) and keep the working record. |
| **Outputs — infringement** | Review generated code (licence contamination, copied snippets — use provenance/reference filters where available), images and text for third-party IP before external use; vendor IP indemnity preferred for T2+. |
| **Trade secrets** | Entering a trade secret into a tool that trains on inputs or lacks confidentiality terms can destroy secret status. Restricted class rules apply. |
| **Client / customer contracts** | Check contractual AI clauses (no-AI, disclosure, data-use limits) before using client data or delivering AI-assisted work; disclose where required. |
| **Attribution** | Internal convention for marking AI-assisted artefacts (commits, documents) so reviewers apply appropriate scrutiny; external attribution where law or contract requires (Art. 50). |
| **Training / fine-tuning on company or customer data** | Requires: contractual right, privacy review, data-minimisation, documented dataset provenance (ISO A.7.5), and register entry as a provider-side activity. |

## 6. DPIA vs FRIA vs AI risk assessment

| | AI risk assessment (this skill) | DPIA (GDPR Art. 35) | FRIA (AI Act Art. 27) |
|---|---|---|---|
| Trigger | Every T1/T2 system | High-risk personal-data processing | Deployers in Art. 27 scope using Annex III high-risk systems (⚠ 2027-12-02) |
| Focus | All harms: people, company, security, legal | Data-protection risks to individuals | Fundamental rights of affected persons/groups |
| Content overlap | Purpose, data, affected persons, risks, mitigations, oversight | Necessity/proportionality, risks, measures | Process description, period/frequency, affected categories, specific risks, oversight, complaint mechanism |
| Output | Tier confirmation, control plan, approval | Consultation with DPA if residual high risk | Notification to market surveillance authority (template) |

Practical rule: one assessment document with modular sections (`assets/ai-risk-assessment.md`) — the DPIA and FRIA sections are completed when triggered; each names its legal owner.

## 7. Clause seeds

- "Personnel shall enter Confidential or Restricted information only into AI tools listed in the Approved AI Tools register for that classification. Consumer or personal AI accounts shall not be used for Company work involving Internal, Confidential or Restricted information." `[NIST MAP 4.1 · ISO 42001 A.7.2, A.9.2 · GDPR Art. 5, 28]`
- "No AI system shall make a decision producing legal or similarly significant effects on a person without meaningful human review, a route for the person to contest the decision, and an explanation of the principal reasons and data used." `[NIST MANAGE 4.1 · ISO 42001 A.9.2 · GDPR Art. 22 · CCPA ADMT · CO SB 26-189]`
- "Prompts, uploaded content, agent action logs and outputs are Company records. They shall be retained per Schedule {{X}} (minimum six months for High-tier systems used in the EU) and are subject to legal hold." `[NIST MEASURE 2.4 · ISO 42001 A.6.2.8 · EU AI Act Art. 26(6)]`
- "Substantial human authorship shall be documented for AI-assisted deliverables in which the Company or its clients require intellectual-property protection." `[NIST MAP 4.1 · ISO 42001 A.10.3]`
