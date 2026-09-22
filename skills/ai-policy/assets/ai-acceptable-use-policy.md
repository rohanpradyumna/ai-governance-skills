# {{Company}} AI Acceptable Use Standard

<!-- Employee-facing. Target 1–3 pages, readable in ten minutes. Plain language. Name the tools, name the data classes, name the consequences, name where to ask. Every rule here must be enforceable by a technical control or a process named in §7. -->

| | |
|---|---|
| Owner | {{AI Governance Lead — role}} · Approver: {{AI Governance Committee}} |
| Version / effective | {{1.0}} / {{YYYY-MM-DD}} · Review: {{semi-annual}} |
| Applies to | Everyone who works for or on behalf of {{Company}}, on any device, for any Company work |
| Parent policy | AI Governance Policy §7.4 · Definitions in AI Governance Policy §3 |

## 1. The short version

- Use **approved AI tools** (§2) through your Company account. Don't use personal or free AI accounts for work.
- Know your data class (§3). **Public and Internal** data can go into approved tools. **Confidential** only into tools approved for it. **Restricted** never, unless Legal/Privacy has approved that exact tool for that exact use.
- **Never** paste passwords, API keys, tokens or customer payment data into any AI tool.
- **You own the output.** Check it before you rely on it or send it. AI makes things up.
- If AI **decides or materially influences** something about a person (hiring, pay, credit, a customer's eligibility), a qualified human must review before it takes effect.
- Building or connecting an **AI agent** — anything that sends, changes, spends or runs things on its own — requires approval under the AI Agent Standard first.
- **Tell people** when they're talking to AI. Don't pass AI work off as human-authored where it matters.
- **Report** anything that goes wrong to {{channel}} — fast, no blame for good-faith reports.

## 2. Approved tools

<!-- Pull from the Approved AI Tools Register. List the tool, the account type, the highest data class allowed, and what it's for. Keep the master list in the register; this table is the snapshot at issue date. -->

| Tool | Use it via | Highest data class allowed | Approved for | Not for |
|---|---|---|---|---|
| {{e.g. Claude Team / ChatGPT Enterprise}} | Company SSO | Confidential | Drafting, summarising, analysis, coding help | Restricted data; consequential decisions about people |
| {{Coding assistant}} | Company SSO | Confidential (source code) | Code completion, review, tests | Committing generated code without review; secrets |
| {{Meeting assistant}} | Company tenant only | Internal | Notes of internal meetings with attendee notice | External calls without consent; HR/legal meetings |
| {{AI features in CRM / helpdesk}} | Existing system | Confidential (within that system) | Drafting replies, summaries | Auto-sending without review {{unless Agent Standard approved}} |
| {{Image / media generator}} | Company account | Public / Internal | Internal drafts, marketing with review & marking | Real people's likenesses; unlabelled external use |

Anything not listed = **not approved**. To get a tool approved, ask {{AI Governance Lead / channel}}; approval takes about {{10}} working days for standard tools. The current list is at {{link}}.

## 3. What data can go where

<!-- Map to the company's own classification labels. -->

| Data class | Examples | Personal / free AI accounts | Approved tools (per §2 ceiling) |
|---|---|---|---|
| **Public** | Published content, marketing, open-source code | OK | OK |
| **Internal** | Everyday business docs, non-sensitive internal data | **No** | OK |
| **Confidential** | Customer data, contracts, financials, source code, product plans, employee data | **No** | Only tools approved for Confidential |
| **Restricted** | Health data, biometrics, children's data, payment card data, credentials, privileged legal material, trade secrets, M&A, export-controlled or regulated data | **No** | **No** — unless Legal/Privacy approved that tool for that use (a Business Associate Agreement is required for health data) |

"Entering data" includes pasting, uploading files, connecting a plugin or integration, and letting an agent read a system. If you're unsure of the class, treat it as Confidential and ask {{Privacy / data owner}}.

## 4. Using AI well

- **Verify before you rely.** Check facts, figures, citations, code and legal/financial statements. You are responsible for what you submit, ship or send.
- **Keep humans in charge of people decisions.** AI may assist with hiring, performance, pay, credit, eligibility or similar decisions only via tools approved as High-tier for that purpose, with the required notices, bias testing and a human reviewer who can change the outcome. Ask HR/Legal first.
- **Be transparent.** Customers and the public are told when they interact with AI. Content generated with AI and published externally is labelled where the law or our contracts require; public communications get human editorial sign-off. Internally, note when significant work (documents, code, analysis) is AI-assisted so reviewers can apply the right scrutiny.
- **Respect rights.** Don't upload material we don't have rights to use. Don't generate content using real people's likeness or voice without consent. Don't use AI to monitor colleagues.
- **Client and customer terms.** Some contracts restrict AI use or require disclosure — check with {{Legal / account owner}} before using client data or delivering AI-assisted work.
- **Prompts are records.** Assume anything you type may be retained, reviewed in an investigation, or requested by a customer or regulator.

## 5. Never

- Enter secrets, credentials, payment card numbers, or Restricted data into any AI tool outside an approved exception.
- Use AI to create deceptive, harassing, discriminatory, sexual or violent content, deepfakes, or malware.
- Bypass Company controls (VPN tricks, personal devices, disabled logging, jailbreaks) to use AI.
- Let AI make or communicate a commitment (legal, financial, contractual, regulatory) on the Company's behalf without human sign-off.
- Build, connect or run an AI agent or automation that acts on systems, money, or people without approval under the AI Agent Standard.
- Present AI output as your own where authorship matters (regulatory filings, court documents, academic or professional attestations, client deliverables that require it).

## 6. Agents and automations

If you want an AI to *do* things — send emails, update records, issue refunds, run code, open pull requests, post publicly, call other tools — that's an AI agent. Before it runs against real systems or real people it needs: a registered owner, its own login (not yours), a list of exactly what it may touch, limits, a way to stop it, logs, and approval by {{AI Governance Lead / Committee}} under the AI Agent Standard. Low-risk experiments in a sandbox with test data are fine — tell {{channel}} so they're in the register.

## 7. How this is enforced

- Approved tools are behind Company single sign-on; unapproved AI services are {{blocked / monitored}} on Company networks and devices.
- {{Data-loss prevention}} flags Restricted data in prompts.
- Company AI tenants have vendor training on our data switched off contractually.
- Agents run through {{gateway}} that enforces allowlists and caps and logs every action.
- Breaches are handled under the {{Disciplinary Policy}}. Deliberately putting Restricted data into an unapproved tool, bypassing controls, or running an unapproved agent is serious misconduct.

## 8. Questions and reporting

- Not sure? Ask {{AI Governance channel / email}} — answering within {{1 business day}}.
- Something went wrong (wrong data pasted, an agent did something unexpected, harmful output reached a customer)? Report immediately to {{incident channel}}. Good-faith reports are protected.
- Want a tool approved or an exception? {{Request form / link}}.

## 9. Acknowledgement

I have read and will follow the AI Acceptable Use Standard. Name · Date · {{Signature / LMS attestation}}

<!-- Framework tags for the coverage matrix (remove before delivery):
§2–3 [NIST MAP 4.1, GOVERN 6.1 · ISO 42001 A.7.2, A.9.2, A.10.3 · GDPR Art. 28]
§4 human oversight [NIST MANAGE 4.1 · ISO 42001 A.9.2 · GDPR Art. 22 · CCPA ADMT · CO SB 26-189]
§4 transparency [EU AI Act Art. 50 · Utah AI Policy Act · NIST MEASURE 2.8 · ISO 42001 A.8.2]
§5 prohibited [EU AI Act Art. 5 · TX TRAIGA · ISO 42001 A.9.2]
§6 agents [IMDA MGF D1–D3 · OWASP ASI02, ASI03 · NIST MANAGE 2.4]
§7 enforcement [NIST GOVERN 1.4 · ISO 42001 A.9.2]
§8 reporting [ISO 42001 A.3.3 · NIST GOVERN 4.3]
§9 training/acknowledgement [EU AI Act Art. 4 · NIST GOVERN 2.2 · ISO 42001 Cl. 7.3] -->
