# AI Risk Assessment — {{System name}} ({{AI-###}})

<!-- Per-system assessment for Elevated/High tier (short form for Standard: Parts 1, 2, 9 only). Modular: complete Part 6 (DPIA) when personal data is processed; Part 7 (FRIA) when EU AI Act Art. 27 applies. Structure follows NIST MAP → MEASURE → MANAGE and ISO/IEC 42001 A.5 / ISO 42005. Remove guidance comments. -->

| | |
|---|---|
| System Owner (role) | {{…}} · Technical Owner: {{…}} |
| Assessor(s) | {{roles}} · Independent reviewer (High): {{role}} |
| Version / date | {{1.0}} / {{YYYY-MM-DD}} |
| Trigger | New system · Scope change ({{what}}) · Periodic review · Incident |
| Approval authority | {{Committee / AI Governance Lead / System Owner}} |
| Tags | `[NIST MAP 1–5, MEASURE 1–4, MANAGE 1–4 · ISO 42001 Cl. 6.1.4, A.5.2–A.5.5 · GDPR Art. 35 · EU AI Act Art. 9, 27]` |

## Part 1 — Context (NIST MAP 1)

1.1 **Purpose and intended use**: {{what the system does, for whom, in which process}}. **Out-of-scope / prohibited uses**: {{…}}. `[MAP 1.1 · ISO A.9.4]`
1.2 **Business value and alternatives considered**: {{…}}. `[MAP 1.4, 3.1]`
1.3 **Role**: Deployer / Provider / Both. Substantial modification or rebranding of a third-party system? {{Y/N}}. `[EU Art. 25]`
1.4 **Components**: model(s) and versions; vendor and hosting path; tools/connectors; data stores; agents in chain. `[MAP 4]`
1.5 **Users and operators**: {{roles}}; proficiency required: {{…}}. `[MAP 3.4]`
1.6 **Affected persons and groups**: {{customers, employees, candidates, public, vulnerable groups, minors}}; scale: {{n per month}}. `[MAP 5.1 · ISO A.5.4]`
1.7 **Jurisdictions**: users {{…}}; affected persons {{…}}; data location {{…}}.
1.8 **Autonomy level** (0–5) and **action classes**: {{…}} (agents: attach approval package per AI Agent Standard §4.2).

## Part 2 — Tiering (Risk Tiering Standard)

| Dimension | Score 0–3 | Rationale |
|---|---|---|
| A Decision impact on people | | |
| B Autonomy | | |
| C Data sensitivity | | |
| D Reversibility & blast radius | | |
| E Audience & exposure | | |
| F Regulatory / contractual trigger | | |
| G Model & provenance uncertainty | | |
| **Total / max** | | |

Prohibited-use check: {{none matched / matched item …}}. **Tier**: {{High / Elevated / Standard}}. **Legal classification**: EU {{…}}; US {{CCPA ADMT / CO ADMT / IL / NYC / none}}; sector {{…}}. Override applied? {{Y/N, why}}. `[MAP 1.5 · EU Art. 6]`

## Part 3 — Data (NIST MAP 4, MEASURE 2.10; ISO A.7)

| Item | Detail |
|---|---|
| Data classes in inputs / outputs / logs | {{Public / Internal / Confidential / Restricted}} |
| Personal data? Special category? Children? | {{…}} → complete Part 6 |
| Sources and provenance; rights to use | {{…}} `[ISO A.7.3, A.7.5]` |
| Vendor data terms: training exclusion, retention, sub-processors, region | {{clause refs}} |
| Data quality & representativeness for this use | {{…}} `[ISO A.7.4 · EU Art. 10]` |
| Retention of prompts/outputs/logs | {{months}}; legal hold process |

## Part 4 — Risk identification (NIST MAP 5, AI 600-1 taxonomy)

<!-- Score likelihood (L) and severity (S) 1–4; rate = L×S. Include only relevant rows; add system-specific ones. -->

| # | Risk | Affected | L | S | Rate | Existing controls | Gaps |
|---|---|---|---|---|---|---|---|
| R1 | Inaccurate / confabulated output relied on | {{…}} | | | | | |
| R2 | Harmful bias or discriminatory outcome | | | | | | |
| R3 | Personal data exposure or unlawful processing | | | | | | |
| R4 | Confidential / IP leakage via prompts, outputs, vendor retention | | | | | | |
| R5 | Prompt injection / goal hijack (direct or via retrieved content) | | | | | | |
| R6 | Tool misuse, out-of-scope or irreversible action (agents) | | | | | | |
| R7 | Identity / privilege abuse; shared credentials | | | | | | |
| R8 | Cascading failure, runaway cost, blast radius | | | | | | |
| R9 | Lack of transparency to affected persons; undisclosed AI | | | | | | |
| R10 | Automation bias / ineffective human oversight | | | | | | |
| R11 | Vendor / model change, outage, lock-in | | | | | | |
| R12 | Regulatory non-compliance ({{name regimes}}) | | | | | | |
| R13 | Safety / physical harm (if applicable) | | | | | | |
| R14 | Reputational / customer trust | | | | | | |
| R15 | Environmental / cost | | | | | | |

`[MAP 5.1 · MEASURE 3.1 · ISO A.5.4, A.5.5 · OWASP LLM/ASI]`

## Part 5 — Evaluation plan and results (NIST MEASURE)

| Property | Method & dataset | Acceptance criterion | Result | Pass? |
|---|---|---|---|---|
| Accuracy / task success | {{…}} | {{≥ x%}} | | |
| Robustness / edge cases | | | | |
| Fairness / disparate impact (if people-affecting) | {{method: e.g. selection-rate ratio, error-rate parity by group}} | {{threshold}} | | |
| Safety refusals / harmful content | | | | |
| Security: injection (incl. indirect), tool misuse, data exfiltration | {{red-team plan}} | | | |
| Limits & gates enforced (agents) | {{tests}} | 100% | | |
| Kill switch / auto-halt (agents) | | ≤ {{15}} min | | |
| Logging completeness | | 100% of fields | | |
| Disclosure behaviour | | | | |
| Explainability sufficient for reasons/adverse-action notices | | | | |

Independent review (High): {{role, date, conclusion}}. `[MEASURE 1.3, 2.1–2.11 · ISO A.6.2.4]`

## Part 6 — Data Protection Impact Assessment (complete if personal data)

<!-- GDPR Art. 35 / UK GDPR / equivalent. Combine with FRIA where Part 7 applies (AI Act Art. 27(4)). -->

6.1 Processing description, purposes, categories of data and subjects, recipients, transfers, retention.
6.2 Lawful basis per purpose (Art. 6/9); legitimate-interest assessment if relied on.
6.3 Necessity and proportionality; minimisation; alternatives.
6.4 Automated decision-making (Art. 22 / CCPA ADMT / CO ADMT): does the system make or materially influence a decision with legal or similarly significant effect? Safeguards: human intervention, contest, explanation, notice, opt-out where required.
6.5 Rights handling: access, erasure, objection — including data in logs, memory and vendor retention.
6.6 Risks to individuals and measures (reference Part 4 rows).
6.7 DPO / Privacy Lead opinion; consultation with supervisory authority required? {{Y/N}}.
`[GDPR Art. 35 · AI Act Art. 26(9) · NIST MEASURE 2.10]`

## Part 7 — Fundamental Rights Impact Assessment (EU AI Act Art. 27; complete if in scope ⚠ 2027-12-02)

<!-- In scope: public bodies; private entities providing public services; deployers using Annex III high-risk AI for credit scoring or life/health insurance pricing. -->

7.1 Deployer's processes in which the system is used, in line with intended purpose.
7.2 Period and frequency of use.
7.3 Categories of natural persons and groups likely affected.
7.4 Specific risks of harm to those persons/groups (reference Part 4).
7.5 Human oversight measures per the provider's instructions for use.
7.6 Measures if risks materialise: internal governance, complaint mechanism, redress.
7.7 Notification to market surveillance authority (template) — date, reference. Reuse of prior FRIA? {{Y/N}}.
`[EU Art. 27 · ISO A.5.4]`

## Part 8 — Human oversight design (NIST MAP 3.5, GOVERN 3.2)

| Element | Design |
|---|---|
| Oversight role(s) | {{role}}; competence evidence: {{training}} |
| What they see | {{evidence, reasoning, confidence, data used}} |
| Authority | {{override, halt, escalate — without approval}} |
| Time / workload | {{expected reviews per hour; ceiling}} |
| Sampling (autonomous actions) | {{rate}} |
| Contest & explanation route for affected persons | {{…}} |
| Automation-bias countermeasures | {{…}} |

`[EU Art. 14, 26(2) · IMDA D2 · ASI09]`

## Part 9 — Risk treatment and residual risk (NIST MANAGE 1)

| Risk # | Treatment (control added / changed) | Owner (role) | Due | Residual L×S | Accepted by |
|---|---|---|---|---|---|
| | | | | | |

Controls required by tier (Schedule A) — confirm each: register ✔ · approved tools ✔ · data matrix ✔ · evaluation ✔ · oversight ✔ · disclosure ✔ · logging {{months}} ✔ · monitoring ✔ · vendor DDQ ✔ · change control ✔ · agent controls ✔ · training ✔.

**Residual risk statement**: {{…}}. **Decision**: Approve / Approve with conditions ({{list}}) / Reject. **Approver (role), date**: {{…}}. `[MANAGE 1.2–1.4 · ISO Cl. 6.1.3]`

## Part 10 — Monitoring and review plan (NIST MANAGE 4)

Metrics and thresholds: {{accuracy, fairness, override rate, incident count, cost, drift indicators, limit approaches}} · Alerting to: {{role}} · Review cadence: {{quarterly (High) / semi-annual}} · Re-assessment triggers: scope change, incident, vendor model change, regulatory change · Decommission criteria: {{…}}. `[MANAGE 4.1 · ISO A.6.2.6 · EU Art. 26(5), 72]`

## Sign-off

| Role | Name | Date |
|---|---|---|
| System Owner | | |
| Technical Owner | | |
| Privacy Lead (if Part 6) | | |
| Security Lead | | |
| Independent reviewer (High) | | |
| Approving authority | | |
