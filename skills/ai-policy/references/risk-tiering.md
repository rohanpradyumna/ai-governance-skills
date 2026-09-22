# Risk tiering for AI systems

**Read this when:** classifying the company's AI systems, tools, models and agents (SKILL.md step 4), or writing the tiering section of the governance policy. The tier decides which controls apply; one undifferentiated "AI risk" level is the most common template failure.

Aligned to: EU AI Act risk classes (prohibited / high / limited / minimal), NIST AI RMF MAP function, ISO/IEC 42001 A.5 (impact assessment) and ISO/IEC 42005, IMDA agentic framework (autonomy, data access, tool scope as bounding factors). Tier by **use case in context**, not by model sophistication — a spreadsheet formula in a hiring decision outranks a frontier model summarising public news.

---

## 1. Tiers

| Tier | Meaning | Who approves | Default review cadence |
|---|---|---|---|
| **P — Prohibited** | Uses the company will not permit, by law or by choice | Nobody; exceptions only via committee + legal, documented | — |
| **T1 — High** | Consequential effects on people, safety, money, legal position or the company's licence to operate; or autonomous action with material blast radius; or a legal high-risk classification | AI Governance Committee (or board delegate) | Quarterly monitoring review; annual full re-assessment |
| **T2 — Elevated** | Material but bounded effects; customer-facing; confidential data; supervised autonomy | AI Governance Lead + system owner's executive | Semi-annual |
| **T3 — Standard** | Internal productivity, reversible, low-sensitivity data, human-in-the-loop | System owner; recorded in register | Annual, via register attestation |

Some organisations want a fifth "Minimal / no-register" bucket for embedded AI features (spell-check, photo enhancement). Default: **everything AI goes in the register**, but T3 entries need only the minimal fields.

## 2. Scoring dimensions

Score each dimension 0–3. Use the highest-scoring dimension **and** the total, per §3.

| Dimension | 0 | 1 | 2 | 3 |
|---|---|---|---|---|
| **A. Decision impact on people** | No effect on any person's rights, opportunities or wellbeing | Minor, easily reversed inconvenience | Affects service quality, price offered, or content a person sees; influences a human decision | **Materially influences or makes** a consequential decision: employment, credit, insurance, housing, education, health, legal/benefits eligibility, safety |
| **B. Autonomy** (see `agentic-ai-controls.md` §2) | Level 0 advisory | Level 1 assisted (approve each action) | Level 2 supervised | Level 3–5 bounded-autonomous or higher; or any irreversible/financial/external action without per-action approval |
| **C. Data sensitivity** | Public / synthetic | Internal non-sensitive | Confidential business data or personal data | Special-category / sensitive personal data (health, biometrics, children, financial account, protected traits), trade secrets, privileged material, or data under regulatory regime (HIPAA, PCI, GLBA, export control) |
| **D. Reversibility & blast radius** | Output reviewed before any use; nothing changes | Changes limited to one record/user and trivially undone | Bulk or multi-system changes, or external artefacts already sent, recoverable with effort | Irreversible, safety-relevant, or affects many people/systems at once (production, money movement, public statements) |
| **E. Audience & exposure** | Single internal user, own work | Internal team | Customers, partners, employees as subjects, or public content | Vulnerable groups, minors, patients, the general public at scale, or regulators/courts |
| **F. Regulatory / contractual trigger** | None | Contract clauses on AI use exist | Notice/disclosure duties apply (Art. 50, Utah, state chatbot rules, NYC LL144 notice) | Legal **high-risk** or ADMT classification (EU Annex III; CCPA ADMT significant decision; CO SB 26-189 consequential decision; IL HB 3773; sector model-risk rules) |
| **G. Model & provenance uncertainty** | Established vendor, enterprise terms, no training on inputs, documented evals | Vendor with consumer terms or unclear data use | Open-weight / self-hosted / fine-tuned without independent eval | Unknown provenance, unvetted marketplace agent/plugin, or shadow tool |

## 3. Tier decision rule

1. **Prohibited check first** (§4). If it matches → P. Stop.
2. **Any dimension = 3 in A, B, D or F** → **T1 High**.
3. Else **total ≥ 11** or any two dimensions = 3 → **T1 High**.
4. Else **any dimension = 2**, or total 6–10 → **T2 Elevated**.
5. Else → **T3 Standard**.
6. **Overrides**: the AI Governance Lead may raise a tier for reputational, ethical or strategic reasons (record why); may never lower below the legal-trigger floor (F = 3 → at least T1).

Re-tier on any scope change (new data, new users, new autonomy, new jurisdiction, new model), on incident, and at the cadence in §1.

## 4. Prohibited uses (default list — trim/extend at intake)

Legal (EU Art. 5, TRAIGA, BIPA, sector law):
- Manipulative or deceptive techniques that distort behaviour and cause harm; exploiting vulnerabilities of age, disability or economic situation.
- Social scoring of people leading to detrimental treatment.
- Emotion recognition or biometric categorisation of employees, candidates or students (except medical/safety with legal sign-off).
- Untargeted scraping of facial images; biometric identification without lawful basis and legal review.
- Generating sexual deepfakes, non-consensual intimate imagery, CSAM, or content inciting self-harm or crime.
- AI developed or used with intent to discriminate on protected characteristics.

Company policy (typical):
- Solely automated consequential decisions about people without meaningful human review.
- Entering restricted data (see `data-and-privacy.md` matrix) into any tool not on the approved list for that classification.
- Impersonating a human when asked, or presenting AI output as human-authored where disclosure is required (customers, public, regulators, courts).
- Covert monitoring of employees' communications or productivity via AI beyond what employment law and the monitoring policy allow.
- Autonomy Level 5, self-modifying agents, agents changing identities/permissions, agents deleting audit logs.
- Using AI to make or communicate legal, regulatory or financial commitments on behalf of the company without human sign-off.
- Training or fine-tuning models on customer data without contractual right and privacy review.
- Circumventing safety features, rate limits, or content controls of AI tools.

## 5. Tier → required controls matrix

✔ = required · ○ = recommended · — = not required. Control names map to the templates; tags to `frameworks-crosswalk.md`.

| Control | T3 Standard | T2 Elevated | T1 High |
|---|---|---|---|
| Register entry (minimal fields) | ✔ | ✔ | ✔ (full fields) |
| Named system owner (role) | ✔ | ✔ | ✔ + executive sponsor |
| Approved-tool / approved-vendor check | ✔ | ✔ | ✔ |
| Data classification check against tool permission matrix | ✔ | ✔ | ✔ |
| Risk assessment (`ai-risk-assessment.md`) | Short form (self-attested) | Full form | Full form + independent review (2nd line / internal audit / external) |
| DPIA (where personal data) | If GDPR/UK GDPR triggers | ✔ | ✔ |
| FRIA (EU Art. 27 where applicable) | — | — | ✔ if in scope |
| Bias / fairness testing | — | If people-affecting | ✔ pre-deployment + at least annually; documented method and thresholds |
| Accuracy / performance evaluation before use | ○ | ✔ | ✔ with acceptance criteria and independent sign-off |
| Security review (OWASP LLM/ASI, threat model) | ○ | ✔ | ✔ + penetration/red-team incl. injection via retrieved content |
| Human oversight design (meaningful-oversight test) | User reviews output | Defined reviewer & sampling | Named oversight role with override authority; SLA; competence evidence |
| Transparency / disclosure to affected persons | Where law requires | ✔ | ✔ + individual notice & explanation/contest route |
| Logging & retention | Tool defaults | Action logs ≥ {{6}} months | Full logs & traces ≥ {{12}} months (≥ 6 legal min EU); tamper-evident |
| Monitoring & drift/performance metrics | — | Periodic | Continuous with thresholds & alerting |
| Incident procedure linkage | AUP reporting | ✔ | ✔ with regulator/customer notification analysis |
| Vendor due diligence (`vendor-ai-due-diligence-questionnaire.md`) | Standard procurement check | Full questionnaire | Full questionnaire + contract clauses + annual review |
| Change control / re-approval on scope change | Register update | Owner approval | Committee approval |
| Agent controls (`agentic-ai-controls.md`) | A-1, B-1, E-1 minimum if agent | §4 catalogue "Standard/Elevated" columns | Full catalogue, High column |
| Training for users / overseers | General AI literacy | Role-specific | Role-specific + oversight competence evidence |
| Approval authority | System owner | AI Governance Lead + executive | AI Governance Committee |
| Documentation retained | Register row | Assessment + approvals | Full file: assessment, evals, approvals, logs, notices, contracts, reviews |

## 6. Mapping to legal classes (put in register)

| Company tier | EU AI Act class | US ADMT laws | Notes |
|---|---|---|---|
| P | Prohibited (Art. 5) or company-prohibited | — | Record whether legal or elective |
| T1 | High-risk (Annex III / I) **or** company-High | CCPA ADMT "significant decision"; CO SB 26-189 "consequential decision"; IL HB 3773 employment; NYC LL144 AEDT | Legal high-risk is always T1; T1 is broader than legal high-risk |
| T2 | Limited (Art. 50) or minimal | Notice-only regimes (Utah, chatbot rules) | Customer-facing chatbots usually land here |
| T3 | Minimal | — | Art. 4 literacy still applies |

## 7. Worked examples

| System | A | B | C | D | E | F | G | Tier | Why |
|---|---|---|---|---|---|---|---|---|---|
| Copilot for internal docs, enterprise tenant, no training on data | 0 | 0 | 2 | 0 | 1 | 0 | 0 | T2 | C=2 (confidential data) |
| Meeting-note summariser, consumer free tier, personal account | 0 | 0 | 2 | 0 | 1 | 0 | 2 | T2 → often P | Shadow tool with training on inputs; typically banned for confidential data |
| Résumé screener ranking candidates | 3 | 1 | 2 | 1 | 2 | 3 | 1 | **T1** | A=3, F=3 (EU Annex III, NYC LL144, IL, CA ADMT) |
| Support agent that can issue refunds ≤ $200 autonomously | 1 | 3 | 2 | 2 | 2 | 2 | 0 | **T1** | B=3 (financial action without per-action approval) |
| Support chatbot, answers only, escalates to human | 1 | 0 | 2 | 0 | 2 | 2 | 0 | T2 | Art. 50 disclosure; no actions |
| Coding agent opening PRs (human merges), sandboxed | 0 | 1 | 2 | 1 | 1 | 0 | 0 | T2 | Merge gate keeps D low |
| Coding agent with prod deploy rights | 0 | 3 | 2 | 3 | 1 | 0 | 0 | **T1** | B=3, D=3 |
| Marketing image generator, human publishes | 0 | 0 | 0 | 1 | 2 | 2 | 0 | T2 | Art. 50(2)/(4) marking; brand risk |
| Fraud-scoring model auto-blocking transactions | 3 | 3 | 3 | 2 | 2 | 3 | 1 | **T1** | Financial-sector overlay; adverse action duties |
| Spam filter | 0 | 2 | 1 | 1 | 1 | 0 | 0 | T3 | Reversible, low impact |

## 8. Writing the tiering clause

Policy text pattern: "Every AI system shall be assigned a risk tier (Prohibited, High, Elevated, Standard) by its System Owner using the AI Risk Tiering Standard before use, recorded in the AI System Register, and re-assessed on any scope change and at least {{annually}}. Controls required for each tier are set out in Schedule {{X}}. Systems meeting a legal high-risk or automated-decision classification shall be tiered High regardless of score." Tags: `[NIST MAP 1.1, MAP 3.x, GOVERN 1.4 · ISO 42001 A.5.2–A.5.5, Clause 6.1 · EU AI Act Art. 6, Annex III · IMDA D1]`.
