# {{Company}} Artificial Intelligence Governance Policy

<!-- Master policy (ISO/IEC 42001 Cl. 5.2). Target ≤ 6 pages. Measurable requirements live in the Standards; keep this to intent, scope, principles, prohibited uses, roles, mandatory outcomes, enforcement. Remove all guidance comments before delivery. -->

| Document control | |
|---|---|
| Owner | {{AI Governance Lead — role}} |
| Executive sponsor | {{role}} |
| Approver | {{Board / CEO / Executive Committee}} |
| Version | {{1.0}} |
| Effective date | {{YYYY-MM-DD}} |
| Review cadence | Annual, and on material change in law, AI use, or organisation |
| Classification | Internal |
| Related documents | AI Acceptable Use Standard · AI Agent Standard · AI Risk Tiering Standard (Schedule A) · AI System Register · AI Risk Assessment Procedure · AI Incident Response Runbook · {{Information Security Policy}} · {{Privacy Policy}} · {{Code of Conduct}} · {{Vendor Management Policy}} · {{Records Retention Schedule}} |

## 1. Purpose

{{Company}} uses artificial intelligence to {{one sentence on business intent}}. This Policy sets how the Company governs the acquisition, development, deployment, use and retirement of AI systems — including AI models, generative AI tools, and AI agents that take actions — so that AI use is lawful, safe, secure, fair, transparent, and accountable to a named human. `[NIST GOVERN 1.2 · ISO 42001 Cl. 5.2, A.2.2]`

## 2. Scope

2.1 This Policy applies to all employees, officers, contractors, temporary staff and third parties acting on the Company's behalf ("Personnel"), in all locations. `[ISO 42001 Cl. 4.3]`

2.2 It applies to every **AI system** the Company develops, procures, deploys, operates or uses, including: AI features embedded in licensed software; AI assistants and chatbots; coding, writing and meeting assistants; models accessed via API; internally developed or fine-tuned models; **AI agents** and LLM-driven automations; and AI provided to customers {{if provider}}. Personal or consumer AI accounts used for Company work are in scope.

2.3 Where the Company acts as a **provider** of AI systems, Schedule {{C}} adds provider obligations. <!-- delete if deployer only -->

2.4 This Policy supplements, and does not replace, the {{Information Security Policy}}, {{Privacy Policy}}, {{Code of Conduct}} and applicable law. Where requirements conflict, the stricter applies. `[ISO 42001 A.2.3]`

## 3. Definitions

<!-- Single source of definitions; Standards reference this section. -->

| Term | Meaning |
|---|---|
| **AI system** | A machine-based system that, for explicit or implicit objectives, infers from inputs how to generate outputs such as predictions, content, recommendations or decisions that can influence physical or virtual environments. Includes generative AI. |
| **Generative AI** | AI that produces text, code, images, audio, video or other content. |
| **AI agent** | An AI system that pursues a goal by planning and executing actions — calling tools, APIs or systems, reading or writing data, or communicating with people or other agents — with limited or no step-by-step human direction. |
| **Autonomy level** | The 0–5 scale in the AI Agent Standard describing how independently an agent acts. |
| **Consequential decision** | A decision that produces legal or similarly significant effects on a person, including decisions about employment, compensation, credit, insurance, housing, education, healthcare, benefits, or legal status. |
| **Deployer** | The Company when it uses an AI system under its own authority. **Provider**: the Company when it develops an AI system or model and places it on the market or puts it into service under its own name. |
| **Human oversight** | Review, approval or override of AI outputs or actions by a person with the competence, information, authority, time and accountability to do so meaningfully. |
| **AI incident** | An event in which an AI system's output or action causes, or could plausibly have caused, harm to a person, the Company, or a third party; violates this Policy or law; or operates outside its approved scope. |
| **Risk tier** | Prohibited, High, Elevated or Standard, per Schedule A. |
| **System Owner** | The role accountable for a specific AI system under §6. |
| **shall / should / may** | Mandatory / expected unless a documented exception is approved / permitted. |
| **Public / Internal / Confidential / Restricted** | As defined in the {{Data Classification Standard}}. |

## 4. Principles

<!-- Keep to one line each; every principle must map to a control in §7 or a Standard. -->

The Company commits to AI that is: **(a) Lawful and accountable** — a named human role owns every AI system and its outcomes; **(b) Safe, secure and reliable** — tested before use and monitored in use; **(c) Fair** — tested for harmful bias where it affects people; **(d) Transparent** — people know when they interact with AI and how consequential decisions are made; **(e) Privacy-preserving** — data minimised, protected, and used only for approved purposes; **(f) Human-centred** — humans retain meaningful control over consequential decisions and over agents' actions; **(g) Proportionate** — governance effort scales with risk tier. `[NIST GOVERN 1.2 · ISO 42001 A.6.1.2, A.9.3 · OECD AI Principles]`

## 5. Prohibited uses

5.1 Personnel shall not develop, procure or use AI to: <!-- trim/extend from references/risk-tiering.md §4 -->
(a) manipulate or deceive people in ways that cause harm, or exploit vulnerabilities of age, disability or circumstance;
(b) score or profile people in ways leading to detrimental treatment unrelated to the context in which data was collected;
(c) infer emotions or protected characteristics of employees, candidates or students, or perform biometric identification, except where lawful and approved in writing by Legal;
(d) generate sexual deepfakes, non-consensual intimate imagery, child sexual abuse material, or content inciting self-harm, violence or crime;
(e) discriminate, or intentionally produce discriminatory effects, on the basis of protected characteristics;
(f) make consequential decisions about people without human oversight meeting §7.6;
(g) impersonate a human where disclosure is required, or present AI output as human-authored to customers, regulators, courts or the public where that would mislead;
(h) enter Confidential or Restricted information into any AI tool not approved for that classification, or any secret or credential into any AI tool;
(i) operate agents at autonomy level 5, agents that modify their own instructions, tools or permissions, agents that alter identities or access rights, or agents that delete or alter audit logs;
(j) make or communicate legal, regulatory, financial or contractual commitments on the Company's behalf without human sign-off;
(k) circumvent safety features, usage limits or controls of AI tools or of the Company's enforcement mechanisms.
`[EU AI Act Art. 5 · TX TRAIGA · IL BIPA · NIST GOVERN 1.1 · ISO 42001 A.9.2]`

5.2 Items (a)–(e) reflect legal prohibitions and cannot be excepted. Items (f)–(k) may be excepted only by the AI Governance Committee with Legal concurrence under §9.3.

## 6. Governance and roles

<!-- Scale using references/governance-operating-model.md. Roles, not names. -->

6.1 The **{{Board / Audit & Risk Committee}}** approves this Policy and the Company's AI risk appetite and receives an AI governance report at least {{annually}}. `[NIST GOVERN 2.3 · ISO 42001 Cl. 5.1]`

6.2 The **Executive Sponsor** ({{role}}) is accountable for this Policy, its resourcing and its reporting.

6.3 The **AI Governance Committee** ("the Committee"), chartered separately, approves Standards, approves High-tier systems and agents, decides exceptions, oversees incidents and monitors the register. It includes representatives of Legal/Privacy, Security, Data/AI, HR, Risk/Compliance and business units using AI. `[NIST GOVERN 1.4, 2.1 · ISO 42001 Cl. 5.3]`

6.4 The **AI Governance Lead** ({{role}}) operates the program: maintains the AI System Register, runs intake and tiering, approves Elevated-tier systems, coordinates assessments, training and monitoring, and maintains this Policy and the Standards.

6.5 Each AI system has a **System Owner** (an employee at {{manager}} level or above) accountable for its tiering, risk assessment, controls, monitoring, register accuracy and decommissioning; a **Technical Owner** for performance, security and change control; and, for agents, an **Agent Owner** and **Agent Operator** per the AI Agent Standard. `[NIST GOVERN 2.1, 3.2 · ISO 42001 A.3.2]`

6.6 **Legal/Compliance** maintains the register of applicable AI laws and reviews it at least every {{six}} months; **Privacy** owns DPIAs/FRIAs; **Security** owns AI threat modelling, agent identity and logging; **HR** owns employment-AI rules, worker notifications and training rollout; **Procurement** owns vendor due diligence. `[NIST GOVERN 1.1, 6.1]`

6.7 **Internal Audit** (or an external assessor) independently assesses this program at least every {{two years}} and reports to the {{Audit Committee}}, not to the AI Governance Lead. `[ISO 42001 Cl. 9.2 · NIST MEASURE 1.3]`

6.8 All Personnel shall follow the AI Acceptable Use Standard, complete required training, and report AI incidents and concerns through {{channel}}; reports made in good faith are protected from retaliation. `[ISO 42001 A.3.3 · NIST GOVERN 4.3]`

## 7. Mandatory requirements

<!-- Each clause: requirement · owner · evidence · tag. Detail sits in the named Standard. -->

7.1 **Inventory.** Every AI system shall be recorded in the AI System Register before use, including suspected unapproved ("shadow") use, with its purpose, System Owner, data classes, autonomy level, risk tier, legal classification and evidence locations. *Owner:* System Owners; register maintained by AI Governance Lead. *Evidence:* register; {{quarterly}} attestation. `[NIST GOVERN 1.6 · ISO 42001 A.4.2, A.6.2.7 · EU AI Act Art. 49 where applicable]`

7.2 **Risk tiering.** Every AI system shall be assigned a risk tier under Schedule A before use and re-assessed on any scope change and at least {{annually}}. Systems meeting a legal high-risk or automated-decision classification shall be tiered High regardless of score. *Owner:* System Owner; validated by AI Governance Lead. *Evidence:* tiering record. `[NIST GOVERN 1.3, MAP 1.5 · ISO 42001 Cl. 6.1.2, A.5.2 · EU AI Act Art. 6]`

7.3 **Risk and impact assessment.** High- and Elevated-tier systems shall complete the AI Risk Assessment (including DPIA and, where required, FRIA sections) and receive approval from the authority in Schedule A before deployment. Residual risks shall be documented and accepted by the approving authority. *Evidence:* signed assessment. `[NIST MAP 1–5, MANAGE 1.4 · ISO 42001 Cl. 6.1.4, A.5.2–A.5.5 · GDPR Art. 35 · EU AI Act Art. 27 where applicable]`

7.4 **Approved tools and data.** Personnel shall use only AI tools listed in the Approved AI Tools Register, within the data classification ceiling listed for each, per the AI Acceptable Use Standard. Approved tools shall be provided through Company-managed accounts with single sign-on, contractual exclusion of training on Company data, and a data processing agreement. Unapproved tools shall be blocked or monitored by technical controls. *Owner:* AI Governance Lead (list), Security (enforcement). `[NIST MAP 4.1, GOVERN 6.1 · ISO 42001 A.7.2, A.9.2, A.10.3 · GDPR Art. 28]`

7.5 **Testing before use.** High-tier systems shall be evaluated for accuracy, robustness, security (including prompt-injection and tool-misuse testing for generative and agentic systems) and — where they affect people — harmful bias, against documented acceptance criteria, before deployment and after material change; Elevated-tier systems shall be evaluated proportionately. *Owner:* Technical Owner. *Evidence:* evaluation report. `[NIST MEASURE 2.1–2.11 · ISO 42001 A.6.2.4 · EU AI Act Art. 9, 10, 15 (providers) · OWASP LLM/ASI]`

7.6 **Human oversight.** No consequential decision shall be made solely by an AI system. Each High-tier system shall have a designated Human Oversight Role with the competence, information, authority and time to review and override outputs, and affected persons shall have a route to contest decisions and receive the principal reasons. *Owner:* System Owner. `[NIST GOVERN 3.2, MAP 3.5, MANAGE 4.1 · ISO 42001 A.9.2 · EU AI Act Art. 14, 26(2) · GDPR Art. 22 · CCPA ADMT · CO SB 26-189]`

7.7 **AI agents.** Any AI system that takes actions shall comply with the AI Agent Standard, including a unique identity per agent, least privilege and least agency, enumerated tool and data allowlists, action-class approval gates, quantitative limits, a tested kill switch owned by a named role, complete action logging, treatment of external content as untrusted, disclosure of AI status and principal to people it interacts with, and re-approval on any scope change. *Owner:* Agent Owner. `[IMDA MGF D1–D4 · OWASP ASI01–10 · NIST MANAGE 2.4 · ISO 42001 A.6.2.6, A.6.2.8 · EU AI Act Art. 50(1)]`

7.8 **Transparency.** People interacting with Company AI shall be informed that they are interacting with AI and, for agents, on whose behalf the agent acts. AI-generated content published or sent externally shall be identifiable as AI-generated where law or contract requires, and public communications drafted with AI shall receive human editorial sign-off. Employees and candidates shall be notified where AI materially influences decisions about them, as required by law. *Owner:* System Owner; HR for workforce notices. `[EU AI Act Art. 50 · Utah AI Policy Act · NYC LL 144 · IL HB 3773 · CCPA ADMT · NIST MEASURE 2.8 · ISO 42001 A.8.2, A.8.5]`

7.9 **Data and privacy.** AI use shall comply with the {{Privacy Policy}} and the data rules in the AI Acceptable Use Standard: lawful basis for personal data; data minimisation and field-level access for agents; no training or fine-tuning on customer or personal data without contractual right and Privacy approval; prompts, outputs and agent logs treated as Company records under the {{Records Retention Schedule}} with retention of at least {{six}} months for High-tier systems (twelve months default), subject to legal hold. *Owner:* Privacy Lead; System Owners. `[GDPR Art. 5, 6, 22, 35 · EU AI Act Art. 26(6) · NIST MEASURE 2.10 · ISO 42001 A.7, A.6.2.8]`

7.10 **Security.** AI systems shall be included in the {{Information Security Policy}} scope, with AI-specific threat modelling (OWASP LLM and Agentic Top 10), secure handling of prompts and secrets, sandboxed code execution, and tamper-evident logging. *Owner:* Security Lead. `[NIST MEASURE 2.7 · ISO 42001 A.6.1.3 · EU AI Act Art. 15 (providers)]`

7.11 **Third parties.** AI vendors, models, plugins and agents shall pass due diligence proportionate to tier before use, with contracts covering data use and training exclusion, retention, security, model-change notice, agent controls, transparency documentation, IP and incident cooperation, and shall be reviewed at least every {{one / two}} years. Vendor AI features switched on inside existing software are new AI systems under §7.1. *Owner:* Procurement; System Owner. `[NIST GOVERN 6.1–6.2, MANAGE 3.1–3.2 · ISO 42001 A.10.2, A.10.3 · EU AI Act Art. 25]`

7.12 **Monitoring and change.** High-tier systems shall be monitored continuously against defined performance, drift, fairness and security thresholds with alerting; Elevated-tier systems periodically. Any scope change — model, instructions, tools, data, autonomy, users, jurisdiction — shall trigger re-tiering and re-approval under Schedule A. Vendor-initiated model changes shall be tracked and evaluated. *Owner:* Technical Owner; System Owner. `[NIST MEASURE 2.4, MANAGE 4.1 · ISO 42001 A.6.2.6 · EU AI Act Art. 26(5), 72]`

7.13 **Incidents.** AI incidents shall be reported immediately through {{channel}} and handled under the AI Incident Response Runbook: halt or contain the system, preserve logs, assess harm and notification duties (data-protection authorities, market surveillance authorities, customers, individuals), remediate, and feed lessons into this Policy and the Standards. *Owner:* Security Lead (response); Legal (notifications). `[NIST GOVERN 4.3, MANAGE 4.3 · ISO 42001 A.8.4, Cl. 10.2 · EU AI Act Art. 26(5), 73 · GDPR Art. 33]`

7.14 **AI literacy and training.** All Personnel shall complete AI literacy training within {{30}} days of joining and annually; Personnel in Human Oversight, System Owner, Technical Owner, Agent Owner/Operator and approval roles shall complete role-specific training before assuming the role. Records shall be retained. *Owner:* HR; AI Governance Lead. `[EU AI Act Art. 4, 26(2) · NIST GOVERN 2.2 · ISO 42001 Cl. 7.2, 7.3, A.4.6]`

7.15 **Decommissioning.** Retired AI systems shall have access revoked, data and memory disposed of per retention rules, dependants notified and the register updated. *Owner:* System Owner. `[NIST GOVERN 1.7, MANAGE 2.4 · ISO 42001 A.6.2.6]`

7.16 **Legal and regulatory review.** Legal shall review applicable AI laws and standards at least every {{six}} months and on material change in the Company's AI use, jurisdictions or customers, and the AI Governance Lead shall update this Policy and the Standards accordingly. `[NIST GOVERN 1.1, 1.5 · ISO 42001 A.2.4, Cl. 10]`

## 8. Employment-related AI

<!-- Delete if no employment AI now or planned; otherwise keep — every company hires. -->

8.1 AI used in recruiting, selection, compensation, performance, promotion, scheduling, discipline, termination or monitoring is tiered High. Before use it shall be tested for disparate impact using a documented method, candidates and employees shall receive the notices required by applicable law (including {{NYC LL 144 ten-business-day notice and annual independent bias audit; Illinois HB 3773 notice; California CCPA ADMT pre-use notice and opt-out; Colorado SB 26-189 notice and adverse-outcome disclosure from 2027-01-01; EU worker-representative notification}}), selection data shall be retained for at least {{four}} years, and adverse decisions shall be reviewed by a human with authority to change them. Emotion recognition and covert AI monitoring of employees are prohibited. *Owner:* HR. `[EEOC Title VII/ADA · EU AI Act Annex III(4), Art. 26(7) · CA FEHA ADS regs · NIST MEASURE 2.11]`

## 9. Compliance, exceptions and enforcement

9.1 Compliance is monitored through the register, monitoring metrics, internal audit and the Committee's standing agenda; the Executive Sponsor reports to the {{Board}} at least {{annually}} on the metrics in the Committee Charter. `[NIST GOVERN 1.5 · ISO 42001 Cl. 9.1, 9.3]`

9.2 Violations are handled under the {{Disciplinary Policy}} and contractor terms. Deliberate entry of Restricted data into unapproved tools, circumvention of controls, or operation of an unapproved agent constitutes serious misconduct.

9.3 **Exceptions** to §5.1(f)–(k) or to any Standard require a written request stating business need, risk and compensating controls; approval by the AI Governance Lead (Elevated/Standard) or the Committee with Legal concurrence (High/prohibited-by-policy); an expiry of no more than {{twelve}} months; and recording in the exceptions register. Legal prohibitions cannot be excepted.

9.4 This Policy is enforced through technical controls including {{single sign-on gating of approved tools, blocking or monitoring of unapproved AI services, data-loss prevention on prompts, tenant-level training opt-outs, an agent gateway enforcing allowlists and caps, and centralised logging}}.

## Schedule A — Risk tiers, approval authority and required controls

<!-- Paste the tier definitions and tier → controls matrix from references/risk-tiering.md §1 and §5, adjusted to the company. -->

| Tier | Definition | Approver | Review |
|---|---|---|---|
| Prohibited | §5 | — | — |
| High | {{…}} | AI Governance Committee | Quarterly monitoring; annual re-assessment |
| Elevated | {{…}} | AI Governance Lead + System Owner's executive | Semi-annual |
| Standard | {{…}} | System Owner (registered) | Annual attestation |

{{Tier → controls matrix}}

## Schedule B — Applicable laws and standards

<!-- From references/regulatory-landscape.md for the intake jurisdictions. Mark ⚠ items "verify before adoption". -->

| Regime | Applies because | Key obligations reflected in | Status / verify |
|---|---|---|---|
| NIST AI RMF 1.0; ISO/IEC 42001:2023 | Framework baseline | Whole policy | Voluntary |
| {{EU AI Act Art. 4, 50 (in force); Art. 26/27 (⚠ 2027-12-02)}} | {{EU users/staff}} | §7.6–7.9, 7.14 | ⚠ |
| {{…}} | | | |

## Schedule C — Provider obligations <!-- delete if deployer only -->

{{Technical documentation, instructions for use, QMS, conformity assessment and EU database registration for high-risk systems; post-market monitoring and serious-incident reporting (Art. 72–73); downstream information (Art. 13/53); content-marking capability (Art. 50(2)); customer terms on acceptable use and oversight (ISO A.10.4).}}

## Schedule D — Statement of Applicability (ISO/IEC 42001 Annex A) <!-- Comprehensive depth only -->

| Control | Applicable | Justification if not | Implemented in | Status |
|---|---|---|---|---|
| A.2.2 AI policy | Y | | This Policy | Implemented |
| {{… all 38 …}} | | | | |

## Revision history

| Version | Date | Author (role) | Change |
|---|---|---|---|
| {{1.0}} | {{date}} | {{AI Governance Lead}} | Initial issue |
