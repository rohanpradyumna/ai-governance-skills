# {{Company}} AI Governance Committee Charter

<!-- Comprehensive depth, or whenever a new committee is being stood up. Scale membership down for small companies (see references/governance-operating-model.md §1). Remove guidance comments. -->

| | |
|---|---|
| Approved by | {{Board / CEO / Executive Committee}} |
| Sponsor | {{Executive Sponsor — role}} |
| Version / effective | {{1.0}} / {{YYYY-MM-DD}} · Charter review: annual |
| Tags | `[NIST GOVERN 1.4, 2.1, 2.3 · ISO 42001 Cl. 5.1, 5.3, 9.3 · IMDA D2]` |

## 1. Purpose

The AI Governance Committee ("Committee") is the body accountable to the {{Board / CEO}} for governing the Company's acquisition, development, deployment, use and retirement of AI systems under the AI Governance Policy. It owns the Company's AI management system {{(ISO/IEC 42001)}}.

## 2. Authority

Delegated by the {{Board / CEO}}, the Committee may:
- Approve, amend and retire AI Standards, procedures and the risk tiering scheme (Schedule A).
- Approve or reject **High-tier** AI systems and agents, set conditions, and suspend or withdraw approval.
- Grant, condition and revoke **exceptions** under Policy §9.3 (with Legal concurrence for prohibited-by-policy items); it may not except legal prohibitions.
- Direct the halting of any AI system or agent pending review.
- Require risk assessments, evaluations, audits or remediation from any function.
- Approve the Approved AI Tools Register criteria and vendor tiering.
- Escalate to the {{Board / Audit & Risk Committee}} any matter exceeding the Company's AI risk appetite, any Sev-1 incident, and any regulatory inquiry.

It must escalate (not decide): changes to the AI Governance Policy itself; AI risk appetite; matters with material financial, legal or reputational exposure above {{threshold}}.

## 3. Membership

| Seat | Role | Voting |
|---|---|---|
| Chair | {{Executive Sponsor — COO / CIO / CRO / GC}} | Yes (casting vote) |
| Secretary / program lead | {{AI Governance Lead}} | Yes |
| Legal & Privacy | {{General Counsel or delegate; DPO}} | Yes |
| Security | {{CISO or delegate}} | Yes |
| Data / AI engineering | {{Head of Data / AI}} | Yes |
| People | {{CHRO or delegate}} | Yes |
| Risk / Compliance | {{Head of Risk or Compliance}} | Yes |
| Business units using AI | {{Heads of Product, Operations, Customer Support, Marketing}} — {{2–3}} seats | Yes |
| Internal Audit | {{Head of Internal Audit}} | Observer (no vote — independence) |
| Invited as needed | System Owners presenting; Procurement; Comms; external counsel or ethics advisor | No |

Members serve ex officio; delegates must have authority to commit their function. Conflicts of interest (e.g. a member is the System Owner of the item under decision) are declared and the member abstains.

## 4. Quorum and decisions

Quorum: Chair (or delegate) + Legal/Privacy + Security + at least one business seat. Decisions by majority of voting members present; Chair casts deciding vote. Legal may veto on lawfulness. Decisions, rationale, conditions and dissent are minuted. Urgent High-tier decisions between meetings: Chair + Legal + Security may decide and ratify at the next meeting.

## 5. Cadence and standing agenda

Meets {{monthly}} during program rollout, then {{quarterly}} plus ad hoc for High-tier approvals and incidents.

Standing agenda:
1. Actions from last meeting
2. AI System Register health (new, changed, suspected shadow AI, overdue reviews)
3. High-tier pipeline: approvals, conditions, re-approvals after scope change
4. Agents: autonomy changes, limit breaches, kill-switch test status
5. Incidents and near-misses; corrective actions
6. Monitoring metrics and threshold breaches for High-tier systems
7. Regulatory and standards changes (Legal) and required policy updates
8. Vendor matters: due-diligence coverage, model-change notices, contract gaps
9. Training and literacy completion by role
10. Exceptions register: new, expiring, overdue
11. Audit findings and management review items {{(ISO 42001 Cl. 9.3)}}
12. Escalations to the Board

## 6. Inputs and outputs

**Inputs**: register extracts; risk assessments and evaluation reports; incident reports; monitoring dashboards; regulatory watch memo; vendor DDQs; training records; audit reports; exception requests.
**Outputs**: minutes and decision log; approved Standards; approval letters with conditions; exception grants; escalation memos; {{annual}} AI governance report to the Board containing the metrics in §7.

## 7. Metrics reported

Systems by tier and status · % register rows attested on time · High-tier approvals / rejections / conditioned · # exceptions open and average age · incidents by severity, mean time to detect and to halt · % notifications on time · training completion by role · vendor DDQ coverage and overdue reviews · monitoring threshold breaches · regulatory items pending action · audit findings open > 90 days.

## 8. Working groups

The Committee may charter working groups (e.g. Agent Security, Employment AI, Vendor Review) chaired by a member, with defined scope, deliverables and end date; they recommend, the Committee decides.

## 9. Secretariat

The AI Governance Lead schedules meetings, circulates papers {{5}} working days ahead, keeps minutes and the decision log, tracks actions, and maintains this Charter.

## 10. Review

This Charter is reviewed annually by the Committee and approved by the {{Board / CEO}}; effectiveness is assessed as part of {{internal audit / management review}}.
