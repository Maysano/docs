# What AI Does Not Do

Maysano uses AI to accelerate governance workflows. This page defines the boundaries of AI involvement — what is explicitly outside the AI's authority, capability, and design intent.

---

## AI Does Not Make Decisions

AI in Maysano generates suggestions, drafts, recommendations, and summaries. It does not make governance decisions.

- AI does not approve product releases.
- AI does not promote lifecycle states.
- AI does not select governance components for a product.
- AI does not create DQ checks without human review.
- AI does not set KPI targets or modify objectives.

Every AI output is a proposal. A human must review, accept, modify, or reject it before it takes effect.

---

## AI Does Not Own Accountability

Accountability in Maysano is always assigned to a human role:

- The **Outcome Owner** is accountable for objectives and outcome KPIs.
- The **Product Manager** is accountable for product value and alignment.
- The **Product Owner** is accountable for metadata, quality implementation, and tooling.
- The **System Steward** is accountable for governance integrity and component quality.

AI assists these roles. It does not replace them. If an AI recommendation leads to a poor outcome, accountability rests with the human who approved it.

---

## AI Does Not Access Arbitrary Data

AI features in Maysano operate within defined boundaries:

- The AI assistant can read product metadata, governance components, and quality scores through controlled internal tools.
- The AI does not have direct access to source databases, data warehouses, or raw data.
- The AI does not query customer data, PII, or sensitive records.
- Quality intelligence features receive aggregated check results and dimension scores — not the underlying data rows.

Data access is mediated by the platform's internal tool layer, which enforces scope and permissions.

---

## AI Does Not Override Governance

AI respects the governance model:

- AI-generated specifications follow the ODPS 4.1 structure and active guidance rulesets.
- AI cannot create governance components (DQ Profiles, SLA Profiles) without human action.
- AI cannot modify published (immutable) product versions.
- AI recommendations are filtered against existing checks to avoid duplicates.

If a guidance ruleset instructs the AI to follow specific patterns, the AI adheres to those rules. The System Steward controls the rules; the AI follows them.

---

## AI Does Not Guarantee Correctness

AI outputs are probabilistic, not deterministic:

- Generated specifications may contain inaccuracies that require human review.
- Quality check recommendations may not cover all relevant scenarios.
- Executive summaries reflect the data provided, not necessarily the full picture.
- Remediation advice suggests hypotheses, not confirmed root causes.

Human judgment remains essential for validating AI outputs before they become part of the governance record.

---

## AI Does Not Learn From Your Data

The AI in Maysano does not train on your organization's data:

- Conversations and product data are not used to fine-tune the underlying model.
- AI responses are generated from the model's general knowledge combined with the context provided in the current request.
- No data leaves the platform except through explicit API calls to the LLM provider, which are subject to the provider's data handling policies.

---

## AI Does Not Operate Autonomously

AI features in Maysano are always initiated by a human action:

- A user opens the assistant and asks a question.
- A user requests AI-generated specifications.
- A user clicks "Recommend checks" to trigger check recommendations.
- A user initiates batch auto-setup.

The AI does not monitor products in the background, proactively generate alerts, or take actions without being invoked.

---

## Summary of Boundaries

| AI Does | AI Does Not |
|---|---|
| Suggests specifications | Approves or publishes them |
| Recommends DQ checks | Creates or runs them without review |
| Generates executive summaries | Makes governance decisions |
| Proposes remediation steps | Fixes data issues |
| Follows guidance rulesets | Modifies governance rules |
| Accelerates workflows | Replaces human accountability |
