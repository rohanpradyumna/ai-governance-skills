# {{Company}} AI Literacy and Training Plan

<!-- Satisfies EU AI Act Art. 4 (in force since 2025-02-02), Art. 26(2) oversight competence, ISO/IEC 42001 Cl. 7.2–7.3 and A.4.6, NIST GOVERN 2.2. Scale modules to company size; a 40-person company can deliver Module 1 as a 45-minute session. Remove guidance comments. -->

| | |
|---|---|
| Owner | {{HR / L&D}} · Content owner: {{AI Governance Lead}} |
| Approver | {{AI Governance Committee}} |
| Version / effective | {{1.0}} / {{YYYY-MM-DD}} · Review: annual and on material change to tools, Standards or law |
| Records | {{LMS}}; retained {{5}} years; reported to Committee {{quarterly}} |
| Tags | `[EU AI Act Art. 4, 26(2) · NIST GOVERN 2.2, 3.2 · ISO 42001 Cl. 7.2, 7.3, A.4.6 · IMDA D2, D4 · OWASP ASI09]` |

## 1. Objective

Ensure every person who uses, builds, approves or oversees AI on the Company's behalf has literacy proportionate to their role, the systems they touch and the people affected — "to the best extent" required by Art. 4 and sufficient for meaningful human oversight.

## 2. Audience segmentation and requirements

| Segment | Who | Required modules | Deadline | Refresh |
|---|---|---|---|---|
| **All Personnel** | Everyone incl. contractors with system access | M1 | Within {{30}} days of joining; existing staff by {{date}} | Annual |
| **Power users** | Staff using AI daily for Confidential data; marketing/comms publishing AI-assisted content; sales using AI on customer data | M1 + M2 | Before tool access is granted | Annual |
| **System Owners & Technical Owners** | Per register | M1 + M2 + M3 | Before approval of their first system | Annual |
| **Human Oversight roles** | Approvers/reviewers of High-tier outputs and agent actions | M1 + M2 + M4 (system-specific) | Before assuming the role; competence sign-off | Semi-annual + after scope change |
| **Agent Owners / Operators / builders** | Anyone configuring or running agents | M1 + M2 + M3 + M5 | Before agent registration | Semi-annual |
| **People decision-makers** | HR, recruiters, managers using AI in hiring/performance/pay; credit/underwriting staff | M1 + M2 + M6 | Before use | Annual |
| **Approvers & Committee** | AI Governance Lead, Committee members, Legal, Privacy, Security, Procurement | M1 + M3 + M7 | Within {{60}} days of appointment | Annual |
| **Executives & Board** | | M8 briefing | Within {{90}} days; annually | Annual |

## 3. Modules

| Module | Duration | Content | Assessment |
|---|---|---|---|
| **M1 AI fundamentals & the AUP** | 45–60 min | What AI/GenAI/agents are and aren't; how models fail (confabulation, bias, injection); the Acceptable Use Standard walk-through: approved tools, data classes, never-list, disclosure, reporting; where to ask | Quiz ≥ {{80%}}; AUP acknowledgement |
| **M2 Using AI well with sensitive work** | 45 min | Verification techniques; prompt hygiene (no secrets, minimisation); IP and client-contract checks; labelling AI-assisted work; recognising and reporting incidents; scenario exercises drawn from the register | Scenario quiz |
| **M3 Governing an AI system** | 90 min | Register and tiering; risk assessment walkthrough; DPIA/FRIA triggers; evaluation and acceptance criteria; vendor DDQ and contract clauses; change control; monitoring; decommissioning | Complete a mock assessment |
| **M4 Meaningful human oversight (system-specific)** | 60–120 min per system | What the system does, what it gets wrong, base rates, failure modes; how to read its evidence and confidence; override and halt authority; automation-bias drills (seeded wrong recommendations); workload expectations; how affected persons contest; legal notices for this system | Practical: reviewer catches ≥ {{X}}% of seeded errors; competence sign-off by System Owner |
| **M5 Agents** | 90 min | Autonomy levels, action classes and gates; identity and least privilege; allowlists, limits, kill switch; untrusted content and injection; logging; disclosure; scope-change re-approval; incident quick card | Lab: configure a sandbox agent to Standard; kill-switch drill |
| **M6 AI in decisions about people** | 60 min | Applicable law for the company's jurisdictions ({{EEOC / EU Annex III / NYC LL 144 / IL HB 3773 / CA ADMT & FEHA / CO SB 26-189 / ECOA}}); notices and consent; bias testing basics; human review and adverse-action reasons; record retention; what to escalate | Quiz + HR/Legal sign-off |
| **M7 Governance & regulatory landscape** | 90 min | NIST AI RMF, ISO/IEC 42001, EU AI Act (timeline, roles, Art. 4/50/26/27), US state laws, sector rules; the Company's Policy, Standards and decision rights; how to run an approval; incident escalation | Discussion; case decisions |
| **M8 Executive & Board briefing** | 30–45 min | Risk appetite; regulatory exposure and dates; program status and metrics; incidents; decisions required | — |

## 4. Delivery

Formats: {{LMS e-learning}} for M1/M2/M6; live workshops for M3/M5/M7; system-specific sessions run by System Owners for M4; briefing deck for M8. Materials maintained by {{AI Governance Lead}}; updated within {{30}} days of any Standard change, new approved tool, or regulatory change affecting content. New approved tools trigger a short (≤ 10 min) tool-specific micro-module.

## 5. Competence evidence for oversight roles (Art. 26(2))

For each High-tier system, the register links to: list of oversight-role holders; M4 completion and practical result per person; System Owner's competence sign-off; date of last refresh. Individuals without current competence evidence may not approve or override for that system.

## 6. Metrics (to Committee)

Completion by segment and module · overdue by segment · quiz pass rates · M4 practical results · time from role assignment to competence sign-off · incidents attributable to training gaps · training content age vs. Standard versions.

## 7. Schedule (first year)

| When | Action | Owner |
|---|---|---|
| {{Month 1}} | Publish AUP; deliver M1 to all staff (live + recording); acknowledgements | HR / AI Governance Lead |
| {{Month 1–2}} | M2 to power users; M5 to anyone running agents; M6 to HR/recruiting | AI Governance Lead / HR |
| {{Month 2–3}} | M3 to System/Technical Owners; M7 to Committee and approvers | AI Governance Lead |
| {{Month 3}} | M4 for each High-tier system; competence sign-offs | System Owners |
| {{Month 3}} | M8 executive/board briefing | Executive Sponsor |
| Ongoing | New-joiner M1 within 30 days; micro-modules on tool approval; annual refresh cycle from {{month}} | HR |
