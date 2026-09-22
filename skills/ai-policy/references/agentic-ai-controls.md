# Agentic AI controls

**Read this when:** the company runs (or plans) any AI that *acts* — agents, copilots with write access, workflow automations driven by an LLM, MCP tool use, RPA-with-LLM, multi-agent systems, or third-party agents operating in its environment. Drafting `assets/ai-agent-standard.md` without this file produces a chatbot policy with the word "agent" pasted in.

Sources synthesised: Singapore IMDA Model AI Governance Framework for Agentic AI (Jan/May 2026), OWASP Top 10 for Agentic Applications (2026), OWASP LLM Top 10 (2025), EU AI Act Art. 50 guidelines on agents (Jul 2026), NIST AI RMF / AI 600-1, practitioner consensus (MAIN business template 2026, Microsoft Agentic AI Maturity Model, CSA agentic NIST profile).

---

## 1. Definitions to put in the policy

| Term | Definition to use |
|---|---|
| **AI agent** | An AI system that pursues a goal by planning and executing a sequence of actions — calling tools, APIs, or other systems, reading and writing data, or communicating with people or other agents — with limited or no step-by-step human direction. |
| **Action** | Any operation an agent performs beyond returning text to the user who prompted it. |
| **Tool** | Any function, API, MCP server, connector, plugin, browser or shell capability an agent can invoke. |
| **Principal** | The person or organisational unit on whose behalf and under whose authority the agent acts. |
| **Agent owner** | The role accountable for the agent's scope, behaviour, and compliance with this Standard. |
| **Agent operator** | The role that runs, monitors and can halt the agent day-to-day. |
| **Autonomy level** | Per the scale in §2. |
| **Scope change** | Any change to an agent's model, system prompt/instructions, tools, data access, autonomy level, principal, or deployment environment. |

## 2. Autonomy scale (record in the register; drives the tier)

| Level | Name | Description | Typical gate |
|---|---|---|---|
| 0 | Advisory | Produces text/recommendations only; human performs every action | None beyond AUP |
| 1 | Assisted | Proposes concrete actions (drafts, diffs, transactions); human approves each one | Human approval per action |
| 2 | Supervised | Executes low-impact, reversible actions autonomously; queues everything else for approval | Approval for irreversible/financial/external |
| 3 | Bounded autonomous | Executes within a defined envelope (allowlisted tools, caps, environments) without per-action approval; human reviews logs/exceptions | Envelope enforced technically; sampling review |
| 4 | Delegating | Level 3 plus the ability to spawn or instruct other agents | Sub-agent inherits narrowest scope; delegation logged |
| 5 | Open-ended | Self-directed goal decomposition, dynamic tool acquisition, broad access | **Prohibited** by default; requires committee exception with compensating controls |

Rule: **least agency** — start at the lowest level that achieves the task; raise only with evidence (evaluation results, incident-free run history) and re-approval.

## 3. Action classes and default gates by tier

Classify every action an agent *can* take. The gate is the stricter of (row, tier column).

| Action class | Examples | Standard tier | Elevated tier | High tier |
|---|---|---|---|---|
| **Read** internal data within allowlist | Query CRM, read tickets, search docs | Log | Log | Log + data-scope review |
| **Reversible write** | Draft in CRM, create ticket, propose PR, stage email | Log | Log | Log + sampling review |
| **Irreversible write** | Delete/overwrite records, merge PR to prod, send bulk email, publish content, change pricing/config | Human approve | Human approve | Human approve by named oversight role |
| **Financial** | Refunds, payments, purchases, credits, quotes | Cap + log below cap; approve above | Approve above lower cap | Approve every action, dual control above threshold |
| **External communication** | Message a customer, post publicly, contact a vendor | Log + disclosure | Approve first N / sampling | Human approve |
| **Code / command execution** | Run scripts, shell, infra changes | Sandbox only | Sandbox + review | Prohibited outside sandbox |
| **Identity / access changes** | Create users, grant permissions, rotate keys | Prohibited | Prohibited | Prohibited (human-only) |
| **Delegation** | Call another agent, spawn sub-agent | Log; inherit scope | Approve new delegation targets | Approve each delegation path |
| **Self-modification** | Edit own instructions, add tools, change memory policy | Prohibited | Prohibited | Prohibited |

Consequential decisions about people (employment, credit, insurance, housing, education, health, legal status) are **never** executed by an agent without human review that meets the "meaningful oversight" test in §6, regardless of tier.

## 4. Control catalogue

Each control: requirement · owner · evidence · tags. Use in `ai-agent-standard.md`.

### 4.1 Identity and access

| # | Requirement | Evidence | Tags |
|---|---|---|---|
| A-1 | Each agent instance has its own identity (service principal / workload identity / API key) — never a shared account, never a human's credentials, never a hard-coded secret. Identity is registered in the AI system register with owner and principal. | IAM inventory reconciles to register | NIST GOVERN 1.3 · ISO A.3, A.9 · OWASP ASI03 · IMDA D3 |
| A-2 | Permissions are scoped to the minimum tools, data, environments and actions required for the approved task (least privilege) and the minimum autonomy (least agency). Standing broad roles (admin, owner, `*`) are prohibited. | Permission review record per agent | NIST MANAGE 1.3 · ISO A.9.2 · ASI03 |
| A-3 | Credentials are short-lived, rotated automatically, stored in a secrets manager, and revoked on decommission or incident. | Rotation logs | ISO 27001 cross-ref · ASI03 |
| A-4 | Agents acting on behalf of a human carry the "on-behalf-of" identity in every downstream call so audit trails show *which agent acted under whose authority*. | Log schema §4.5 | IMDA D2/D3 · ASI03 |
| A-5 | Agent-to-agent calls are authenticated and authorised; no implicit trust between agents; messages are validated and schema-checked. | Architecture review | ASI07 |

### 4.2 Scope bounding

| # | Requirement | Evidence | Tags |
|---|---|---|---|
| B-1 | **Tool allowlist**: the agent may invoke only enumerated tools/MCP servers/APIs with enumerated methods and parameter constraints; everything else is denied by default. Dynamic tool discovery/installation is prohibited unless committee-approved. | Allowlist config under version control | ASI02, ASI04 · IMDA D1 |
| B-2 | **Data allowlist**: enumerated data stores, collections, tenants and classification levels; read/write split. | Data access matrix | ISO A.7 · NIST MAP 1.6 |
| B-3 | **Environment bounding**: production vs. staging vs. sandbox declared; code execution only in ephemeral sandboxes with no production credentials and egress controls. | Environment diagram | ASI05 |
| B-4 | **Quantitative limits**: per-run and per-day caps on spend, transactions, records modified, messages sent, tokens/compute, tool calls, runtime; hard-stop on breach. | Limit config; breach alerts | ASI08, LLM10 · MAIN 2026 |
| B-5 | **Blast-radius limits**: batch operations capped (e.g. ≤ {{50}} records per run without approval); staged rollout for bulk actions; dry-run mode available. | Config; dry-run logs | ASI08 |
| B-6 | **Prohibited actions** list enforced technically (identity changes, self-modification, security-control changes, deleting logs, contacting regulators/press, legal commitments). | Policy-as-code rules | ASI10 |

### 4.3 Human oversight and stop authority

| # | Requirement | Evidence | Tags |
|---|---|---|---|
| C-1 | Every agent has a named **agent owner** (accountable) and **agent operator** (runs/halts) recorded in the register; owner is at least manager level for Elevated/High. | Register | NIST GOVERN 2.1 · ISO A.3.2 · IMDA D2 |
| C-2 | **Kill switch**: the operator (and security on-call) can halt the agent within {{15 minutes}} at any time; halting requires no vendor involvement; tested at least {{quarterly}} and after each scope change. | Test log | IMDA D3 · ASI10 |
| C-3 | **Auto-halt conditions** defined and implemented: cap breach, anomalous tool-call pattern, repeated failures, policy-violation detection, confidence below threshold, injection detection, human request. | Alert rules | ASI08 |
| C-4 | **Approval gates** per §3 are enforced in the execution path (not just requested in the prompt); approvers have competence, authority and time (see §6); approvals are logged with approver identity and rationale. | Gate config; approval logs | EU Art. 14/26 · NIST GOVERN 3.2 · IMDA D2 |
| C-5 | **Sampling review**: for autonomous actions (level ≥ 3), a defined sample ({{5%}} or ≥ {{20}}/week) is human-reviewed for correctness and policy compliance; findings feed change control. | Review records | NIST MEASURE 2.x |
| C-6 | Automation-bias countermeasures: approvers see the agent's reasoning/evidence, not just a recommendation; approval UIs avoid one-click defaults for High tier; approver workload monitored. | UI review; workload metrics | IMDA May 2026 update · ASI09 |

### 4.4 Input, memory and context integrity

| # | Requirement | Evidence | Tags |
|---|---|---|---|
| D-1 | All content the agent ingests from outside its instructions — documents, web pages, emails, tickets, tool outputs, other agents' messages — is treated as **untrusted data, never instructions**. Prompt-injection defences (input filtering, instruction/data separation, output validation, spotlighting) are documented. | Threat model; test results | ASI01 · LLM01 |
| D-2 | Agent memory (short- and long-term, vector stores) is segregated per agent and per tenant/customer; writes to persistent memory are validated and reviewable; memory can be purged. | Architecture; purge procedure | ASI06 · LLM08 |
| D-3 | System prompts/instructions are version-controlled, reviewed before change, and not treated as a security boundary (no secrets in prompts). | Repo history | LLM07 |
| D-4 | Retrieval sources are allowlisted and integrity-checked; poisoning of knowledge bases is monitored. | Source list; monitoring | ASI06 |
| D-5 | Outputs that will be executed (code, SQL, commands, API payloads) are validated against schemas/allowlists before execution. | Validation layer | ASI02, ASI05 |

### 4.5 Logging and auditability

Minimum log record for every agent action (retain ≥ {{12 months}}; ≥ 6 months mandatory where EU Art. 26 applies; longer for regulated sectors):

`timestamp · agent_id · agent_version (model, prompt version, tool set hash) · principal / on_behalf_of · session/task_id · goal or instruction summary · tool_name · parameters (redacted per data policy) · target resource · action_class · autonomy_level · gate_applied · approver_id (if any) · result/status · data_classes_touched · cost · anomaly_flags`

| # | Requirement | Evidence | Tags |
|---|---|---|---|
| E-1 | Logs above are captured centrally, tamper-evident, and searchable by agent, principal and target. Agents cannot modify or delete their own logs. | SIEM/observability config | NIST MEASURE 2.x · ISO A.6.2.8 · EU Art. 12/26 · IMDA D3 |
| E-2 | Reasoning traces / plans are retained for High-tier agents to support incident reconstruction. | Trace storage | ASI01 |
| E-3 | Anomaly detection on: goal drift, tool-call anomalies, credential use outside scope, memory anomalies, inter-agent message spikes, cost spikes. | Alert rules | ASI01–08 |
| E-4 | Logs support the individual-rights and disclosure obligations (which decision, which data, which reasoning) required by CCPA ADMT, CO SB 26-189, GDPR Art. 22. | Retrieval procedure | Regulatory |

### 4.6 Lifecycle and change control

| # | Requirement | Evidence | Tags |
|---|---|---|---|
| F-1 | **Pre-deployment approval**: agent proposal (goal, principal, tools, data, autonomy, action classes, limits, oversight, disclosure, evaluation results, rollback) reviewed by the AI Governance Committee or delegated approver per tier before production. | Approval record | NIST MAP · ISO A.6 · IMDA D1 |
| F-2 | **Evaluation before go-live and after change**: task success, safety refusals, injection resistance (red-team on retrieved content, not just user input), tool-misuse tests, cap enforcement tests, kill-switch test. | Eval report | NIST MEASURE · ASI01/02 |
| F-3 | **Scope change = re-approval**: model swap/upgrade, prompt change, new tool or data source, autonomy increase, new principal/tenant, new environment. Vendor-pushed model updates are tracked and evaluated. | Change log | ISO A.6.2.6 · ASI04 |
| F-4 | **Staged rollout**: sandbox → limited pilot (named users, low caps) → production with monitoring; rollback plan documented. | Rollout record | NIST MANAGE |
| F-5 | **Decommissioning**: credentials revoked, memory purged or archived per retention, register updated, dependants notified. | Checklist | ISO A.6.2.7 |
| F-6 | **Third-party agents** (vendor-hosted, marketplace, partner) meet this Standard by contract; their tool/data access in the company environment is bounded and logged the same way; vendor must disclose model/tool changes. | Contract clauses; access review | IMDA May 2026 · `vendor-and-procurement.md` |
| F-7 | **Multi-agent systems**: delegation graph documented; each hop inherits the narrowest scope and lowest autonomy; orchestrator cannot escalate sub-agent permissions; cross-agent messages authenticated; a single human owner for the system as a whole. | Architecture doc | ASI07, ASI08 · IMDA May 2026 |

### 4.7 Transparency to humans

| # | Requirement | Evidence | Tags |
|---|---|---|---|
| G-1 | People interacting with an agent are told it is AI and **on whose behalf it acts** (the principal), at first contact and at key steps (authorisation, reporting, validation) in multi-agent flows. Exception only where obvious to a reasonably informed person. | UI text; templates | EU Art. 50(1) + guidelines · Utah · FTC §5 |
| G-2 | Agent-generated content sent externally is identifiable as AI-generated where law or contract requires (Art. 50(2)/(4)); marketing/comms content gets human editorial sign-off. | Marking config; sign-off log | EU Art. 50 |
| G-3 | Affected persons can reach a human, contest an agent's decision, and obtain the reasons and data used (consequential decisions). | Escalation path | GDPR 22 · CCPA ADMT · CO SB 26-189 |
| G-4 | Internal users know when a colleague's message, ticket update or code change was agent-generated (attribution in the artefact). | Attribution convention | IMDA D4 |

### 4.8 Incident handling (link to `ai-incident-response-runbook.md`)

Agent-specific incident triggers: unauthorised action; cap breach; data exfiltration or exposure; injection success; agent acting outside principal's authority; harmful external communication; runaway cost; loss of kill-switch; vendor model change with behavioural regression. Response: halt → contain (revoke creds) → preserve logs/traces → assess impact & notifications (customers, regulators — EU serious-incident reporting for high-risk; data-breach clocks) → root cause → re-approval before restart.

## 5. OWASP ASI → control mapping (for the coverage matrix)

| OWASP ASI | Primary controls above |
|---|---|
| ASI01 Agent goal hijack | D-1, D-3, D-5, E-2, E-3, F-2 |
| ASI02 Tool misuse & exploitation | B-1, B-4, D-5, F-2 |
| ASI03 Identity & privilege abuse | A-1–A-5 |
| ASI04 Agentic supply chain | B-1 (no dynamic tools), F-3, F-6 |
| ASI05 Unexpected code execution | B-3, D-5 |
| ASI06 Memory & context poisoning | D-2, D-4 |
| ASI07 Insecure inter-agent communication | A-5, F-7 |
| ASI08 Cascading failures | B-4, B-5, C-3, F-7 |
| ASI09 Human-agent trust exploitation | C-6, G-1, G-4 |
| ASI10 Rogue agents | B-6, C-2, C-3, E-1 |

## 6. "Meaningful human oversight" test

Oversight counts only if the overseer has all five: **competence** (trained on what the agent does and fails at), **information** (sees evidence and reasoning, not just a recommendation), **authority** (can override or halt without escalation), **time** (workload allows real review — measure approvals per hour), **accountability** (named in the register; performance reviewed). Write these five into the standard; auditors and EU Art. 26(2) look for them.

## 7. Register fields specific to agents

Add to `ai-system-register`: autonomy level; principal; agent owner; agent operator; tool allowlist reference; data allowlist reference; action classes enabled; caps (spend/day, records/run, messages/day); kill-switch tested date; disclosure implemented (Y/N); delegation targets; memory scope; evaluation report reference; last scope change.

## 8. Gotchas

- "The model refuses to do X" is not a control. Controls live in the execution path: gateways, IAM, allowlists, caps.
- A copilot that can *only* draft but auto-sends after a timeout is Level 3, not Level 1.
- Browser-using agents can reach anything the logged-in human can; treat them as inheriting the human's full permissions unless a separate constrained profile is used.
- MCP servers are tools with supply-chain risk (ASI04): pin versions, review manifests, restrict to approved registries.
- Vendor agents embedded in SaaS (CRM/helpdesk "AI agents") are in scope even though the company didn't build them — register them, bound them, get change-notice clauses.
- Logging prompts verbatim may itself violate the data policy; redact per classification while keeping enough for reconstruction.
