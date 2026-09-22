# Third-party AI: vendors, models, agents

**Read this when:** the company uses any external AI tool, API, model, plugin, MCP server, marketplace agent, or AI feature embedded in licensed SaaS (nearly always). Feeds the vendor section of the governance policy, the Approved AI Tools register, and `assets/vendor-ai-due-diligence-questionnaire.md`.

Tags: `[NIST GOVERN 6.1, 6.2 · MAP 4.1, 4.2 · MANAGE 3.1, 3.2 · ISO 42001 A.10.2, A.10.3 · EU AI Act Art. 25 · IMDA D1 · OWASP ASI04]`

---

## 1. Tier the vendor relationship like the system

| Vendor tier | When | Diligence |
|---|---|---|
| **V1 Critical** | Powers a T1 system; processes Restricted data; agent with actions; provider of a model the company fine-tunes or resells; single point of failure | Full questionnaire + security attestation review + contract clauses §3 + annual review + exit plan |
| **V2 Significant** | Powers T2 systems; Confidential data; customer-facing | Full questionnaire + standard clauses + review every 2 years or on material change |
| **V3 Standard** | T3 productivity tools; Internal data only | Short questionnaire (data use, training, retention, SSO) + standard procurement |

Existing SaaS vendors switching on AI features: treat the feature as a **new AI system** — register it, tier it, check whether the existing contract's data terms cover model training and sub-processors. Default many vendors ship: AI features *on*, training *on*. Require opt-outs be set tenant-wide.

## 2. Due-diligence topics (→ questionnaire)

| Area | What to establish |
|---|---|
| **Role & regulatory** | Is the vendor a provider (EU AI Act), GPAI provider, or only infrastructure? Their conformity/compliance posture; whether the company's use makes it a provider (rebranding, substantial modification). EU Art. 53 downstream documentation for GPAI. |
| **Data use** | Training on inputs/outputs (default and contractual), retention periods, human review of prompts ("abuse monitoring"), sub-processors, hosting regions, residency options, deletion on termination, DSAR support. |
| **Security** | SOC 2 Type II / ISO 27001 / ISO 42001; pen-test summaries; encryption; tenant isolation; SSO/SCIM; admin controls; logging & export of logs; incident notification SLA; vulnerability disclosure; supply-chain of their own models/tools. |
| **Model** | Which models, versions, hosting (first-party, OpenAI/Anthropic/Google via API, open-weight); change-notice for model updates; evaluation results (accuracy, safety, bias) for the intended use; known limitations; system prompt/guardrail controls exposed to the customer; content provenance/marking support (Art. 50(2)). |
| **Agent capabilities** | What actions it can take; whether tools/connectors are customer-configurable and allowlistable; per-agent identity support; approval gates; caps; kill switch; action logs with parameters; memory scope and purge; inter-agent comms; prompt-injection defences and test evidence. |
| **Transparency & explainability** | Disclosure features (AI banners), explanation outputs sufficient for adverse-action reasons; documentation quality (model cards, instructions for use — Art. 13 if high-risk). |
| **Fairness** | Bias testing method and results; demographic coverage; support for the customer's own bias audits (NYC LL144 needs independent audit data). |
| **IP** | Output ownership; indemnity for third-party IP claims (scope, caps); training-data provenance statement; licence for outputs. |
| **Business continuity** | Uptime SLAs; exit/portability (export prompts, fine-tunes, embeddings); fallback options; financial stability; concentration risk across the company's AI estate. |
| **Compliance support** | Willingness to sign DPA/BAA, EU SCCs; support for customer audits or reports; cooperation in incident and regulator inquiries. |

## 3. Contract clauses (priority order)

1. **No training / no secondary use** of customer inputs, outputs, embeddings or fine-tunes; explicit, not toggle-dependent.
2. **Retention & deletion**: stated retention; zero-retention option for Confidential+; deletion certificate on exit; no human review without notice.
3. **Data processing terms**: DPA with sub-processor list & change notice; SCCs/DPF; BAA where PHI; residency commitments where required.
4. **Security**: named standard (SOC 2 II/ISO 27001), annual evidence, breach notice ≤ 72 h (shorter for V1), cooperation, right to audit or to receive audit reports.
5. **Model & feature change notice**: advance notice (≥ 30 days V1) of model swaps, deprecations, material behaviour changes, new tools/connectors, default-setting changes; right to pin versions or opt out; behavioural-regression remediation.
6. **Agent controls** (where agents): customer-controlled allowlists, caps and kill switch; per-agent identity; complete action logs exportable; no autonomous actions outside the configured scope; vendor liability for actions outside scope.
7. **Transparency & documentation**: instructions for use, model documentation, evaluation summaries, Art. 13/53 documentation where applicable; content-marking capability.
8. **Compliance cooperation**: support for the customer's regulatory obligations (Art. 26 logs, ADMT notices, bias audits), regulator inquiries, incident reporting timelines (Art. 73).
9. **IP**: output assignment/licence; indemnity for infringement claims from outputs and from the vendor's training data; no restriction on the company's use of outputs beyond law.
10. **Liability**: caps proportionate to data and action risk; carve-outs for confidentiality, data protection, IP indemnity, wilful misconduct; for agents, liability for unauthorised actions.
11. **Subcontracting / model providers**: flow-down of terms to underlying model providers; disclosure of which.
12. **Termination & transition**: export of data, prompts, fine-tunes; transition assistance; survival of confidentiality and deletion.
13. **Acceptable-use alignment**: vendor's AUP doesn't block the company's lawful use; the company can enforce its own AUP via admin controls.
14. **Insurance**: cyber/tech E&O evidence for V1.

## 4. Approved AI Tools register (companion to the AI system register)

Columns: tool · vendor · approved classification ceiling (Public/Internal/Confidential/Restricted) · approved use cases · prohibited uses · enterprise tenant? (Y/N) · SSO enforced · training opt-out confirmed (how) · retention setting · DPA/BAA on file · sub-processors/hosting region · vendor tier · owner · review date · notes.

Publish the tool names and classification ceilings in the AUP; keep the rest in the register.

## 5. Provider-side additions (if the company sells AI)

If the company places AI systems or models on the market (product features, APIs, agents sold to customers):
- Maintain technical documentation, instructions for use, and (high-risk) QMS, conformity assessment and EU database registration; post-market monitoring and serious-incident reporting (Art. 72–73).
- Provide downstream customers what they need for *their* Art. 26 / ADMT duties: logs, explanation outputs, disclosure features, bias-audit support.
- Contract with customers on acceptable use, prohibited uses, human-oversight expectations and incident cooperation (ISO A.10.4).
- Track whether fine-tuning or rebranding third-party models makes the company the provider.

## 6. Gotchas

- "We don't train on your data" in a blog post is not a contract term. Check the order form / DPA / enterprise terms — consumer and free tiers usually do train.
- API access via a cloud marketplace (Bedrock/Vertex/Azure OpenAI) has different data terms than the model lab's own API; record which path is used.
- Browser extensions and "AI meeting assistants" that join calls are vendors too; they often record everyone, including third parties without consent.
- Open-weight models self-hosted remove vendor data risk but add the company's own provider-like responsibilities (evaluation, security, documentation).
- Marketplace agents/plugins/MCP servers: pin versions, review permissions and manifests, restrict to approved sources (ASI04).
