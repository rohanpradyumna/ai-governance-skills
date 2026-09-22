# AI governance intake questionnaire

<!-- Question bank for SKILL.md step 1. Ask at most eight questions in one message; pick from the ★ set first. Skip anything already answered. Default the rest using the "Default if unknown" column and record assumptions in the deliverable. -->

## ★ Core eight (ask these)

| # | Question | Why it matters | Default if unknown |
|---|---|---|---|
| ★1 | How large is the company (headcount), what sector, and is it in a regulated industry (finance, insurance, health, employment services, education, critical infrastructure, public sector, legal)? | Sizes the document set; triggers sector overlays | Mid-size (50–500), unregulated B2B |
| ★2 | Where are your employees, and where are your customers/users? (EU/EEA, UK, US — which states, especially CA/CO/TX/IL/NY — Singapore, other) | Determines legal regimes | US-only, no EU users |
| ★3 | Do you only *use* AI tools/models/agents (deployer), or do you also *build and sell* AI features or models (provider)? Do you fine-tune or rebrand third-party models? | Provider duties are much heavier; substantial modification flips the role | Deployer only |
| ★4 | What AI is in use or planned? List tools (e.g. ChatGPT/Claude/Gemini/Copilot, coding assistants, meeting assistants, AI features in CRM/helpdesk), models/APIs, and **any agents or automations that take actions** (send messages, change records, spend money, run code, open PRs). Anything customer-facing? Anything touching hiring, pay, credit, insurance, housing, education or health decisions? | Builds the register and tiers; agents make the Agent Standard mandatory | Enterprise chat assistant + coding assistant; no agents; not customer-facing; no people decisions |
| ★5 | How deep do you want to go: **Starter** (rules people can follow this week), **Standard** (defensible program), or **Comprehensive** (ISO 42001 / audit-ready)? | Selects the document set | Standard |
| ★6 | Which existing policies should this align with or reference: information security, privacy, data classification (what labels do you use?), code of conduct, procurement/vendor management, incident response, records retention, HR/disciplinary? | Avoids duplication; reuses classification labels | Assume standard InfoSec/Privacy/Code of Conduct exist; four-level classification (Public/Internal/Confidential/Restricted) |
| ★7 | Who will approve and own the policy (board, CEO, exec committee, CIO/CISO/GC/COO)? Is there an existing risk, security or privacy committee that could own AI governance? | Sets roles and the committee model | CEO approves; COO/CIO sponsors; new AI Governance Committee drawn from existing leaders |
| ★8 | Tone and format: plain-language handbook or formal policy register style? Markdown, Word, or Confluence/Notion? Any house style (numbering, British/American English)? | Output formatting | Formal policy + plain-language AUP; Markdown; American English |

## Secondary (ask only if the answer changes the output and isn't inferable)

| # | Question | Default |
|---|---|---|
| 9 | Do you use AI in recruiting, performance, promotion, scheduling, or monitoring of employees? Any hiring in NYC, Illinois, California, Colorado, or the EU? | No employment AI |
| 10 | Any AI generating content published externally (marketing, social, images/video, customer emails)? | Yes — marketing copy, human-published |
| 11 | Do you process special-category / sensitive personal data (health, biometrics, children, financial account data)? PHI under HIPAA? | No |
| 12 | Do agents have access to production systems, payment/refund capabilities, customer communication channels, or code deployment? What caps exist today? | If agents exist: assume production read, no financial, human-approved comms |
| 13 | Are AI tools behind SSO with training opt-out and a DPA? Any known personal/consumer-account use (shadow AI)? | Partially; shadow AI likely |
| 14 | Do customer or client contracts restrict AI use or require disclosure? | Unknown — handoff item |
| 15 | Any existing AI incidents, near-misses, or audit findings to address? | None reported |
| 16 | Risk appetite: does leadership want to be conservative (ban by default, approve exceptions) or enabling (allow by default within guardrails)? | Enabling within guardrails for T3; approval-based for T1/T2 |
| 17 | Board reporting expectations and cadence? Any ISO 27001 / SOC 2 program to piggyback on? | Annual board report; SOC 2 exists |
| 18 | Is there a works council, union, or employee representative body to consult? | No (EU: handoff item) |
| 19 | Preferred numeric defaults: log retention, agent spend caps, review cadences? | Use skill defaults; flag as adjustable |
| 20 | Target dates: when must the policy be live? Any regulatory deadline driving this (e.g. CA ADMT 2027-01-01, CO 2027-01-01, EU Annex III 2027-12-02)? | 90 days |

## Recording assumptions

<!-- Copy this block into the deliverable summary. -->

**Assumptions made at intake**
- Company profile: {{size}}, {{sector}}, {{regulated?}}
- Jurisdictions: employees {{...}}; customers {{...}}
- Role: {{deployer / provider / both}}
- AI footprint: {{tools}}, {{agents: yes/no + actions}}, {{customer-facing: yes/no}}, {{people decisions: yes/no}}
- Depth: {{Starter / Standard / Comprehensive}}
- Aligned policies: {{...}}; classification labels: {{...}}
- Owner/approver: {{...}}; committee: {{existing / new}}
- Defaults used: log retention {{6/12}} months; agent caps {{...}}; review cadence {{annual / semi-annual}}
