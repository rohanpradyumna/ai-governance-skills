# Review checklist

**Read this when:** SKILL.md step 6, before presenting any draft. Work through every gate; fix rather than annotate. Then build the coverage matrix (`frameworks-crosswalk.md` §4) and the handoff list.

---

## A. Structure gates

- [ ] Document set matches the chosen depth; `ai-agent-standard.md` present if any agent/automation exists.
- [ ] Each document has a document-control block (owner role, approver, version, effective date, review cadence, classification).
- [ ] Policy ≤ ~6 pages; procedures aren't buried in it; standards hold the measurable requirements.
- [ ] One definitions section (in the policy); standards reference it; terms used consistently (AI system, AI agent, autonomy level, high-impact/consequential decision, deployer, provider, human oversight, AI incident, Restricted/Confidential).
- [ ] Every `{{placeholder}}` replaced or listed in the handoff; every `<!-- guidance -->` comment removed; no empty headings (deleted with reason noted in handoff).
- [ ] Cross-references to existing company policies (InfoSec, Privacy, HR/Code of Conduct, Procurement, Records, Incident Response) instead of duplicated text.

## B. Clause quality gates

- [ ] Every control clause has requirement · owner (role) · evidence · framework tag.
- [ ] Modal verbs used correctly and defined (shall / should / may).
- [ ] No untestable adjectives ("appropriate", "adequate", "reasonable", "timely", "regularly", "robust") without a threshold, named reviewer, or deadline. Search for each and fix.
- [ ] No person's name as an owner; roles only (holders may be listed in an annex/register).
- [ ] Numbers are real decisions, not "TBD" — caps, retention, cadences, SLAs filled with defaults and flagged as adjustable in the handoff.
- [ ] Every prohibition pairs with an enforcement mechanism (technical control or process).
- [ ] The AUP is readable in ten minutes by a new hire: named approved tools, named banned data classes, named consequences, where to ask.

## C. Content gates

- [ ] **Tiering** applied per system and use; legal high-risk/ADMT classifications forced to High; prohibited list present and split legal vs. company-elective.
- [ ] **Register** includes suspected shadow AI, embedded SaaS AI features, coding assistants, browser extensions, meeting assistants, and every agent — each with owner and tier.
- [ ] **Data matrix** present; consumer accounts excluded from Internal+; secrets never in prompts; Restricted rules with Legal/Privacy sign-off; BAA note if health.
- [ ] **Human oversight** clauses pass the five-part test (competence, information, authority, time, accountability) for High tier.
- [ ] **Agents** (if any): per-agent identity, least agency, tool & data allowlists, action classes with gates, caps, kill switch owner and test cadence, log schema, untrusted-input rule, disclosure of AI + principal, scope-change re-approval, multi-agent inheritance rule, third-party agents covered.
- [ ] **Transparency**: AI disclosure for external-facing AI; synthetic-content marking where the company generates content; employee/candidate notices where employment AI exists.
- [ ] **Employment AI** (every company with staff): bias testing, notices, human review, record retention (4 years CA FEHA; 3 years CO 2027), NYC LL144 audit if NYC hiring, IL notice, EU worker-representative notification for high-risk.
- [ ] **Vendors**: approved-tools register, training opt-out contractual, model-change notice, agent clauses if applicable.
- [ ] **Incidents**: AI incident defined (incl. agent-specific triggers), reporting channel, severity, halt → contain → preserve → notify → learn; regulator/customer notification analysis; links to existing IR plan.
- [ ] **Training**: role-based literacy plan; oversight-role competence; records (EU Art. 4).
- [ ] **Review & change**: jurisdiction review cadence; policy review cadence; re-tier on scope change; management review; independent audit for Comprehensive.
- [ ] **Principles** section is short and each principle maps to at least one control (no orphan values statements).

## D. Legal-accuracy gates (regulatory snapshot 2026-09)

- [ ] No claim that the "Colorado AI Act" is in force or requires impact assessments/duty of care. Colorado = SB 26-189 ADMT Act, effective 2027-01-01, notice/adverse-outcome/human-review/3-year records, ⚠ rulemaking.
- [ ] No claim that EU high-risk obligations apply from August 2026. Annex III ⚠ 2027-12-02; Annex I ⚠ 2028-08-02. Art. 4 (2025-02-02) and Art. 50 (2026-08-02) are in force.
- [ ] TRAIGA described as intent-based; no general disclosure/impact-assessment duty for private companies (healthcare-provider disclosure aside).
- [ ] California: CCPA ADMT regs (employer compliance 2027-01-01; risk assessments by 2027-12-31) and FEHA ADS regs (2025-10-01, 4-year records) are what bind employers; SB 53 is frontier developers only.
- [ ] "Aligned to" NIST/ISO, not "compliant with"; ISO 42001 certification not presented as legal compliance.
- [ ] Deployer/provider role stated; substantial-modification flip mentioned if the company customises or rebrands models.
- [ ] Every ⚠ item from `regulatory-landscape.md` that the draft relies on appears in the handoff list as "verify before adoption".
- [ ] No invented article numbers, dates, or statute names; anything not in `regulatory-landscape.md` is marked "verify".
- [ ] "Not legal advice" note present in the deliverable summary (not necessarily inside the policy text itself).

## E. Coverage matrix

- [ ] Built from the sections triggered at intake (`frameworks-crosswalk.md` §4 rule).
- [ ] Every row has a document + clause or a reasoned N/A; no "Partial" without a fix or a handoff item.
- [ ] Comprehensive depth: Statement of Applicability covers all 38 Annex A controls.

## F. Handoff list must include

1. Assumptions made at intake (jurisdictions, role, data classes, existing policies).
2. Numbers to confirm (caps, retention, cadences, thresholds) with the defaults used.
3. ⚠ regulatory items to verify, each with the primary source from `sources.md`.
4. Items needing a professional: works-council/union consultation, sector regulator expectations, contract reviews, DPIA/FRIA sign-off, insurance.
5. Technical enforcement to implement (SSO gating, DLP, agent gateway, spend caps, logging) with owners.
6. First-90-days actions in order.

## G. Anti-patterns to catch

| Anti-pattern | Fix |
|---|---|
| One 40-page "AI Policy" with everything in it | Split into policy + standards + procedures; AUP stays ≤ 3 pages |
| "Employees must use AI responsibly and ethically" as a control | Replace with specific, testable rules |
| "All AI is high risk" or "AI is treated like any other software" | Tier per system |
| Agent standard that only says "agents must be monitored" | Apply `agentic-ai-controls.md` catalogue |
| Approved-tool list absent because "it changes too often" | Put the list in a register, reference it from the AUP, name the owner and update cadence |
| Human oversight = "a manager reviews outputs sometimes" | Named role, authority, sampling rate, competence |
| Copying vendor marketing ("enterprise-grade privacy") into the policy | Cite contract terms and the register instead |
| Policy bans consumer AI but SSO/DLP don't enforce it | Add enforcement pairing and a rollout action |
| Citing blogs, vendors or this skill as authority | Primary sources only (`sources.md`) |
| Assuming NIST/ISO alignment satisfies EU/US law | Layer legal obligations explicitly |
