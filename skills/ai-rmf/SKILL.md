---
name: ai-rmf
description: "Perform a technical NIST AI Risk Management Framework (AI RMF 1.0) assessment of an AI/ML system — MAP the context, MEASURE fairness, robustness, explainability, privacy and accuracy, and MANAGE the resulting risks. Use when a user needs to actually evaluate an AI system's behaviour (bias testing, drift, explainability, model cards, fairness metrics, robustness/adversarial testing) rather than draft governance documents. Use when the user mentions 'AI risk assessment,' 'NIST AI RMF,' 'model risk management,' 'AI fairness,' 'AI bias,' 'algorithmic accountability,' 'model card,' 'AI evaluation,' 'model drift,' or needs to MAP/MEASURE/MANAGE a specific AI or ML system. Companion to the ai-policy skill, which drafts the governance documents this skill's findings feed into."
license: MIT
metadata:
  author: ai-governance-skills
  version: "1.0.0"
---

# AI RMF — Technical MAP / MEASURE / MANAGE Assessment

This skill does the **technical evaluation** work of the NIST AI RMF: given a specific AI/ML system, it MAPs the context, MEASURES it against fairness/bias/robustness/explainability/privacy/accuracy criteria, and turns the findings into a MANAGE treatment plan. It is the engineering counterpart to [`ai-policy`](../ai-policy/SKILL.md), which drafts the governance policy set (AUP, agent standard, charters, regulatory mapping) that this skill's findings feed into.

**Division of labour** — do not duplicate the other skill's job:

| | `ai-rmf` (this skill) | `ai-policy` |
|---|---|---|
| Produces | Per-system technical risk findings (fairness metrics, robustness results, explainability artefacts) | Governance documents (policy, standards, register, charters, vendor DDQ, training plan) |
| Regulatory facts | None — defers entirely | Owns `references/regulatory-landscape.md`, the single source of truth |
| Risk tiering scale | Uses `ai-policy`'s `references/risk-tiering.md` dimensions (A–G) — never invents a second scale | Defines the scale |
| Output lands in | `ai-policy`'s `assets/ai-risk-assessment.md` Parts 4, 5, 9, 10 | The full governance document set |

## When to use / not use

Use for: assessing a specific AI/ML system's fairness, bias, robustness, explainability, privacy or accuracy; building or reviewing a model card; running the MAP/MEASURE/MANAGE loop; explaining what "good" looks like for a fairness or robustness evaluation.

Do not use for: drafting AI policy, acceptable-use rules, agent standards, committee charters, vendor questionnaires or literacy plans (use `ai-policy`); making regulatory-scope determinations (use `ai-policy`'s regulatory-landscape reference, confirmed by counsel); prompt-injection or agent-security penetration testing (run your organization's security review process and bring the results into the Security row of Step 3 below).

## The NIST AI RMF — four functions

| Function | What it covers |
|---|---|
| **Govern (GOV)** | Policy, accountability, roles, risk appetite — *drafted by `ai-policy`; this skill only checks whether the practice actually exists for the system under review* |
| **Map (MAP)** | Context — what the AI system is, what it does, who is impacted, what could go wrong |
| **Measure (MEAS)** | Evaluate the system — fairness, robustness, accuracy, explainability, privacy, security; quantitative + qualitative |
| **Manage (MAN)** | Treat the risks — mitigations, monitoring, incident response, decommissioning |

Voluntary but increasingly cited in contracts, RFPs and regulation — treat it as the lingua franca of AI risk.

## Workflow

### Step 1 — Identify the system(s) in scope

If the user hasn't already inventoried their AI systems in `ai-policy`'s `assets/ai-system-register.md`, start there — don't build a second, competing inventory. Otherwise, confirm which system(s) this assessment covers and pull its entry (vendor, training data, deployment context, affected population) from the register.

### Step 2 — MAP: assess the context

- **Purpose** — what is the system's stated goal? Does actual deployment match?
- **Stakeholders** — who interacts with it, who is affected by its decisions, who can challenge a decision?
- **Failure modes** — what does "broken" look like? (wrong answer, biased answer, hallucinated answer, slow/expensive answer, wrongly refused, wrongly answered)
- **Reversibility** — when this system makes a wrong call, can the decision be undone?
- **Tier** — score the system using `ai-policy`'s `references/risk-tiering.md` dimensions (decision impact, autonomy, data sensitivity, reversibility, audience, regulatory trigger, provenance uncertainty). Don't re-derive a tier here; if one already exists in the register, use it.

### Step 3 — MEASURE: evaluate the system

#### Accuracy / performance

- Test-set evaluation on held-out data, not training data.
- Performance **per slice**, not just aggregate — a system that's 95% accurate overall may be far worse on the demographic most affected by it.
- Confusion matrices for classification; quantile-based error analysis for regression.
- For LLMs: task-specific evals (HELM, MMLU, TruthfulQA) — and especially custom evals built on the application's own real prompts.

#### Fairness / bias

- **Demographic parity** — similar outcomes across protected classes?
- **Equalized odds** — similar false-positive / false-negative rates across groups?
- **Calibration** — when the system says "80% likely," is that actually ~80% across every group?
- **Individual fairness** — do similar inputs produce similar outputs?

These metrics trade off against each other — you cannot maximize all of them at once. Step 2 should have already decided which matters most for this use case (e.g. equalized odds for hiring; the choice for lending depends on whose interests dominate — flag this as a decision for the system owner, not a default this skill picks).

**Tooling**: Fairlearn (Microsoft), AI Fairness 360 (IBM), What-If Tool (Google), Aequitas (University of Chicago).

#### Robustness

- Adversarial inputs — perturbations that flip predictions (Foolbox, ART for traditional ML).
- Distribution shift — does the model degrade as the input distribution changes? (it will, eventually)
- Stress testing with extreme-but-plausible inputs.
- For LLMs: output stability across paraphrased prompts. Jailbreak and prompt-injection resistance are a distinct security discipline — run that testing separately and bring the results in as a Security finding rather than re-deriving them here.

#### Explainability / transparency

- **Local explanations** — why did the model make *this* decision? (SHAP, LIME, integrated gradients)
- **Global explanations** — what features matter overall?
- **Model card** — intended use, performance metrics, training data, limitations, ethical considerations (Google's pattern; use the Model Card Toolkit).
- **System card** — the longer-form version for an LLM-integrated pipeline, not just the model.

A model that can't be explained at all is a model that can't be defended in a regulatory inquiry. For high-impact decisions (Part 2 tier = High), explainability is not optional.

#### Privacy

- Does the model leak training data? (membership-inference, training-data-extraction attacks for LLMs)
- Are PII-bearing inputs/outputs appropriately scoped and redacted before training or logging?

#### Security (input only — do not perform this testing here)

Bring in the output of your organization's own AI/prompt-injection security review (jailbreaks, indirect injection, agent privilege boundaries, tool misuse) as a single summarized finding. If no such review exists yet, flag that as a gap in the MANAGE plan rather than attempting the testing inside this skill.

### Step 4 — MANAGE: treat the risks

| Risk | Treatment options |
|---|---|
| Bias against a protected class | Retrain with balanced data; add a fairness constraint to the training objective; pre/post-processing corrections; remove the feature; remove the application |
| Hallucination on factual queries | Retrieval-augmented generation; citation requirements; a fact-checking step; user warning |
| Drift over time | Monitoring; scheduled retraining; champion–challenger deployment |
| Adversarial robustness gaps | Adversarial training; input validation; rate limiting on probing patterns |
| Lack of explainability for high-stakes decisions | Switch to an interpretable model class; add post-hoc explanation; add human-in-the-loop |
| Third-party model with insufficient transparency | Vendor risk review; contractual guarantees on training data; consider a self-hosted alternative |
| PII leakage potential | Differential privacy in training; PII redaction in prompts; output filtering |

For each risk: give it an owner (a role, not a person's name), a due date, and a disposition — **Fixed** (control implemented and verified) / **Deferred** (planned, with a date) / **Accepted risk** (documented rationale and sign-off). High-tier systems need both an engineering and a system-owner sign-off on any accepted risk; anything touching a protected-class decision needs legal/ethics sign-off too.

### Step 5 — GOVERN: check, don't draft

This skill checks whether the supporting governance practice exists for the system under review — it does not write the practice. If any of these is missing, say so as a MANAGE-plan gap and point the user at `ai-policy`:

- AI principles documented and approved → `ai-policy` `assets/ai-governance-policy.md`
- Approval gate exists for high-impact deployments → `ai-policy` `references/governance-operating-model.md`
- Model card / system card in place → produced in Step 3 above
- AI incident response defined → `ai-policy` `assets/ai-incident-response-runbook.md`
- Decommissioning plan exists → note the end-of-life owner and trigger conditions

## Using this alongside `ai-policy`

- Findings from Step 3 (MEASURE) populate `ai-policy`'s `assets/ai-risk-assessment.md` **Part 4** (risk identification) and **Part 5** (evaluation plan and results).
- The MANAGE plan from Step 4 populates **Part 9** (risk treatment and residual risk); the monitoring metrics/thresholds populate **Part 10**.
- If `ai-policy` isn't in use and the user just wants a standalone technical write-up, use the lighter output format below instead of the full template.
- Never restate a regulatory fact (EU AI Act tiers, US state law, sector rules) inside output from this skill — cite `ai-policy`'s `references/regulatory-landscape.md`. That file is the maintained, dated source; duplicating facts here is how the two documents drift out of sync.

## Standalone output format

Use only when `ai-policy`'s `ai-risk-assessment.md` template isn't in play.

```markdown
# AI Risk Assessment (Technical) — [System name]
## Framework: NIST AI RMF 1.0
## Date / Assessor:

### MAP — context summary
[purpose, stakeholders, failure modes, reversibility, tier]

### MEASURE findings
| Category | Method | Finding | Severity |
|---|---|---|---|
| Accuracy | | | |
| Fairness | | | |
| Robustness | | | |
| Explainability | | | |
| Privacy | | | |
| Security (external input) | | | |

### MANAGE plan
| Risk | Treatment | Owner | Due | Disposition |
|------|-----------|-------|-----|--------------|

### Governance gaps (route to ai-policy)
- [ ] ...
```

## Boundaries

- This skill produces technical risk findings and evaluation methodology — not the final compliance posture. For high-stakes regulated AI (medical devices, autonomous systems, hiring AI subject to local audit laws), regulatory determinations are made with counsel.
- Refuse to help build AI systems that fall into the EU AI Act prohibited list, that violate civil-rights law (disparate impact in protected-class decisions), or that surveil individuals without lawful basis.
- Refuse to help build systems designed to evade transparency/disclosure requirements (undisclosed bots, deepfakes meant to deceive in regulated contexts).
- Frontier-model alignment/catastrophic-risk research is out of scope — this skill is enterprise-deployment risk management, not AI safety research.

## References

- **NIST AI RMF 1.0** + **Generative AI Profile** — foundational
- **NIST AI 100-1, 100-2** — companion documents
- **ISO/IEC 42001** (AI management system) and **ISO/IEC 23894** (AI risk management)
- **Fairlearn**, **AI Fairness 360**, **What-If Tool**, **Aequitas** — fairness evaluation tooling
- **HELM**, **MMLU**, **TruthfulQA** — LLM evaluation benchmarks
- **Google Model Card Toolkit** — model/system card format
- **MIT AI Risk Repository** — academic-curated risk catalogue
- **Stanford CRFM Foundation Model Transparency Index** — comparative transparency assessment
- For regulatory sources (EU AI Act, US state/federal, sector law), see `ai-policy`'s `references/sources.md` — do not cite regulation from this skill directly.
