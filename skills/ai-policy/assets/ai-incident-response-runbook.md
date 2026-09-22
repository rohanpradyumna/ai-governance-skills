# {{Company}} AI Incident Response Runbook

<!-- Procedure layer. Plugs into the existing incident response plan; states only what is different for AI. Remove guidance comments. -->

| | |
|---|---|
| Owner | {{Security Lead}} · Co-owners: {{AI Governance Lead}}, {{Legal}} |
| Approver | {{AI Governance Committee}} |
| Version / effective | {{1.0}} / {{YYYY-MM-DD}} · Review: annual and after every Sev-1/2 AI incident |
| Parent | AI Governance Policy §7.13 · {{Incident Response Plan}} · {{Data Breach Procedure}} |
| Tags | `[NIST GOVERN 4.3, MANAGE 2.4, 4.3 · ISO 42001 A.3.3, A.8.4, Cl. 10.2 · EU AI Act Art. 26(5), 73 · GDPR Art. 33–34]` |

## 1. What counts as an AI incident

Any event in which an AI system's output or action **causes or could plausibly have caused harm** to a person, the Company or a third party; **violates** the AI Governance Policy, a Standard or law; or **operates outside its approved scope**. Includes near-misses. Examples:

| Category | Examples |
|---|---|
| Data | Restricted/Confidential data entered into an unapproved tool; personal data exposed in outputs; vendor retention or training discovered contrary to contract; memory/RAG store leaks across tenants |
| Output harm | Materially wrong output relied on (financial, legal, medical, safety); discriminatory outcome; defamatory, harassing or infringing content published; deepfake or unlabelled synthetic content released |
| Agent action | Action outside allowlist or principal's authority; limit or cap breach; irreversible action without required approval; harmful external communication; runaway cost; kill-switch failure; sub-agent escalation |
| Security | Successful prompt injection (direct or via retrieved content); credential misuse by or via an agent; poisoned knowledge base; malicious tool/MCP server; model or prompt exfiltration |
| Governance | Unregistered (shadow) AI in production; use of a prohibited practice; missing legally required notice/disclosure; vendor model change causing regression |
| Legal / regulatory | Complaint from an affected person or regulator; "serious incident" under EU AI Act Art. 3(49) (death/serious harm to health, serious disruption of critical infrastructure, infringement of fundamental-rights obligations, serious harm to property/environment) |

## 2. Severity

| Sev | Criteria | Response lead | Halt? | Committee / exec notified |
|---|---|---|---|---|
| **1 Critical** | Harm to people, safety, or fundamental rights; Restricted data exposed; regulatory "serious incident"; agent acting irreversibly outside scope at scale; public/customer-facing harm | {{Security Lead}} + {{Legal}} | Immediately | Within 1 hour |
| **2 High** | Confidential data exposed; consequential decision affected; cap breach with financial loss; injection with access to tools; unlabelled synthetic content externally | {{Security Lead}} | Immediately (High tier) / within 1 h | Within 4 hours |
| **3 Medium** | Policy violation without confirmed harm; shadow AI with Confidential data; agent anomaly caught by auto-halt; vendor regression | {{AI Governance Lead}} | Case-by-case | Next Committee meeting |
| **4 Low** | Near-miss; Internal data in unapproved tool; minor disclosure gap | {{System Owner}} | No | Monthly report |

## 3. Reporting

- Anyone: report immediately via {{incident channel / email / hotline}}. Include what happened, which system (register ID if known), data or people involved, what you did. Good-faith reports are protected. `[ISO A.3.3]`
- Automated: auto-halt, limit-breach and anomaly alerts from {{agent gateway / SIEM}} open a ticket automatically.
- Vendors: contractually required to notify within {{24/72}} h; Procurement forwards to {{incident channel}}.
- Affected persons/customers: complaints routed from {{support / privacy inbox}}.

## 4. Response steps

### Step 1 — Triage (≤ {{1 h}} for Sev 1–2)
Assign severity; open incident record; identify system(s) and register entry; identify System/Agent Owner; assemble responders (Security, AI Governance Lead, System Owner, Technical Owner, Privacy if personal data, Legal if Sev 1–2, HR if employee-related, Comms if external).

### Step 2 — Halt and contain
- Agents: activate kill switch; revoke or rotate the agent's credentials; disable tool allowlist entries; freeze memory writes; stop dependent agents in the delegation chain. Record time-to-halt. `[NIST MANAGE 2.4 · IMDA D3]`
- Tools: suspend affected accounts/tenants; block the unapproved service; request deletion from vendor where data was entered.
- Models/features: roll back to last approved version; disable feature flag; switch to human-only process with communicated fallback.
- Do **not** delete logs, prompts, traces or memory — preserve them (Step 3).

### Step 3 — Preserve evidence
Export agent action logs, reasoning traces, prompts/outputs, approvals, tool-call parameters, model/prompt versions, vendor logs; snapshot memory/vector stores; apply legal hold; record chain of custody. `[ISO A.6.2.8 · EU Art. 26(6)]`

### Step 4 — Assess impact and notification duties (Legal leads)
| Duty | Trigger | Clock |
|---|---|---|
| Personal data breach to supervisory authority / individuals | GDPR Art. 33–34; UK GDPR; state breach laws; HIPAA | 72 h (GDPR); varies |
| EU AI Act serious incident | Deployer: inform provider, then importer/distributor and market surveillance authority (Art. 26(5)); provider: Art. 73 — 15 days; 2 days for widespread infringement/critical infrastructure; 10 days for death ⚠ (Annex III timing 2027-12-02) | Per Art. 73 |
| Adverse-decision correction & disclosure | CCPA ADMT, CO SB 26-189 (2027), GDPR Art. 22, ECOA | Per regime |
| Customers / contractual notice | MSAs, DPAs, SLAs | Per contract |
| Regulators (sector) | FCA/PRA, NYDFS (72 h), state insurance, HHS | Per regime |
| Securities disclosure (public cos.) | Material incident | Per SEC rules |
| Law enforcement | Fraud, CSAM, threats | Immediately |

### Step 5 — Remediate and communicate
Correct harmful outputs/decisions (re-run with human review; notify affected persons with reasons and contest route); reverse agent actions where possible; refund/compensate per policy; communicate with customers and staff via {{Comms}}; update the register status to Restricted until re-approval.

### Step 6 — Root cause and lessons learned (≤ {{10}} working days)
Five-whys or equivalent across: instructions/prompt · model behaviour or vendor change · tool/allowlist · permissions/identity · limits/gates · oversight design · data/retrieval · training/awareness · vendor terms · detection/monitoring. Output: corrective actions with owners and dates; updates to Standards, allowlists, tier, evaluation suite, training; Committee review for Sev 1–2. `[ISO Cl. 10.2 · NIST MANAGE 4.2]`

### Step 7 — Restart
Agents and High-tier systems restart only after re-evaluation (Agent Standard §9) and re-approval by the tier's authority; conditions and monitoring enhancements documented.

## 5. Agent-specific playbook (quick card)

1. Kill switch → confirm halted (time-stamp).
2. Revoke credentials; disable tools; freeze memory; halt sub-agents.
3. Pull logs: agent id, principal, session, tool calls & parameters, approvals, cost.
4. Enumerate actions taken since last known-good; classify reversible / irreversible / financial / external.
5. Reverse reversible actions; queue irreversible for human remediation; notify affected parties.
6. Check for injection source (retrieved content, tool output, other agent); quarantine the source.
7. Check other agents sharing tools, prompts, memory or vendor model for the same exposure.
8. Root cause → re-evaluate → re-approve → restart at lower autonomy for {{2 weeks}}.

## 6. Records and metrics

Incident register fields: id · date/time · reporter · system id · category · severity · time-to-halt · data classes · persons affected · notifications made (who/when) · root cause category · corrective actions · closure date. Metrics to Committee: incidents by severity and category; mean time to detect / halt; % with notifications on time; repeat causes; open corrective actions > 30 days. `[NIST MANAGE 4.3 · ISO A.8.4, Cl. 9.1]`

## 7. Exercises

Tabletop at least {{annually}} covering one agent scenario (e.g. refund agent hijacked via injected email) and one data scenario (Restricted data in consumer tool); kill-switch drills {{quarterly}} per Agent Standard §7.2.
