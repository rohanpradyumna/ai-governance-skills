# Regulatory landscape for company AI policies

**Read this when:** determining which legal regimes the company's AI use triggers (SKILL.md step 3). Read only the sections the intake activates.

**Snapshot date: 2026-09-22.** Rules marked ⚠ were mid-change at snapshot; tell the user to re-verify them against primary sources (`sources.md`) before adoption. Never state a date or article number that isn't in this file — write "verify" instead.

Every table row ends with a **Policy clause implication**: the requirement the company's documents must contain if the row applies. Use it as the seed for the clause.

---

## 0. Frameworks baseline (applies to everyone)

These are voluntary standards, not laws. Use them as the skeleton; layer law on top.

| Framework | What it is | Use in the policy set |
|---|---|---|
| **NIST AI RMF 1.0** (Jan 2023) + Playbook | Four functions: **GOVERN** (org-wide: 6 categories, 19 subcategories), **MAP** (context & risks per system), **MEASURE** (analyse/track), **MANAGE** (treat, respond, monitor). Seven trustworthiness characteristics: valid & reliable; safe; secure & resilient; accountable & transparent; explainable & interpretable; privacy-enhanced; fair with harmful bias managed. Being revised under the 2025 US AI Action Plan ⚠. | Structure of the governance policy (GOVERN) and the risk assessment (MAP/MEASURE/MANAGE). Tag clauses with subcategory IDs (`frameworks-crosswalk.md`). |
| **NIST AI 600-1** GenAI Profile (Jul 2024) | 12 GenAI risk areas: CBRN information; confabulation; dangerous/violent/hateful content; data privacy; environmental; harmful bias & homogenization; human-AI configuration; information integrity; information security; intellectual property; obscene/degrading content; value-chain & component integration. 200+ suggested actions. Increasingly cited in US federal procurement. | Risk taxonomy for the risk assessment template; AUP prohibited-use list. |
| **ISO/IEC 42001:2023** AI Management System | Certifiable. Clauses 4–10 (context, leadership, planning, support, operation, performance evaluation, improvement) + **Annex A**: 9 control objectives A.2–A.10, 38 controls (policy; internal organization; resources; impact assessment; lifecycle; data; information for interested parties; use; third-party relationships). Annex B = implementation guidance. Requires a **Statement of Applicability**. Clause 5.2 requires a top-management-approved AI policy. | The "Comprehensive" depth is ISO-ready: governance policy = Clause 5.2 policy; register = Clause 8 planning; committee = Clause 5 leadership; internal audit = 9.2 (independent of the AI function). |
| **ISO/IEC 23894:2023** | AI risk management guidance (extends ISO 31000). | Risk method wording. |
| **ISO/IEC 42005:2025** | AI system impact assessment. | Structure of `ai-risk-assessment.md` impact section. |
| **OECD AI Principles** (2019, rev. 2024); **Council of Europe Framework Convention on AI** (opened Sept 2024) | Principles: inclusive growth, human-centred values & fairness, transparency & explainability, robustness/security/safety, accountability. | Principles section of the governance policy. |
| **OWASP Top 10 for LLM Applications** (2025) | LLM01 prompt injection … LLM10 unbounded consumption; includes excessive agency (LLM06), system prompt leakage, vector/embedding weaknesses, misinformation. | Security requirements for GenAI systems. |
| **OWASP Top 10 for Agentic Applications** (Dec 2025, "2026" edition) | ASI01 goal hijack; ASI02 tool misuse; ASI03 identity & privilege abuse; ASI04 supply chain (dynamic tools/plugins); ASI05 unexpected code execution; ASI06 memory/context poisoning; ASI07 insecure inter-agent communication; ASI08 cascading failures; ASI09 human-agent trust exploitation; ASI10 rogue agents. Introduces **"least agency"**. | `ai-agent-standard.md` security controls (see `agentic-ai-controls.md`). |
| **Singapore IMDA Model AI Governance Framework for Agentic AI** (22 Jan 2026; updated 20 May 2026) | Four dimensions: (1) assess and **bound risks upfront** (autonomy level, data access, tool scope, environment), (2) **meaningful human accountability** across developers/deployers/operators/end-users, (3) **technical controls & processes** (identity, audit trail of which agent acted under whose authority, testing, monitoring), (4) **end-user responsibility**. May 2026 update adds multi-agent systems, third-party agents, automation bias. Voluntary but the only official agent-specific framework. | Structure of `ai-agent-standard.md`. |
| **MITRE ATLAS**; **CSA AI Controls Matrix** (2025) | Adversarial ML threat taxonomy; cloud-security-style control catalogue for AI. | Security standard references. |

---

## 1. European Union — AI Act (Regulation (EU) 2024/1689)

Applies to providers placing AI systems on the EU market and deployers established in the EU, **and** to providers/deployers outside the EU where the output is used in the EU. Role definitions (Art. 3): **provider** develops or has developed and places on market under own name; **deployer** uses under its authority in a professional context; also importer, distributor, product manufacturer.

### 1.1 Timeline

| Date | What applies | Status |
|---|---|---|
| 2024-08-01 | Entry into force | Done |
| 2025-02-02 | **Art. 5 prohibited practices**; **Art. 4 AI literacy** | In force |
| 2025-08-02 | **GPAI model obligations** (Ch. V, Art. 53–55); governance bodies; penalties regime | In force; Commission enforcement powers vs GPAI from 2026-08-02; GPAI models on market before 2025-08-02 must comply by 2027-08-02 |
| 2026-08-02 | **Art. 50 transparency obligations**; national regulatory sandboxes (Art. 57); most remaining provisions | In force. Commission guidelines on Art. 50 adopted 2026-07-20; voluntary Code of Practice on Transparency of AI-Generated Content available. Systems on the market before 2026-08-02 have until **2026-12-02** for Art. 50(2) marking. |
| 2026-12-02 | New Art. 5 prohibition: AI generating non-consensual intimate content and CSAM (added by Digital Omnibus) | ⚠ verify OJ publication |
| **2027-12-02** | **High-risk Annex III systems** (Art. 6(2)) — full Ch. III obligations incl. Art. 26 deployer duties, Art. 27 FRIA | ⚠ Moved from 2026-08-02 by the Digital Omnibus (Parliament approved 2026-06-16). Verify Official Journal status. |
| **2028-08-02** | High-risk Annex I systems (embedded in regulated products) | ⚠ Moved from 2027-08-02. Verify. |

### 1.2 Risk classes

| Class | Examples | Obligations |
|---|---|---|
| **Prohibited** (Art. 5) | Subliminal/manipulative techniques causing harm; exploiting vulnerabilities; social scoring; predictive policing on profiling alone; untargeted facial scraping; emotion recognition in workplace/education (except medical/safety); biometric categorisation inferring protected traits; real-time remote biometric ID in public for law enforcement (narrow exceptions) | Banned. Fines up to €35M / 7% global turnover. |
| **High-risk** (Art. 6, Annex III) | Biometrics; critical infrastructure; education & vocational training (admission, assessment, proctoring); **employment & workers management** (recruitment ads, screening, evaluation, promotion/termination, task allocation, monitoring); access to essential services (**credit scoring**, life/health insurance pricing, public benefits, emergency dispatch); law enforcement; migration; justice & democratic processes. Annex I: safety components in regulated products. | Providers: risk management (Art. 9), data governance (10), technical documentation (11), record-keeping (12), transparency to deployers (13), human oversight (14), accuracy/robustness/cybersecurity (15), QMS (17), conformity assessment, EU database registration (49). Deployers: **Art. 26** (below). Fines up to €15M / 3%. |
| **Limited / transparency** (Art. 50) | Chatbots, agents, emotion recognition, biometric categorisation, synthetic content, deepfakes | Disclosure & marking (below). |
| **Minimal** | Everything else (spam filters, most internal productivity uses) | No AI Act duties beyond Art. 4 literacy; voluntary codes. |
| **GPAI models** (Ch. V) | General-purpose models; systemic-risk models above 10^25 FLOPs training compute | Technical documentation, downstream information, copyright policy, training-content summary; systemic risk: evaluation, adversarial testing, incident reporting, cybersecurity. Most companies are **not** GPAI providers. |

### 1.3 Obligations most companies actually hit

| Article | Who | Requirement | Policy clause implication |
|---|---|---|---|
| **Art. 4 AI literacy** (in force since 2025-02-02) | All providers and deployers | Ensure, to their best extent, sufficient AI literacy of staff and others operating AI on their behalf, considering their role, context and the people affected. No specific level guaranteed; no certification required. | Governance policy shall require role-based AI literacy training for all staff using AI, with enhanced training for those exercising human oversight; training records retained. → `ai-literacy-training-plan.md`. |
| **Art. 50(1)** (from 2026-08-02) | Providers of systems interacting with people | Inform the person they are interacting with an AI system unless obvious. Commission guidelines extend to **AI agents**: disclose artificial nature **and** on whose behalf the agent acts; in multi-agent settings, disclose at key steps (authorisation, reporting, validation). | Every customer- or public-facing chatbot/agent shall display an AI disclosure and the principal it acts for. → agent standard §disclosure. |
| **Art. 50(2)** | Providers of GenAI systems | Mark synthetic audio/image/video/text outputs in machine-readable format and detectable as AI-generated (watermarks, metadata, C2PA-style provenance). Applies to companies offering GenAI features under their own brand, not just model labs. | If the company offers generative features to users, outputs shall carry machine-readable provenance marking; vendor contracts shall require marking capability. |
| **Art. 50(3)** | Deployers of emotion recognition / biometric categorisation | Inform exposed persons; process data per GDPR. | Prohibit in workplace/education (Art. 5); elsewhere require notice. |
| **Art. 50(4)** | Deployers | Disclose deepfakes (image/audio/video resembling real persons/places/events). Disclose AI-generated/manipulated **text published to inform the public on matters of public interest**, unless human editorial review with a person holding editorial responsibility. | Marketing/comms standard: label synthetic media; AI-drafted public communications require named human editorial sign-off. |
| **Art. 26 deployer duties** (high-risk; ⚠ 2027-12-02) | Deployers of high-risk systems | (1) Use per provider's instructions; (2) assign **human oversight** to persons with competence, training, authority and support; (3) ensure input data is relevant and representative where the deployer controls it; (4) monitor operation, inform provider/distributor and market surveillance authority of serious incidents, suspend use if risk; (5) **keep logs ≥ 6 months** where under deployer's control; (6) **inform workers' representatives and affected workers** before putting a high-risk system into use at the workplace; (7) public bodies register in EU database; (8) inform natural persons subject to decisions that a high-risk system is used; (9) use Art. 13 information to conduct a **DPIA**; (10) cooperate with authorities. Substantial modification or rebranding → deployer becomes **provider** (Art. 25). | For each High-tier system: named oversight role with override authority; monitoring & suspension procedure; log retention ≥ 6 months; worker notification procedure (HR); individual notice text; DPIA on file; change-control rule flagging provider-status flips. |
| **Art. 27 FRIA** (⚠ 2027-12-02) | Public bodies; private entities providing public services; deployers using high-risk AI for **credit scoring** or **life/health insurance risk assessment & pricing** | Fundamental rights impact assessment before first use: processes, period/frequency, affected persons/groups, specific risks, oversight measures, mitigations & complaint mechanism. Notify market surveillance authority using the AI Office template. Can be combined with the DPIA. | Risk assessment template includes FRIA fields; procedure to notify authority; re-assess on change. |
| **Art. 5** | Everyone | Prohibited practices above. | AUP and governance policy prohibited-uses list, including workplace emotion recognition. |
| **Art. 99 penalties** | — | €35M/7% (prohibitions); €15M/3% (most obligations, incl. Art. 50 and 26); €7.5M/1% (incorrect information). SME caps use the lower of the two. | Cite in the policy's "why this matters" preamble, not in clauses. |

### 1.4 Adjacent EU law

| Law | Relevance | Policy clause implication |
|---|---|---|
| **GDPR** | Personal data in prompts/outputs/training; Art. 22 automated decision-making with legal or similarly significant effects (right to human intervention, contest, explanation); Art. 35 DPIA for high-risk processing; Art. 13/14 transparency; Art. 28 processors (AI vendors); international transfers (US-hosted models). CJEU *SCHUFA* (Dec 2023): a score that "materially influences" a decision is itself an Art. 22 decision. | Data standard: lawful basis per AI use; DPIA trigger list; vendor DPAs; no solely-automated significant decisions without Art. 22 safeguards; DSAR handling covers AI-held data. |
| **Digital Services Act / DMA** | Platform recommender transparency, systemic risk for VLOPs. | Only if a platform. |
| **NIS2 / DORA / CRA** | Cyber-resilience for essential entities, financial entities (DORA ICT third-party risk incl. AI vendors), products with digital elements. | Security standard cross-reference; DORA register of ICT providers should include AI vendors. |
| **Product Liability Directive (2024/2853)** (applies from 2026-12-09) | Software and AI systems are "products"; strict liability for defects incl. from learning/updates. | Provider-side: documentation and update governance. ⚠ verify. |
| **Platform Work Directive (2024/2831)** (transpose by 2026-12-02) | Algorithmic management transparency and human review for platform workers. | Only if gig-platform. |
| **Copyright (DSM Directive Art. 4)** | Text-and-data-mining opt-out; GPAI copyright policy. | Provider-side training-data policy. |

---

## 2. United States

No comprehensive federal AI statute. Federal posture (⚠ volatile): **EO 14365** (2025-12-11) "Ensuring a National Policy Framework for AI" directs agencies to challenge burdensome state laws; DOJ **AI Litigation Task Force** established 2026-01-09; White House **National Policy Framework for AI** (2026-03-20) is non-binding legislative recommendations; no preemption statute enacted (Senate stripped the moratorium 99–1 in 2025). State laws remain in force unless a court says otherwise. DOJ intervened in *xAI v. Colorado* (stayed pending rulemaking).

### 2.1 Federal sector and general law that already reaches AI

| Regime | Requirement | Policy clause implication |
|---|---|---|
| **Title VII / ADA / ADEA (EEOC)** | Employer liable for discriminatory outcomes of AI hiring/promotion tools, including vendor tools; disparate impact theory applies under Title VII; ADA reasonable accommodation for AI assessments. (EEOC's 2023 technical guidance was withdrawn in 2025 ⚠, but statutes are unchanged.) | Employment AI standard: bias testing before use and annually; accommodation route; human review of adverse decisions; vendor contract requires validation data. |
| **FCRA / ECOA / Reg B (CFPB)** | Adverse action notices must state **specific principal reasons** even when a complex model is used (CFPB Circulars 2022-03, 2023-03); FCRA duties if AI outputs function as consumer reports; UDAAP. | Credit/lending AI: explainability sufficient for reason codes; model documentation; vendor as service provider oversight. |
| **FTC Act §5** | Deceptive AI capability claims ("AI washing"), unfair practices, algorithmic disgorgement remedies; Operation AI Comply (2024–). A 2026 FTC policy statement on AI accuracy suppression is **proposed, not final** ⚠. | Marketing standard: substantiate AI claims; no undisclosed AI in consumer interactions where material. |
| **SEC** | AI-washing enforcement; risk-factor and cybersecurity incident disclosure (Item 1.05 8-K) may cover AI incidents; proposed predictive-analytics conflicts rule withdrawn 2025. | Public companies: AI risk in disclosure controls; incident runbook feeds disclosure committee. |
| **HIPAA** | PHI in prompts → covered; BAAs with AI vendors; minimum necessary; de-identification standards. | Health data may only enter AI tools under a BAA; list them. |
| **GLBA / Safeguards Rule; SR 11-7 model risk management (Fed/OCC); NAIC Model Bulletin on AI (Dec 2023, adopted by 20+ states)** | Financial institutions: model inventory, validation, governance, third-party oversight; insurers: written AI program, governance, risk management, testing for unfair discrimination. | Financial/insurance overlays: model risk management standard incorporated by reference; AI systems register = model inventory. |
| **NYDFS 23 NYCRR 500** + Oct 2024 AI cybersecurity guidance; **Colorado Division of Insurance Reg. 10-1-1** (life insurers' external consumer data & algorithms) | Cyber risk assessments must consider AI-enabled threats and AI use; insurer governance and testing. | Sector overlay clauses. |
| **FDA** (SaMD, AI-enabled device guidance; PCCP) | AI in medical devices: premarket, predetermined change control plans. | Provider-side in medtech only. |
| **COPPA; FERPA** | Children's data; student records in AI tools. | Ed/consumer overlays. |
| **Copyright Office** (2025 reports) | Purely AI-generated output not copyrightable; human authorship required; fair-use training litigation ongoing ⚠. | IP standard: human creative contribution documented for deliverables; disclosure to clients where contractually required. |
| **OMB M-25-21 / M-25-22** (Apr 2025) | Federal agency AI use & acquisition: inventories, Chief AI Officers, high-impact AI risk practices. | Only if selling to US government: mirror in vendor questionnaire. |

### 2.2 State laws

| State / law | Status (2026-09) | Who / what | Key duties | Policy clause implication |
|---|---|---|---|---|
| **California — CCPA ADMT regulations** (CPPA, approved 2025-09-22) | Effective 2026-01-01. ADMT used for **significant decisions** must comply by **2027-01-01** (new ADMT: before first use). Risk assessments for covered processing since 2026-01-01 due by **2027-12-31**; attestations to CPPA from 2028-04-01. Cybersecurity audits phased 2028–2030 by revenue. | Businesses subject to CCPA (incl. as **employers** of CA workers). "Significant decision" = financial/lending, housing, education, **employment or independent-contracting opportunities or compensation**, healthcare. | **Pre-use notice**; **right to opt out** (with human-appeal alternative in some cases); right to access information about the ADMT logic and outcome; **risk assessment** before use; privacy-policy updates; vendor terms. Enforcement by CPPA/AG, $2,500/$7,500 per violation, no private right of action. | Employment & consumer AI standard: ADMT inventory flag; pre-use notice templates; opt-out/appeal workflow; risk assessment on file per ADMT. |
| **California — Civil Rights Council FEHA regulations on automated-decision systems** | Effective 2025-10-01 | Employers ≥ 5 employees | Liability for ADS with discriminatory effect; **4-year record retention** of ADS data; anti-bias testing as evidence of defence; vendor as agent. | Employment AI: bias testing, 4-year retention of selection data, vendor accountability. |
| **California SB 53** (Transparency in Frontier AI Act) | Effective 2026-01-01 | **Large frontier developers** (> $500M revenue, frontier compute) | Publish frontier AI framework, transparency reports, critical-incident reporting to OES, whistleblower protections. | Not applicable to deployers; mention only if the company trains frontier models. |
| **California AB 2013** | Effective 2026-01-01 | GenAI developers | Publish training-data summary. | Provider-side only. |
| **California SB 942** (AI Transparency Act) as delayed by AB 853 | Effective **2026-08-02** ⚠ | Covered GenAI providers (> 1M monthly users) | Free AI-detection tool; latent (and optional manifest) disclosures in outputs. | Provider-side; deployers should prefer vendors that comply. |
| **California SB 243** (companion chatbots) | Effective 2026-01-01 | Operators of companion chatbots | Disclosure, suicide-prevention protocols, minors safeguards, annual reporting from 2027. | Only if consumer companion products. |
| **Colorado — SB 26-189 ADMT Act** (repeals & replaces 2024 Colorado AI Act SB 24-205, which **never took effect**) | Signed 2026-05-14; effective **2027-01-01** subject to AG rulemaking (draft ADMT & Chatbot Safety Rules filed 2026-08-11; comments to 2026-10-26; AG says no enforcement until rules final) ⚠ | Developers, midstream developers, deployers of ADMT that **materially influences** consequential decisions (employment, education, finance, housing, insurance, health, legal, essential services) | **Notice** to individuals; **adverse-outcome disclosure** with reasons and data used; **meaningful human review** / appeal; **records for 3 years**; chatbot safety duties. Fault-based liability allocation; certain indemnities void. **No** general duty of care, impact-assessment or risk-program mandate (removed from the 2024 Act). AG-only enforcement. | Consequential-decision AI standard: notice text, adverse-action disclosure template, human review SLA, 3-year records. Do **not** cite "Colorado AI Act" duties of care or impact assessments. |
| **Texas — TRAIGA (HB 149)** | Effective 2026-01-01; AG complaint portal live by 2026-09-01; 60-day cure period; no enforcement actions reported as of mid-2026 | Anyone doing business in or serving Texans | Prohibits AI developed/deployed **with intent** to unlawfully discriminate (disparate impact alone is not a violation), to incite self-harm/crime, to produce CSAM/sexual deepfakes; government social scoring and biometric ID limits; **healthcare providers must disclose AI use to patients**; government agencies must disclose. Regulatory sandbox. | AUP prohibited uses; healthcare overlay disclosure. Don't describe TRAIGA as requiring impact assessments or general disclosure. |
| **Illinois — HB 3773** (Human Rights Act amendment) | Effective 2026-01-01 | Employers | Unlawful to use AI that has a **discriminatory effect** on protected classes in recruitment, hiring, promotion, discipline, discharge, terms; **notice** to employees/applicants of AI use; zip code may not be used as proxy. IDHR rules ⚠. | Employment AI: notice + bias testing (effects-based, unlike TRAIGA). |
| **Illinois — AI Video Interview Act** (2020) | In force | Employers using AI on video interviews | Notice, explanation, consent, deletion within 30 days on request, demographic reporting if AI decides who gets in-person interviews. | Recruiting standard. |
| **Illinois — BIPA** | In force | Biometric data | Written consent, retention schedule; private right of action (per-person after 2024 amendment). | Prohibit biometric AI without legal review. |
| **New York City — Local Law 144** | In force since 2023-07-05 | Employers/agencies using **automated employment decision tools** for NYC candidates | Independent **bias audit** within the prior year; publish summary; **10 business days' notice** to candidates; alternative process on request. | Recruiting standard: annual audit and notice. |
| **New York — RAISE Act** | Signed Dec 2025; effective 2027-01-01 ⚠ | Frontier developers | Safety frameworks, incident reporting. | Provider-side frontier only. |
| **Utah — AI Policy Act** (2024, amended 2025) | In force | Businesses using GenAI with consumers | Disclose GenAI use **on request**; regulated occupations (health, law, finance) disclose **proactively**; safe harbour for sandbox participants. | Customer-facing AI disclosure clause. |
| **Other 2026 developments** ⚠ | Illinois SB 315 (2027-01-01), Washington, Connecticut, Virginia (vetoed 2025), Maryland, Kentucky (state gov), Montana (right-to-compute) — landscape changes monthly. | | | Add a clause committing to jurisdiction review at each policy review cycle. |

---

## 3. United Kingdom

| Regime | Requirement | Policy clause implication |
|---|---|---|
| No AI statute; **pro-innovation principles** (safety, security & robustness; transparency & explainability; fairness; accountability & governance; contestability & redress) applied by sector regulators (ICO, FCA, CMA, Ofcom, MHRA, EHRC) via the DRCF. AI Security Institute (renamed 2025). Frontier AI bill repeatedly deferred ⚠. | Principles-based expectations. | Principles section mirrors the five UK principles when UK-relevant. |
| **UK GDPR / DPA 2018** + **Data (Use and Access) Act 2025** | DUAA relaxes Art. 22-style rules for non-special-category data: solely automated significant decisions allowed with safeguards (notice, human intervention, contest). ICO AI & data protection guidance; ICO "AI and biometrics strategy" (2025); DPIA required for most AI processing. | Data standard: DPIA trigger; safeguards for automated decisions; ICO guidance as reference. |
| **Equality Act 2010** | Discrimination via AI is discrimination. | Bias testing for people-decisions. |
| **FCA / PRA** (Consumer Duty, SM&CR, SS1/23 model risk management for banks) | Accountable senior manager for AI; model risk principles. | Financial overlay. |
| **Online Safety Act 2023** | Illegal content and children's safety duties for user-to-user/search services, including GenAI chatbots in scope (Ofcom 2024/25 statements). | Only if consumer platform. |

---

## 4. Singapore

| Regime | Requirement | Policy clause implication |
|---|---|---|
| **PDPA** + PDPC Advisory Guidelines on use of personal data in AI recommendation & decision systems (2024) | Consent/legitimate-interest for training and deployment; transparency; accountability. | Data standard. |
| **Model AI Governance Framework** (2020), **GenAI framework** (May 2024), **Agentic AI framework** (Jan 2026 / May 2026) — see §0 | Voluntary; internationally referenced. | Agent standard structure. |
| **MAS FEAT principles** (fairness, ethics, accountability, transparency) + Veritas toolkit | Financial institutions. | Financial overlay. |
| **AI Verify** testing framework/toolkit; **Cybersecurity Agency Guidelines on Securing AI Systems** (Oct 2024) | Testing and security practice. | Security standard references. |

---

## 5. Other jurisdictions (brief; ⚠ verify all)

| Jurisdiction | Status |
|---|---|
| **Canada** | AIDA (Bill C-27) died Jan 2025; no federal AI statute. PIPEDA/Quebec Law 25 (automated-decision disclosure and explanation rights). Federal Directive on Automated Decision-Making for government. |
| **South Korea** | **AI Basic Act** effective 2026-01-22: high-impact AI and GenAI transparency/labelling, risk management, domestic representative for foreign providers; grace period on fines. |
| **Japan** | AI Promotion Act (May 2025): soft-law, cooperation duties; METI/MIC AI Guidelines for Business. |
| **China** | Interim Measures for Generative AI (2023); **Measures for Labelling AI-Generated Content** effective 2025-09-01 (explicit + implicit labels); algorithm registry; deep synthesis rules; PIPL. |
| **Brazil** | PL 2338/2023 risk-based bill passed Senate Dec 2024; pending in Chamber. LGPD Art. 20 review of automated decisions. |
| **Australia** | Voluntary AI Safety Standard (2024); proposed mandatory guardrails for high-risk AI not yet legislated; Privacy Act reforms (2024) add automated-decision transparency from Dec 2026. |
| **India** | DPDP Act 2023 (rules 2025); advisory-based AI governance; no AI statute. |
| **UAE / Saudi** | Strategy and ethics charters; DIFC/ADGM data-protection rules cover automated processing. |

---

## 6. Sector overlays — quick trigger table

| Sector | Add to the document set |
|---|---|
| **Financial services / lending / insurance** | Model risk management standard (SR 11-7 / SS1/23 / MAS), adverse-action explainability, NAIC AI program elements, DORA ICT third-party register, EU Annex III credit/insurance = High tier + FRIA. |
| **Healthcare / life sciences** | HIPAA BAA list, TRAIGA patient disclosure, FDA/MDR/IVDR if SaMD, clinical-validation requirement before AI influences care, EU Annex III if triage/emergency. |
| **HR / employment (every company with employees)** | Employment AI standard: NYC LL144 audit/notice, IL HB 3773 notice + effects test, CA FEHA 4-year records + CCPA ADMT notice/opt-out, CO SB 26-189 (2027), EU Annex III employment = High tier + worker notification (Art. 26(7)), EEOC/Equality Act bias testing. |
| **Education** | FERPA/COPPA, EU Annex III education, proctoring = High tier, prohibition on emotion recognition. |
| **Public sector / public services** | EU Art. 27 FRIA + EU database registration, OMB memos (US federal), UK Algorithmic Transparency Recording Standard, TRAIGA government duties. |
| **Consumer products / platforms** | Art. 50 disclosures and marking, SB 942/SB 243, DSA, Online Safety Act, FTC §5 substantiation, Utah disclosure. |
| **Critical infrastructure / OT** | EU Annex III critical infrastructure, NIS2, safety-case requirements, no autonomous control actions without fail-safe. |
| **Legal / professional services** | Bar/professional duties: competence, confidentiality, supervision of AI output, client disclosure where required; privilege protection in prompts. |
| **Government contractor (US)** | NIST AI RMF / AI 600-1 alignment, OMB M-25-22 procurement terms, FedRAMP for AI services. |

---

## 7. Standing clause for every policy

Because this landscape changes monthly, the governance policy shall include: "The {{policy owner}} shall review applicable AI laws and standards at least every {{6}} months and at each material change in the Company's AI use, jurisdictions or customer base, and shall update this Policy and its Standards accordingly." Tag: `[NIST GOVERN 1.1 · ISO 42001 A.2.4 · Clause 10]`.
