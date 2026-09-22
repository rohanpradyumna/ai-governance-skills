# Governance operating model

**Read this when:** drafting the governance/roles section of the policy, the committee charter, or a RACI; or when the user asks "who should own this?"

---

## 1. Document hierarchy

| Layer | Purpose | Length | Approver | Change frequency |
|---|---|---|---|---|
| **AI Governance Policy** | Intent, scope, principles, prohibited uses, roles, mandatory outcomes, enforcement. The ISO 42001 Cl. 5.2 policy. | ≤ 6 pages | Board / CEO / Exec committee | Annual |
| **Standards** (Acceptable Use; AI Agent; Data & Privacy for AI; Employment AI; Model Risk; Security for AI) | Measurable requirements ("shall … within …"), control catalogues, tier matrices | 2–10 pages each | AI Governance Committee | Semi-annual / on change |
| **Procedures & runbooks** (intake & approval, risk assessment, incident response, vendor DDQ, change control) | Step-by-step, forms, SLAs | As needed | AI Governance Lead | As needed |
| **Registers & records** (AI system register, risk assessments, approvals, training records, incident log, SoA) | Evidence | — | Owners | Continuous |

Precedence: Policy > Standard > Procedure. Conflicts resolve upward; a procedure cannot relax a standard. Cross-reference existing policies instead of duplicating (InfoSec, Privacy, Code of Conduct, Procurement, HR, Records Retention) — the AI policy states *what is different because it's AI*.

Sizing by company:

| Company | Realistic set |
|---|---|
| < 50 people, deployer only | 1-page AUP + register + tier table; policy owner is a named exec; "committee" = monthly 30-min review with CEO, ops lead, whoever runs IT/security |
| 50–500 | Governance Policy + AUP + Agent Standard (if agents) + register + risk assessment + incident runbook; small committee (4–6) |
| 500–5,000 | Full set; committee + working group; second-line function (risk/compliance) owns the register; internal audit covers annually |
| > 5,000 or regulated | Full set + sector overlays + ISO 42001 SoA; three-tier model below; Chief AI Officer or equivalent |

## 2. Three-tier governance model

Single-committee models either rubber-stamp or bottleneck. Default to three tiers, scaled down for small companies:

| Tier | Body | Composition | Decides |
|---|---|---|---|
| **Oversight** | Board (or Audit/Risk Committee) | Directors; receives reports at least annually, quarterly if High-tier systems exist | Risk appetite, policy approval, material incidents, strategy |
| **Governance** | **AI Governance Committee** | Chair: exec sponsor (COO/CIO/CRO/GC). Members: Legal/Privacy, Security, Data/AI lead, HR, Risk/Compliance, business unit heads with AI use, Internal Audit as observer. 6–10 people. | Standards approval, T1 approvals, exceptions, prohibited-use waivers (with legal), incident escalation, register health, vendor tiering |
| **Operational** | **AI Governance Lead / Office** + working group | Named lead (often in Risk, Legal, Security or a CoE) + delegates from each function | Intake triage, T2 approvals, register upkeep, risk assessment facilitation, training, monitoring reports, procedure changes |

Cadence: Committee monthly during rollout, then quarterly + ad hoc for T1/incidents. Quorum: chair + legal/privacy + security + one business member. Decisions logged with rationale.

## 3. Roles (define as roles, assign to titles at intake)

| Role | Accountable for | Typical title |
|---|---|---|
| **Executive Sponsor** | Policy ownership, resources, board reporting | COO / CIO / CRO / GC |
| **AI Governance Lead** | Running the program; register; intake; committee secretariat; policy maintenance | Head of AI Governance / Responsible AI lead / Risk or Privacy lead (small cos: whoever owns InfoSec policy) |
| **AI Governance Committee** | Decisions in §2 | — |
| **System Owner** | A specific AI system's tiering, risk assessment, controls, monitoring, register accuracy, decommissioning | Business/product leader for the use case |
| **Model Owner / Technical Owner** | Technical performance, evaluation, security, change control | Eng/DS lead |
| **Agent Owner** | Agent scope, autonomy, limits, disclosure, compliance with Agent Standard | Product/ops owner of the workflow |
| **Agent Operator** | Day-to-day running, monitoring, halting | Ops / SRE / support lead |
| **Human Oversight Role** (per T1 system) | Reviewing/overriding AI-influenced decisions; meets the five-part meaningful-oversight test | Domain expert with authority |
| **Data Protection Officer / Privacy Lead** | DPIA/FRIA, lawful basis, rights requests, vendor DPAs | DPO / Privacy counsel |
| **Security Lead** | AI threat modelling, identity for agents, logging, incident response integration | CISO / security lead |
| **Procurement / Vendor Management** | Due diligence, contract clauses, vendor register | Procurement lead |
| **HR / People** | Employment-AI rules, worker notifications, training rollout, disciplinary process | CHRO / HRBP |
| **Legal / Compliance** | Regulatory register, jurisdiction review, disclosures, regulator liaison | GC / Compliance |
| **Internal Audit** (or external assurance) | Independent assessment of the program; reports to Audit Committee, **not** to the AI function (ISO 42001 Cl. 9.2 independence) | Internal Audit |
| **All Personnel** | Follow the AUP; complete training; report concerns/incidents | — |

Rules: one **Accountable** per outcome; every T1/T2 system has a System Owner who is an employee (not a vendor, not a contractor); owners named in the register by role *and* current holder.

## 4. RACI (R = does, A = accountable, C = consulted, I = informed)

| Activity | Exec Sponsor | Gov Lead | Committee | System Owner | Model/Tech Owner | Privacy | Security | HR | Legal | Procurement | Int. Audit | All staff |
|---|---|---|---|---|---|---|---|---|---|---|---|---|
| Approve AI Governance Policy | A | R | C | I | I | C | C | C | C | I | I | I |
| Approve Standards | I | R | A | C | C | C | C | C | C | C | I | I |
| Maintain regulatory register / jurisdiction review | I | R | I | I | I | C | I | C | A | I | I | — |
| Maintain AI system register | I | A | I | R | C | I | C | I | I | C | I | I (report shadow AI) |
| Intake new AI use case | I | A | I | R | C | C | C | C (if people) | C | C | — | — |
| Risk tiering | I | A | I | R | C | C | C | C | C | — | — | — |
| Risk / impact assessment | I | C | I | A | R | C | C | C | C | — | — | — |
| DPIA / FRIA | I | I | I | R | C | A | C | C | C | — | — | — |
| Bias & performance testing | — | I | I | A | R | C | — | C | C | — | — | — |
| Security review / threat model | — | I | I | C | R | — | A | — | — | — | — | — |
| T1 approval | C | R | A | C | C | C | C | C | C | — | I | — |
| T2 approval | I | A | I | R | C | C | C | C | C | — | — | — |
| T3 registration | — | I | — | A/R | — | — | — | — | — | — | — | — |
| Agent scope & limits approval | I | A (T2) | A (T1) | R | C | C | C | — | C | — | — | — |
| Vendor due diligence & contract | — | C | I | R | C | C | C | — | C | A | — | — |
| Approved-tool list & technical enforcement | I | A | I | — | — | C | R | — | C | C | — | I |
| Training & literacy program | I | A | I | — | — | C | C | R | C | — | — | R (complete) |
| Worker / candidate notifications | — | C | I | R | — | C | — | A | C | — | — | — |
| Monitoring & periodic review of T1 systems | I | C | I | A | R | C | C | — | — | — | I | — |
| Incident response (AI) | I | C | I | R | R | C | A | C | C | C | I | R (report) |
| Regulator / customer notification | A | C | C | C | — | C | C | — | R | — | — | — |
| Exceptions & waivers | I | R | A | C | — | C | C | — | C | — | I | — |
| Internal audit of program | I | C | I | C | C | C | C | — | C | — | A/R | — |
| Management review & board reporting | A | R | C | — | — | — | — | — | — | — | C | — |
| Decommissioning | — | I | — | A | R | C | C | — | — | C | — | — |

Collapse columns for small companies (e.g. Gov Lead = Security = Privacy = one person) but keep Internal Audit or an external reviewer separate from whoever runs the program.

## 5. Committee charter essentials (→ `assets/ai-governance-committee-charter.md`)

Purpose · authority (delegated from board/CEO; what it can approve, what it must escalate) · membership & chair · quorum & voting · cadence · standing agenda (register changes, T1 pipeline, incidents, monitoring metrics, regulatory changes, training status, exceptions expiring) · inputs it receives · outputs it produces · conflicts of interest · secretariat · review of the charter annually.

Standing metrics to report: # systems by tier; % register entries reviewed on time; # T1 approvals / rejections / conditions; # exceptions open and age; incidents by severity and mean time to halt; training completion by role; vendor DDQ coverage; monitoring threshold breaches; regulatory changes pending action.

## 6. Enforcement and exceptions

- **Consequences** in the AUP: violations handled under the disciplinary policy; deliberate exfiltration of restricted data or circumventing controls treated as serious misconduct; contractors under contract terms.
- **Exceptions**: written request → Gov Lead (T2/T3) or Committee (T1/prohibited-by-policy) → compensating controls → expiry ≤ 12 months → logged in an exceptions register. Legal prohibitions cannot be excepted.
- **Technical enforcement pairing**: approved tools behind SSO; unapproved AI domains blocked or monitored; DLP on prompts for restricted classes; enterprise tenants with training-opt-out; agent gateway for tool calls; spend caps in billing; MDM for browser extensions. State in the policy that technical controls will be used to enforce it.

## 7. Maturity roadmap (use for the "first 90 days" and the roadmap section)

| Stage | Markers |
|---|---|
| **0 Ad hoc** | No register; personal accounts; no owner |
| **1 Foundational (target ≤ 90 days)** | AUP published; approved-tool list enforced via SSO; register started (incl. suspected shadow AI); owner and committee named; literacy session delivered; incident channel exists |
| **2 Managed (3–9 months)** | Governance Policy approved; tiering applied to all systems; T1 assessments done; Agent Standard live with per-agent identities and caps; vendor DDQ in procurement; monitoring for T1 |
| **3 Defined (9–18 months)** | Standards complete; RACI operating; metrics to board; internal audit performed; training by role; SoA drafted |
| **4 Assured** | ISO 42001 certification or equivalent external assurance; continuous monitoring; automated policy-as-code for agents |
