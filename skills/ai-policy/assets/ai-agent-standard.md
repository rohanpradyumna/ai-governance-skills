# {{Company}} AI Agent Standard

<!-- Mandatory whenever any AI takes actions. Built from references/agentic-ai-controls.md. Fill caps and cadences with real numbers; flag them as adjustable in the handoff. Remove guidance comments. -->

| Document control | |
|---|---|
| Owner | {{AI Governance Lead}} · Technical co-owner: {{Security Lead}} |
| Approver | {{AI Governance Committee}} |
| Version / effective | {{1.0}} / {{YYYY-MM-DD}} · Review: semi-annual and after any agent incident |
| Parent | AI Governance Policy §7.7 · Definitions §3 · Risk tiers Schedule A |
| Related | AI Acceptable Use Standard · AI System Register · AI Risk Assessment Procedure · AI Incident Response Runbook · {{Identity & Access Management Standard}} · {{Secure Development Standard}} · {{Logging Standard}} |

## 1. Purpose and scope

1.1 This Standard sets mandatory requirements for **AI agents**: AI systems that pursue goals by taking actions — invoking tools, APIs, MCP servers or connectors; reading or writing data; executing code; communicating with people or other agents — with limited or no step-by-step human direction. `[IMDA MGF D1 · OWASP ASI · NIST MANAGE 2.4]`

1.2 In scope: agents the Company builds; agents configured on vendor platforms; AI features in licensed software that can take actions (auto-send, auto-update, auto-approve); LLM-driven automations and workflows; browser- or computer-using agents; coding agents; multi-agent systems; third-party agents operating in Company systems or on the Company's behalf. Copilots that only draft for a human to send are autonomy level 0–1 and need §4 registration and §11 disclosure only. <!-- adjust -->

1.3 Autonomy levels, action classes and tier gates in this Standard use the definitions in Annex 1.

## 2. Principles

**Least agency** — autonomy is granted per task at the lowest level that works, earned by evidence, never a default. **Bounded by design** — what an agent *can* do is limited technically, not just by instructions. **A human is always accountable** — every agent has a named owner with stop authority. **Everything is logged** — which agent did what, under whose authority, with what result. `[IMDA D1–D3 · ASI02, ASI03, ASI10]`

## 3. Roles

| Role | Responsibility |
|---|---|
| **Agent Owner** ({{manager}}+ for Elevated/High) | Accountable for scope, autonomy, limits, compliance with this Standard, register accuracy, re-approval on change |
| **Agent Operator** | Runs and monitors the agent; exercises the kill switch; reviews samples and alerts |
| **Principal** | The person/unit on whose behalf the agent acts; recorded per agent and per session where delegated |
| **Human Approver** | For gated actions; must meet the meaningful-oversight test (§7.4) |
| **Security Lead** | Identity, allowlists, logging, threat model, incident response |
| **AI Governance Lead / Committee** | Approvals per tier (Schedule A) |

`[NIST GOVERN 2.1, 3.2 · ISO 42001 A.3.2 · IMDA D2]`

## 4. Registration and approval

4.1 No agent shall act on production systems, real data or real people before it is recorded in the AI System Register with the agent fields in Annex 2 and approved per its risk tier. `[NIST GOVERN 1.6 · ISO 42001 A.6.2.5]`

4.2 The approval package shall state: goal and principal; autonomy level; tool allowlist; data allowlist; action classes enabled and gates; quantitative limits; environments; oversight design and approvers; kill-switch owner; logging location; disclosure design; evaluation results (§9); rollback and decommission plan; vendor terms (if third-party). `[IMDA D1 · NIST MAP 1–3]`

4.3 Approval authority: **High** — AI Governance Committee; **Elevated** — AI Governance Lead with Security concurrence; **Standard** — Agent Owner, registered. Any agent with financial, irreversible-write or external-communication actions above the gates in Annex 1, or autonomy ≥ 3, is at least Elevated; consequential decisions about people are High.

## 5. Identity and access

5.1 Each agent shall have its own identity (workload identity, service principal or dedicated API credential) registered to its Agent Owner. Shared service accounts, human credentials and hard-coded secrets are prohibited. `[ASI03 · IMDA D3 · NIST GOVERN 1.3]`

5.2 Permissions shall be the minimum tools, methods, data scopes, environments and actions needed for the approved goal. Standing administrative or wildcard roles are prohibited. Permissions are reviewed at each re-approval and at least {{quarterly}} for High. `[ASI03 · ISO 42001 A.9.2]`

5.3 Credentials shall be short-lived, rotated automatically, stored in {{secrets manager}}, and revoked within {{1 hour}} of decommission or incident. `[{{IAM Standard}} cross-ref]`

5.4 Where an agent acts for a human, every downstream call shall carry the on-behalf-of identity so logs show which agent acted under whose authority. Agents shall not exceed their principal's own permissions. `[IMDA D2/D3 · ASI03]`

5.5 Agent-to-agent calls shall be mutually authenticated and authorised; messages validated against schemas; no implicit trust between agents. `[ASI07]`

## 6. Scope bounding

6.1 **Tool allowlist.** Agents may invoke only enumerated tools, MCP servers, APIs and methods with parameter constraints, held in version control and enforced at {{gateway / runtime}}. Dynamic discovery or installation of tools is prohibited without Committee approval; MCP servers and plugins are version-pinned and sourced from {{approved registry}}. `[ASI02, ASI04 · IMDA D1]`

6.2 **Data allowlist.** Enumerated stores, collections, tenants and classification ceilings, split read/write; field-level where the platform allows. Restricted data is out of scope for agents unless a Committee exception with Privacy/Legal sign-off exists. `[ISO 42001 A.7 · NIST MAP 1.6]`

6.3 **Environments.** Production, staging and sandbox are declared per agent. Code and command execution occur only in ephemeral sandboxes without production credentials and with egress restricted to allowlisted destinations. `[ASI05]`

6.4 **Quantitative limits** per agent, enforced technically with hard stop and alert on breach (defaults; tune per agent):

| Limit | Standard | Elevated | High |
|---|---|---|---|
| Spend per action / per day | {{$50 / $500}} | {{$200 / $2,000}} | Per-action approval above {{$X}}; dual control above {{$Y}} |
| Records modified per run | {{50}} | {{200}} with dry-run first | {{20}} without approval |
| External messages per day | {{25}} | {{100}} | Human approval per message or per campaign |
| Tool calls per task / runtime per task | {{100 / 15 min}} | {{300 / 30 min}} | {{Defined per agent}} |
| Sub-agent spawns | 0 | {{3}}, allowlisted | Approval per delegation path |

`[ASI08, LLM10 · IMDA D1]`

6.5 **Prohibited actions** (all tiers, enforced technically): creating or modifying identities, roles or permissions; changing security controls or logging; deleting or altering audit records; modifying own instructions, tools or memory policy; contacting regulators, press or courts; making legal, contractual or regulatory commitments; accessing Restricted data outside an exception; operating at autonomy level 5. `[ASI10 · AI Governance Policy §5.1(i)–(j)]`

## 7. Human oversight and stop authority

7.1 **Action gates** per Annex 1 shall be enforced in the execution path (gateway/orchestrator), not merely requested in the prompt. Approvals record approver identity, timestamp and rationale. `[EU AI Act Art. 14, 26(2) · NIST GOVERN 3.2 · IMDA D2]`

7.2 **Kill switch.** The Agent Operator and {{Security on-call}} shall be able to halt any agent within {{15 minutes}} without vendor involvement. The kill switch is tested at deployment, after each scope change and at least {{quarterly}}; tests are logged. `[IMDA D3 · ASI10 · NIST MANAGE 2.4]`

7.3 **Auto-halt** shall trigger on: limit breach; anomalous tool-call patterns; {{N}} consecutive failures; detected prompt injection or policy violation; confidence below {{threshold}} on gated actions; loss of logging; human request. Restart requires Agent Owner review (Elevated/High: AI Governance Lead). `[ASI08]`

7.4 **Meaningful oversight.** Human approvers shall have: competence (trained on the agent's task and failure modes), information (evidence and reasoning, not just a recommendation), authority (may override or halt without escalation), time (approvals per hour monitored; ceiling {{X}}), and accountability (named in the register). Approval interfaces for High-tier agents shall not default to one-click accept. `[EU AI Act Art. 26(2) · IMDA D2 · ASI09]`

7.5 **Sampling review.** For autonomy ≥ 3, the Agent Operator reviews {{5% or ≥ 20}} actions per week for correctness and compliance; findings feed §10. `[NIST MEASURE 2.4]`

7.6 **Consequential decisions** about people are never executed by an agent without human review meeting §7.4 and a route for the person to contest and receive reasons. `[GDPR Art. 22 · CCPA ADMT · CO SB 26-189 · EU AI Act Annex III]`

## 8. Inputs, memory and context integrity

8.1 All content an agent ingests other than its approved instructions — documents, web pages, emails, tickets, tool outputs, other agents' messages — is untrusted data and never instructions. Defences (instruction/data separation, input filtering, output validation, spotlighting) are documented in the threat model and tested (§9). `[ASI01 · LLM01]`

8.2 Memory and vector stores are segregated per agent and per tenant/customer; persistent memory writes are validated and reviewable; memory is purgeable on request, incident or decommission. `[ASI06 · LLM08]`

8.3 Instructions and system prompts are version-controlled and reviewed before change; they contain no secrets and are not treated as a security boundary. `[LLM07]`

8.4 Retrieval sources are allowlisted and integrity-monitored. `[ASI06]`

8.5 Outputs to be executed (code, SQL, shell, API payloads) are schema-validated against the allowlist before execution. `[ASI02, ASI05]`

## 9. Evaluation before go-live and after change

9.1 Before production and after any scope change, the Technical Owner shall evaluate and document: task success on a representative set; harmful-output refusal; prompt-injection resistance including **indirect injection via retrieved content and tool outputs**; tool-misuse and parameter-tampering tests; enforcement of every limit in §6.4; gate enforcement in §7.1; kill-switch and auto-halt; logging completeness (§10); disclosure behaviour (§11). High tier: independent review of results. `[NIST MEASURE 2.1–2.7 · ISO 42001 A.6.2.4 · ASI01–02]`

9.2 Rollout is staged: sandbox → pilot with named users and reduced limits for at least {{2 weeks}} → production with monitoring; a rollback plan exists. `[NIST MANAGE 4.1]`

## 10. Logging, monitoring and change control

10.1 Every action shall be logged centrally and tamper-evidently with at least: timestamp; agent id and version (model, instruction version, tool-set hash); principal / on-behalf-of; session or task id; goal summary; tool name; parameters (redacted per data class); target resource; action class; autonomy level; gate applied; approver id; result; data classes touched; cost; anomaly flags. Agents cannot alter or delete their logs. `[ISO 42001 A.6.2.8 · EU AI Act Art. 12, 26(6) · IMDA D3 · NIST MEASURE 2.4]`

10.2 Retention: {{12}} months default; at least 6 months for agents in scope of EU AI Act Art. 26; longer where sector rules apply; reasoning traces retained for High. Logs support individual-rights and adverse-action disclosure requests. `[EU AI Act Art. 26(6) · CCPA ADMT · CO SB 26-189]`

10.3 Monitoring and alerting for goal drift, tool-call anomalies, out-of-scope credential use, memory anomalies, inter-agent message spikes, cost spikes and limit approaches. `[ASI01–08]`

10.4 **Scope change = re-approval.** Model swap or version change, instruction change, new tool or data source, autonomy increase, new principal or tenant, new environment, or vendor-pushed model update shall trigger re-tiering, re-evaluation (§9) and re-approval (§4). `[ISO 42001 A.6.2.6 · EU AI Act Art. 25 · ASI04]`

10.5 **Multi-agent systems** shall document the delegation graph; each hop inherits the narrowest scope and lowest autonomy in the chain; orchestrators cannot escalate sub-agent permissions; one human Agent Owner is accountable for the system as a whole. `[ASI07, ASI08 · IMDA May 2026]`

10.6 **Third-party agents** (vendor-hosted, marketplace, partner) shall meet this Standard by contract, be bounded and logged within Company systems as if Company-built, and be subject to model/tool change-notice clauses. `[ISO 42001 A.10.3 · IMDA May 2026]`

10.7 **Decommissioning**: credentials revoked, memory purged or archived per retention, register updated, dependants notified. `[ISO 42001 A.6.2.6 · NIST GOVERN 1.7]`

## 11. Transparency

11.1 People interacting with an agent shall be told at first contact that it is an AI and **on whose behalf it acts**, and again at key steps (authorisation, reporting, validation) in multi-agent or long-running interactions, unless obvious to a reasonably informed person. Standard text: "{{You're chatting with {{Company}}'s AI assistant, acting for {{team}}. A person can take over at any time — just ask.}}" `[EU AI Act Art. 50(1) and 2026 guidelines · Utah AI Policy Act · FTC Act §5 · IMDA D4]`

11.2 Agent-generated content sent externally is identifiable as AI-generated where law or contract requires; public communications drafted by agents receive human editorial sign-off. `[EU AI Act Art. 50(2), 50(4)]`

11.3 Affected persons can reach a human, contest an agent's decision and obtain the principal reasons and data used. `[GDPR Art. 22 · CCPA ADMT · CO SB 26-189]`

11.4 Internally, agent-generated artefacts (messages, ticket updates, commits, PRs, documents) are attributed to the agent so reviewers apply appropriate scrutiny. `[IMDA D4]`

## 12. Incidents

Agent-specific incident triggers: unauthorised or out-of-scope action; limit breach; data exposure; successful injection; action beyond the principal's authority; harmful external communication; runaway cost; kill-switch failure; behavioural regression after a vendor model change. Response per the AI Incident Response Runbook: halt → revoke credentials → preserve logs and traces → assess harm and notification duties → root cause → re-approval before restart. `[NIST MANAGE 4.3 · ISO 42001 A.8.4 · EU AI Act Art. 26(5), 73]`

## Annex 1 — Autonomy levels, action classes and default gates

<!-- Paste from references/agentic-ai-controls.md §2 and §3; adjust thresholds. -->

**Autonomy:** 0 Advisory · 1 Assisted (approve each action) · 2 Supervised (reversible actions autonomous; rest queued) · 3 Bounded autonomous (within enforced envelope; sampling review) · 4 Delegating (may instruct other agents) · 5 Open-ended (**prohibited**).

| Action class | Standard | Elevated | High |
|---|---|---|---|
| Read (allowlisted) | Log | Log | Log + scope review |
| Reversible write | Log | Log | Log + sampling |
| Irreversible write | Approve | Approve | Approve by named oversight role |
| Financial | Cap + log; approve above cap | Approve above lower cap | Approve each; dual control above threshold |
| External communication | Log + disclosure | Approve first N / sampling | Approve |
| Code / command execution | Sandbox only | Sandbox + review | Prohibited outside sandbox |
| Identity / access change | Prohibited | Prohibited | Prohibited |
| Delegation | Log; inherit scope | Approve new targets | Approve each path |
| Self-modification | Prohibited | Prohibited | Prohibited |

## Annex 2 — Agent fields in the AI System Register

autonomy level · principal · Agent Owner · Agent Operator · tool allowlist ref · data allowlist ref · action classes enabled · limits (spend/day, records/run, messages/day, sub-agents) · environments · kill-switch owner and last test date · auto-halt conditions ref · disclosure implemented (Y/N + text ref) · delegation targets · memory scope · evaluation report ref · logging location and retention · last scope change · vendor/platform and change-notice clause ref.

## Revision history

| Version | Date | Author (role) | Change |
|---|---|---|---|
| {{1.0}} | {{date}} | {{AI Governance Lead}} | Initial issue |
