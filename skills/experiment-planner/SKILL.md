---
name: experiment-planner
description: Use when a PM wants to design an A/B test or product experiment, especially in Optimizely. Scans Jira/Confluence for prior experiments and analytics docs, asks 4 guided questions, classifies whether dev work is needed, and returns a full experiment plan with hypothesis, variants, primary/guardrail metrics, Optimizely setup, and Jira ticket list.
---

# Experiment Planner

## Purpose
Help PMs design stronger experiments — clear hypothesis, primary and guardrail metrics, realistic implementation plan, and a decision about whether the experiment can be built independently in Optimizely or requires development support. Prevent weak experiments with vague hypotheses or missing metrics.

## When to use
- A/B test planning
- Optimizely experiment setup planning
- UI variant testing
- Copy / messaging testing
- Funnel / flow testing
- Pricing / package testing
- CTA testing
- Landing page tests
- Checkout, onboarding, or feature-adoption tests
- Experiment documentation and ticket creation

## Context to gather (before questions)
Search Jira/Confluence MCP tools for:

**Jira:**
- Previous experiment tickets
- Optimizely-related implementation tickets
- Frontend components involved in similar experiments
- Feature flag tickets
- Analytics implementation tickets
- Past bugs related to experiments
- Tickets touching the target flow

**Confluence:**
- Previous A/B test documentation and results
- Experiment guidelines and Optimizely setup docs
- Product analytics documentation and event taxonomy
- Funnel and conversion metrics documentation
- Known Optimizely limitations

Classify findings as **Facts**, **Assumptions**, or **Missing**. If no MCP tools are connected, skip silently and proceed.

## Guided questions
Ask one at a time, in this exact format:

> **Question N:** <question>
> A. <option>
> B. <option>
> C. <option>
> D. Other: write your own

**Question 1:** What type of change do you want to test?
A. UI / visual change
B. Copy / messaging change
C. Flow / funnel change
D. Other: write your own

**Question 2:** What is the main goal of this experiment?
A. Increase conversion
B. Reduce drop-off
C. Increase engagement or usage
D. Other: write your own

**Question 3:** What should be the primary success metric?
A. Click-through rate
B. Completion / conversion rate
C. Revenue / purchase rate
D. Other: write your own

**Question 4:** Can this experiment be built directly in Optimizely, or do you need development support?
A. Can be done independently in Optimizely
B. Requires frontend development
C. Not sure — help me decide
D. Other: write your own

## Optimizely-vs-development classification
When Q4 = "Not sure" (or to validate any answer), classify the change:

**Usually doable directly in Optimizely:**
- Copy / CTA text changes
- Minor visual changes (color, spacing, image swap)
- Show/hide existing elements
- Reorder existing page elements
- Simple targeting rules
- Basic landing page variations

**Usually requires development:**
- New backend logic or API calls
- Pricing calculation changes
- Checkout behavior changes
- New user permissions
- New data persistence
- Complex funnel changes
- New components
- New event tracking not already instrumented
- Server-side experimentation

Return one of: **Likely no development needed** / **Possibly requires frontend development** / **Definitely requires development** / **Requires technical review** — with a short reason.

## Output
Produce the following structure exactly (markdown):

```markdown
# Experiment Plan: [Experiment Name]

## 1. Experiment Summary
[Short description of the experiment.]

## 2. Background / Context
[Relevant context from Jira, Confluence, previous tests, product flow, or analytics — with source links.]

## 3. Hypothesis
If we [make this change], then [metric] will improve because [reason].

## 4. Experiment Type
UI / Copy / Flow / Funnel / Pricing / Other

## 5. Target Audience
[Who should be included in the experiment.]

## 6. Target Surface
[Page, screen, component, funnel step, or user segment.]

## 7. Variants
### Control
[Current experience.]
### Variant A
[New experience.]

## 8. Primary Metric
[The main metric that determines success.]

## 9. Guardrail Metrics
- [Metric that should not be harmed]
- [Metric that should not be harmed]

## 10. Optimizely Setup Recommendation
- Experiment type:
- Targeting:
- Traffic allocation:
- Pages / components:
- Events needed:
- Custom attributes needed:
- QA checklist:
- Development needed: Yes / No / Not sure → [classification + reason]

## 11. Implementation Plan
[How the experiment should be implemented.]

## 12. Development Requirements
[Only if development is needed.]

## 13. Analytics Requirements
- Event:
- Trigger:
- Properties:
- Expected behavior:

## 14. Risks
- [Risk 1]

## 15. Decision Rule
Ship the variant if [primary metric] improves without negatively impacting [guardrail metric].

## 16. Jira Tickets Needed
- Experiment setup ticket
- Analytics ticket
- Frontend ticket (if needed)
- QA ticket (if needed)
```

## Quality rules
- Be specific, not generic
- Use company terminology found in context
- Separate facts (cite source) from assumptions (mark clearly)
- Call out missing information explicitly — especially missing events
- Always include guardrail metrics, not just primary
- If the change cannot be cleanly tested via A/B (e.g., one-time event, regulatory), recommend an alternative method (user research, usability test, data analysis)

## Advanced behaviors (apply when relevant)
- Identify whether A/B testing is even the right method for this question
- Detect tests that are too broad or underpowered
- Suggest QA steps and rollout strategy after success
- Suggest "what NOT to test" if the change has obvious risks
- Generate Jira tickets for setup, analytics, frontend, QA
- Generate a stakeholder-friendly experiment summary
- Generate a Confluence-ready experiment documentation page
