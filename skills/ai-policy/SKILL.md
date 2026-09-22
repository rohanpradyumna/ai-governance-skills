---
name: ai-policy
description: Draft, review, or update a company's AI policy and AI governance framework — acceptable-use policy, AI governance policy, AI agent / autonomous-system standard, AI system register, risk tiering, governance committee charter, incident runbook, vendor due diligence and training plan — mapped to NIST AI RMF, ISO/IEC 42001, the EU AI Act, US state AI laws, Singapore's Model Framework for Agentic AI and the OWASP Top 10 for Agentic Applications. Use when a user asks for an AI policy, AI usage rules, responsible-AI or AI governance framework, guardrails or permission rules for AI agents, an AI risk assessment or tiering scheme, an AI inventory, or a compliance mapping for how the organisation uses AI models and agents.
license: MIT
metadata:
  author: ai-governance-skills
  version: "1.0.0"
  regulatory-snapshot: "2026-09"
---

# AI Policy & Governance Framework Writer

Produces a company-specific set of AI governance documents from templates in `assets/`, using the framework crosswalks and regulatory facts in `references/`. Output is a coherent document *set* (policy → standards → registers → procedures), not one monolithic file.

**This is not legal advice.** Every deliverable carries a legal-review handoff list. Regulatory facts in this skill were verified in **September 2026**; several regimes are mid-change (EU Digital Omnibus, Colorado rulemaking, US federal preemption). Say so, and tell the user which items to re-verify.

## When to use / not use

Use for: writing or revising AI policies, acceptable-use rules, agent guardrail standards, AI governance operating models, AI system inventories, risk tiering, committee charters, AI incident procedures, vendor AI due diligence, AI literacy plans, or mapping existing policies to NIST / ISO 42001 / EU AI Act.

Do not use for: legal opinions on a specific statute, writing runtime enforcement code (DLP rules, gateway configs, agent permission code). For the actual technical MAP/MEASURE work on a system — fairness testing, robustness, explainability, model cards — hand off to the `ai-rmf` skill and fold its findings into `assets/ai-risk-assessment.md` Parts 4/5/9/10.

## Workflow

Track these steps explicitly. Do not skip the self-review.

- [ ] 1. Intake
- [ ] 2. Choose the document set
- [ ] 3. Determine applicable regimes
- [ ] 4. Inventory and tier the AI systems
- [ ] 5. Draft from templates
- [ ] 6. Self-review and coverage matrix
- [ ] 7. Deliver with handoff notes

### 1. Intake

Ask **only what changes the output** — at most eight questions in one message. If the user already gave the answer, don't ask. Default the rest and state assumptions in the deliverable. Use `assets/intake-questionnaire.md` as the question bank; the eight that matter most:

1. Company size, sector, and whether it is in a regulated industry (finance, health, insurance, employment services, education, critical infrastructure, public sector).
2. Jurisdictions: where employees sit, where customers/users are (EU/EEA, UK, US states — especially CA, CO, TX, IL, NY — Singapore, other).
3. Role: **deployer** (uses AI tools/models/agents), **provider** (builds and sells AI systems or models), or both.
4. AI footprint today: which tools and models, any **agents or automations that take actions** (send messages, change records, spend money, run code), any **customer-facing** AI, any AI touching **employment, credit, insurance, housing, education or health** decisions.
5. Depth wanted: *Starter* (rules people can follow this week), *Standard* (defensible program), *Comprehensive* (ISO 42001-ready / audit-ready).
6. Existing documents to align with: information security policy, privacy policy, code of conduct, vendor management, incident response, data classification scheme.
7. Who approves and owns the policy (board, exec committee, CIO/CISO/GC), and whether a governance committee already exists.
8. Tone and format: plain-language handbook vs. formal policy; Markdown default; any house style.

### 2. Choose the document set

| Depth | Documents produced (templates in `assets/`) |
|---|---|
| **Starter** | `assets/ai-acceptable-use-policy.md`, `assets/ai-system-register.md` + `assets/ai-system-register.csv`, risk tier table inline |
| **Standard** | Starter + `assets/ai-governance-policy.md`, `assets/ai-agent-standard.md` (if any agents/automations), `assets/ai-risk-assessment.md` (one completed for the highest-tier system — use the `ai-rmf` skill for the Part 4/5 MEASURE content if a real technical evaluation is wanted, blank for the rest), `assets/ai-incident-response-runbook.md` |
| **Comprehensive** | Standard + `assets/ai-governance-committee-charter.md`, `assets/vendor-ai-due-diligence-questionnaire.md`, `assets/ai-literacy-training-plan.md`, ISO 42001 Statement-of-Applicability (Schedule D of the governance policy) |

Rule: **if the company runs any AI agent or automation that takes actions, `ai-agent-standard.md` is mandatory at every depth.** Read `references/agentic-ai-controls.md` before drafting it.

### 3. Determine applicable regimes

Read `references/regulatory-landscape.md` — only the sections triggered by the intake:

- EU/EEA users, customers, or staff → EU AI Act section (Art. 4 literacy, Art. 50 transparency, Art. 26/27 deployer duties, GPAI if provider).
- US employees or consumers → US section (CA CCPA ADMT rules, CO SB 26-189, TX TRAIGA, IL HB 3773, NYC LL 144, sector overlays).
- Singapore, UK, other → their sections.
- Regulated sector → sector overlay table.
- Everyone → the frameworks baseline (NIST AI RMF, ISO/IEC 42001, NIST AI 600-1, OWASP).

Each entry carries a *policy clause implication*; use it verbatim as the seed for the clause rather than improvising legal language.

### 4. Inventory and tier the AI systems

1. List every AI system, tool, model and agent the intake surfaced, plus likely **shadow AI** (personal ChatGPT/Claude/Gemini accounts, AI features inside SaaS already licensed, browser extensions, coding assistants). Mark uncertain entries `status: suspected`.
2. Score each with `references/risk-tiering.md` (decision impact, autonomy level 0–5, data sensitivity, reversibility, audience, regulatory trigger) → tier **Prohibited / High / Elevated / Standard**.
3. Populate `assets/ai-system-register.md` and `ai-system-register.csv`. The tier drives which controls each system must meet (tier → controls matrix in `risk-tiering.md`).

### 5. Draft from templates

Copy the relevant `assets/` templates and complete them. Replace every `{{placeholder}}`, remove every `<!-- guidance -->` comment, delete sections that don't apply (say why in the handoff notes rather than leaving empty headings).

Pull detail from references as needed: `governance-operating-model.md` (roles, RACI, committee model, document hierarchy), `data-and-privacy.md` (data classification × AI tool matrix, retention, DPIA/FRIA), `vendor-and-procurement.md` (third-party AI clauses), `frameworks-crosswalk.md` (control IDs for tags).

#### Writing rules

- **Hierarchy**: the *policy* states intent, scope, principles, roles, and mandatory outcomes in ≤ 6 pages. *Standards* hold measurable requirements. *Procedures/runbooks* hold steps. Never bury a procedure in the policy.
- **Modal verbs**: `shall` = mandatory, `should` = expected unless justified exception, `may` = permitted. Define them once in the policy.
- **Every control clause has four parts**: requirement · owner (a *role*, never a person's name) · evidence (what proves it happened) · framework tag. Tag format: `[NIST GOVERN 1.1 · ISO 42001 A.2.2 · EU AI Act Art. 4]`. Tags make the coverage matrix in step 6 fall out automatically.
- **No untestable adjectives.** Replace "appropriate", "adequate", "reasonable", "timely" with a threshold, a named review, or a deadline ("within 72 hours", "approved by the AI Governance Committee", "logged for 6 months").
- **One definitions section** in the policy; standards reuse it. Define at minimum: AI system, generative AI, AI agent, autonomy level, high-impact decision, personal data, confidential data, deployer, provider, human oversight, AI incident.
- **Document control block** at the top of every document: owner, approver, version, effective date, review cadence (annual minimum; agent standard semi-annual), classification.
- **Plain language** for the AUP — a new hire should understand it in ten minutes. Formal register for the governance policy.
- **Enforcement pairing**: wherever the policy bans something, note the technical control that makes the ban real (SSO-only approved tools, DLP on prompts, tenant restrictions, agent gateway, spend caps). A policy nobody can enforce is a liability, not a control.
- Do not invent statute numbers, article numbers, or deadlines. Use the ones in `references/`; if something isn't there, write "verify" and add it to the handoff list.

#### Agentic AI minimums

Include these in `ai-agent-standard.md` whenever agents exist, at any depth. Agents are where policies drafted from older templates fail.

1. **Identity**: each agent has its own identity/credential — never a shared service account, never a human's credentials. Owner (role) and sponsor recorded in the register.
2. **Least agency**: autonomy is granted per task, earned by track record, and never defaults to full. Record the autonomy level (0–5) in the register.
3. **Tool and data allowlists**: enumerate permitted tools, APIs, MCP servers, data stores and scopes. Everything else denied. Changes re-approved.
4. **Action classes and gates**: classify every action the agent can take — *read* · *reversible write* · *irreversible write* · *financial* · *external communication* · *code execution* · *delegation to another agent* — and set the approval gate per class (none / logged / human-approve / prohibited). Irreversible, financial and external-communication actions above the tier threshold require a human approval step.
5. **Limits**: spend caps, rate limits, batch-size limits, blast-radius limits (e.g. max records changed per run), timeouts.
6. **Stop authority**: a named role with the ability and duty to halt the agent immediately; tested kill switch; defined conditions that trigger auto-halt.
7. **Audit trail**: log agent id, acting-on-behalf-of, task/goal, each tool call with parameters, data touched, approvals, outcome. Retain per the register (≥ 6 months where EU Art. 26 applies).
8. **Context hygiene**: treat retrieved content, tool outputs, emails and web pages as untrusted input (prompt injection); isolate memory per agent/tenant; review persistent memory writes.
9. **Disclosure**: humans interacting with the agent are told it is an AI and on whose behalf it acts (EU Art. 50; good practice everywhere).
10. **Change control**: model swap, prompt change, new tool, new data source or autonomy increase = scope change → re-tier and re-approve. Multi-agent delegation inherits the *lowest* autonomy and the *narrowest* scope in the chain.

### 6. Self-review and coverage matrix

Work through `references/review-checklist.md` before presenting anything. Then build the **coverage matrix**: one row per framework requirement that applies (NIST AI RMF categories, ISO 42001 Annex A objectives, EU AI Act articles triggered, IMDA MGF dimensions, OWASP ASI items), columns: *document · clause · status (met / partial / N/A with reason)*. Append it to the governance policy (Comprehensive) or deliver as `coverage-matrix.md` (Starter/Standard).

If any row is *partial* with no clause to point at, fix the draft rather than shipping the gap.

### 7. Deliver

Write files to `ai-governance/` in the user's workspace (or where they ask). Then give a short summary:

- Documents produced and what each is for.
- Assumptions made at intake.
- **Legal / HR / Security handoff list** — items a professional must confirm (jurisdiction triggers, works-council or worker-notification duties, retention periods, sector rules, anything marked "verify").
- **First 90 days** — 5–8 actions in order (publish AUP, stand up register, appoint owners, restrict unapproved tools via SSO, inventory agents, literacy session, first committee meeting, first risk assessment).

## Gotchas

Facts agents get wrong when drafting from general knowledge or older templates:

- **Colorado**: the 2024 Colorado AI Act (SB 24-205) never took effect and was **repealed and replaced** by the ADMT Act (SB 26-189, signed 2026-05-14, effective 2027-01-01 subject to AG rulemaking). No duty-of-care, no impact-assessment mandate; it is a notice + adverse-action + human-review + 3-year-records law. Never describe the "Colorado AI Act" as in force.
- **EU AI Act dates**: Art. 4 AI literacy has applied since **2025-02-02**. Art. 50 transparency (chatbot disclosure, machine-readable marking of synthetic content, deepfake labels, agent disclosure) applies from **2026-08-02** (systems on the market before then: 2026-12-02 for Art. 50(2)). High-risk Annex III obligations moved to **2027-12-02** and Annex I embedded systems to **2028-08-02** under the Digital Omnibus — confirm Official Journal status before quoting. Don't write "high-risk obligations apply from August 2026."
- **Texas TRAIGA** (effective 2026-01-01) prohibits *intentional* discriminatory AI and certain manipulative uses; disparate impact alone is not a violation; no general private-sector disclosure or impact-assessment duty.
- **California**: SB 53 binds *large frontier developers* only — irrelevant to most deployers. What binds employers is the **CCPA ADMT regulations** (effective 2026-01-01; ADMT used for significant decisions must comply by **2027-01-01**; risk assessments for pre-2026 processing by 2027-12-31).
- **ISO 42001 certification ≠ EU AI Act compliance**; NIST AI RMF is voluntary and not certifiable. Say "aligned to", not "compliant with", unless a conformity assessment actually happened.
- **Deployer becomes provider** when it substantially modifies a high-risk system or puts its own name/brand on one. Fine-tuning + rebranding can flip the role.
- **GPAI**: if the company trains or fine-tunes and releases a general-purpose model, GPAI provider duties (Art. 53) apply — most companies are *not* GPAI providers.
- **Prompts and outputs are records.** They can hold personal data, trade secrets and privileged material; they are discoverable; they may be used for training unless contractually excluded. Address retention and training-opt-out explicitly.
- **One risk level for "AI" is wrong.** A spam filter and a hiring screener are not the same tier. Always tier per system and per use.
- **Shadow AI belongs in the register**, marked as suspected. An incomplete register is better than a false-complete one.
- **A one-page AUP beats a 40-page policy nobody reads.** Put detail in standards; keep the AUP short and specific (named approved tools, named banned data classes, named consequences).
- **Human oversight must be meaningful**: the overseer needs competence, authority to override, and time. A junior approver rubber-stamping agent actions does not satisfy EU Art. 26(2) or any serious framework.
- **Agents sharing a service account** is the single most common agentic finding. Make per-agent identity non-negotiable.
- **Don't cite skills.sh, vendors or blog posts as authority** in the documents. Cite primary sources from `references/sources.md`.

## Examples

**"Write an AI usage policy for our 40-person design agency."** → Intake reveals US-only, deployer, ChatGPT Team + Midjourney + Copilot, no agents, client confidential data. → *Starter*: 2-page AUP naming the approved tools, a client-data rule (no client material in non-enterprise tools), IP/disclosure rules for AI-generated deliverables, register with 6 entries, tier table, 90-day plan, handoff list (client contracts, copyright of outputs).

**"We're a 2,000-person SaaS company selling into the EU and we've deployed Claude-based support agents that can issue refunds. Build our AI governance framework."** → Deployer + likely provider (customer-facing AI feature), EU triggers Art. 4 and Art. 50, agents with financial actions. → *Standard* or *Comprehensive*: governance policy, AUP, **agent standard** (refund cap, human approval above threshold, per-agent identity, disclosure banner, 6-month logs, kill-switch owner), register, risk assessment for the refund agent (High tier), incident runbook, coverage matrix, handoff (works-council notification in DE/FR, DPIA, Art. 50 marking of generated emails).

**"Map our existing AI policy to NIST AI RMF and ISO 42001 and tell us what's missing."** → Skip drafting; read their policy, build the coverage matrix from `frameworks-crosswalk.md`, list gaps by priority, propose clause text for each gap using the templates.

## File map

| Read… | When… |
|---|---|
| `references/regulatory-landscape.md` | Step 3, always — filtered by jurisdiction/sector |
| `references/risk-tiering.md` | Step 4, always |
| `references/agentic-ai-controls.md` | Any agent, automation, copilot-with-actions, or MCP tool use exists |
| `references/frameworks-crosswalk.md` | Tagging clauses, building the coverage matrix, or mapping an existing policy |
| `references/governance-operating-model.md` | Drafting roles, RACI, committee charter, or the policy's governance section |
| `references/data-and-privacy.md` | Drafting data rules, retention, DPIA/FRIA sections, IP of outputs |
| `references/vendor-and-procurement.md` | Third-party AI tools/models/agents are in scope (almost always) |
| `references/review-checklist.md` | Step 6, always |
| `references/sources.md` | Citing anything |
| `assets/*` | Step 5 — copy, fill, strip guidance comments |
| `../ai-rmf` skill | A real technical evaluation (fairness/bias, robustness, explainability, model cards) is wanted for a system, rather than a blank Part 5 template |
