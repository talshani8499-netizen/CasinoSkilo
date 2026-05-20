---
name: ux-copy
description: Use when a PM needs UX copy or microcopy — CTAs, error messages, empty states, tooltips, success messages, modals, onboarding text, banners, form labels, paywall or pricing copy. Scans Confluence for brand voice and product terminology, asks 4 guided questions, and returns multiple tone variants plus a full UI copy set.
---

# UX Copy

## Purpose
Produce clear, consistent, user-friendly product copy that matches the company's brand voice and existing terminology. Replace technical or vague wording with specific, actionable, human language across CTAs, errors, empty states, tooltips, banners, and onboarding.

## When to use
- CTA / button copy
- Error and warning messages
- Empty states
- Tooltips
- Success messages
- Confirmation modals
- Onboarding text
- Product banners
- Form labels and helper text
- Paywall copy
- Pricing page copy
- Feature explanation copy
- Release notes snippets
- In-product announcements
- Compliance notices
- Permission prompts

## Context to gather (before questions)
Search Jira/Confluence MCP tools for:

**Jira:**
- Related feature tickets
- Existing UX copy in similar tickets
- Previous copy changes
- Support-related issues caused by unclear copy
- Product areas where the copy will appear

**Confluence:**
- Brand voice and UX writing guidelines
- Tone of voice documents
- Product terminology and glossary
- Previous copy decks or docs
- Existing error message patterns
- Localization rules
- Legal / compliance wording

**Optional sources (when available):**
- Existing product screenshots
- Figma components
- Design system documentation
- Support macros
- Help center articles

Classify findings as **Facts** (cite source), **Assumptions**, or **Missing**. If no MCP tools are connected, skip silently and proceed.

## Guided questions
Ask one at a time, in this exact format:

> **Question N:** <question>
> A. <option>
> B. <option>
> C. <option>
> D. Other: write your own

**Question 1:** What type of copy do you need?
A. CTA / button copy
B. Error or warning message
C. Empty state / tooltip
D. Other: write your own

**Question 2:** What should the user understand or do after reading this copy?
A. Continue to the next step
B. Fix a problem or missing input
C. Understand why something happened
D. Other: write your own

**Question 3:** What tone should the copy use?
A. Clear and professional
B. Friendly and helpful
C. Short and direct
D. Other: write your own

**Question 4:** Are there any constraints for this copy?
A. Very short text / limited space
B. Legal or compliance sensitivity
C. Needs to match existing product language
D. Other: write your own

## Output
Produce the following structure exactly (markdown):

```markdown
# UX Copy Suggestions: [Screen / State]

## 1. Context
[Where this copy appears and what the user is trying to do.]

## 2. Recommended Copy
### Primary Recommendation
[Best copy option]

### Why this works
[Short explanation tied to brand voice, clarity, and user intent.]

## 3. Alternative Versions
### Short version
[Copy]

### Friendly version
[Copy]

### Professional version
[Copy]

### More action-oriented version
[Copy]

## 4. Full UI Copy Set
### CTA
[Button text]

### Tooltip
[Tooltip text]

### Error State
[Error message]

### Success State
[Success message]

### Empty State
[Empty state copy]

## 5. Notes
- [Product, legal, localization, or UX considerations]
```

## Copy quality principles
Every variant must follow these principles. Use them to self-check before returning output.

- **Clear**: the user immediately understands what happened or what to do.
  - Bad: "Action failed." → Better: "We couldn't save your changes. Please try again."
- **Specific**: avoid vague messages.
  - Bad: "Something went wrong." → Better: "We couldn't verify your payment method. Check your details and try again."
- **Actionable**: tell the user what to do next.
  - Bad: "Invalid input." → Better: "Enter a valid email address to continue."
- **Short**: concise, especially in product UI.
  - Bad: "In order to proceed to the next step of this process, you need to complete all required fields." → Better: "Complete all required fields to continue."
- **Human**: avoid robotic or overly technical language.
  - Bad: "Authentication token expired." → Better: "Your session expired. Sign in again to continue."

## Quality rules
- Match brand voice when found in Confluence
- Match existing product terminology when found
- Separate facts (cite source) from assumptions (mark clearly)
- Call out missing information explicitly
- Flag risky compliance / legal language
- Always provide multiple variants when length or tone is a factor

## Advanced behaviors (apply when relevant)
- Rewrite technical text into user-friendly language
- Shorten long copy while preserving meaning
- Suggest better CTA hierarchy
- Suggest error-recovery copy that points to the fix
- Suggest empty state copy with a clear action
- Suggest localization-friendly wording (avoid idioms, ambiguous pronouns)
- Generate A/B copy variants for the Experiment Planner skill
- Generate copy for modals, tooltips, banners, and forms together
