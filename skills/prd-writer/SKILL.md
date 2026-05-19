---
name: prd-writer
description: Use when a PM wants to turn an idea, initiative, or discovery outcome into a full PRD. Scans Jira/Confluence for related context, asks 4 guided questions to assess maturity, and returns a development-ready PRD adapted to the feature's maturity stage (initial idea, clear direction, or existing-feature iteration).
---

# PRD Writer

## Purpose
Turn an idea, feature request, stakeholder ask, or discovery outcome into a structured Product Requirements Document. Force the right product thinking up front, surface missing pieces, and produce a PRD that engineering, design, and stakeholders can use directly. The output adapts to how mature the idea is.

## When to use
- New feature PRDs
- Product improvement / iteration PRDs
- MVP definition
- Internal tool or admin panel PRDs
- User flow redesign PRDs
- Monetization / pricing PRDs
- Compliance-related PRDs
- Experiment-to-feature PRDs
- Technical product PRDs
- Cross-team initiative PRDs

## Context to gather (before questions)
Search whatever Jira/Confluence MCP tools are available. Look for:

**Jira:**
- Related epics and their child tickets
- Similar feature tickets
- Bugs related to the feature
- Past implementation work and decisions
- Current roadmap tickets in this area
- Known dependencies, components, and owners

**Confluence:**
- Existing PRDs (to learn the company's PRD format)
- Product strategy documents
- Previous decision docs
- Research summaries and discovery docs
- UX guidelines and brand voice
- Analytics documentation and event taxonomies
- Technical architecture notes
- Release notes
- Known limitations and constraints

Classify findings as **Facts**, **Assumptions**, or **Missing**. If no MCP tools are connected, skip silently and proceed.

## Guided questions
Ask one at a time, in this exact format:

> **Question N:** <question>
> A. <option>
> B. <option>
> C. <option>
> D. Other: write your own

**Question 1:** How mature is this feature idea right now?
A. Initial idea — needs product thinking and structure
B. Clear direction — needs full PRD and requirements
C. Existing feature — needs improvement or iteration
D. Other: write your own

**Question 2:** Who is the main user affected by this feature?
A. End user
B. Admin / internal user
C. Support / operations team
D. Other: write your own

**Question 3:** What is the main problem this feature should solve?
A. Users are blocked or confused
B. Users are dropping off or not converting
C. Internal teams need a better operational workflow
D. Other: write your own

**Question 4:** What is the main success signal for this feature?
A. Higher conversion
B. Reduced friction / fewer support issues
C. Increased usage or engagement
D. Other: write your own

## Maturity-driven adaptation
Adapt emphasis in the output based on Question 1:

- **Initial idea**: emphasize Problem Statement, User Pain, Assumptions, Open Questions, Validation Plan, MVP Suggestion. De-emphasize detailed requirements.
- **Clear direction**: emphasize Full Requirements, User Flows, Edge Cases, Dependencies, Analytics, Jira Breakdown.
- **Existing feature iteration**: emphasize Current Behavior, Proposed Change, Why Current Flow Isn't Enough, Migration Impact, Regression Risks, Existing Users, Analytics Comparison.

If the company has its own PRD format in Confluence, match that instead of the template below.

## Output
Default structure (adapt to company format when found):

```markdown
# PRD: [Feature Name]

## 1. Overview
[Short explanation of the feature and why it matters.]

## 2. Background / Context
[Company context, prior decisions, related Jira/Confluence references with links, why this is being considered now.]

## 3. Problem Statement
[Clear explanation of the problem.]

## 4. Target Users
[Who is affected and how.]

## 5. Goals
### User Goals
- [Goal 1]
### Business Goals
- [Goal 1]
### Product Goals
- [Goal 1]

## 6. Non-Goals
[What this PRD will not solve.]

## 7. Scope
### In Scope
- [Item 1]
### Out of Scope
- [Item 1]

## 8. User Stories
- As a [user], I want to [action], so that [value].

## 9. User Flow
1. [Step 1]
2. [Step 2]

## 10. Requirements
### Functional Requirements
- [Requirement 1]
### Non-Functional Requirements
- Performance:
- Security:
- Permissions:
- Accessibility:
- Localization:
- Compliance:

## 11. UX / UI Considerations
- [Screen/state 1]
- [Empty states]
- [Error states]
- [Mobile/responsive behavior]

## 12. Analytics & Success Metrics
### Primary Metric
- [Metric]
### Secondary Metrics
- [Metric 1]
### Tracking Events
- Event:
- Trigger:
- Properties:

## 13. Dependencies
- Design:
- Frontend:
- Backend:
- Data:
- Legal:
- Support:
- Marketing:
- Other:

## 14. Risks
- [Risk 1]

## 15. Edge Cases
- [Edge case 1]

## 16. Rollout Plan
- Internal testing:
- Gradual rollout:
- Feature flag:
- Full release:

## 17. Open Questions
- [Question 1]

## 18. Suggested Jira Breakdown
- Epic:
- Ticket 1:
- Ticket 2:
```

## Quality rules
- Be specific, not generic
- Use company terminology found in context
- Separate facts (cite source) from assumptions (mark clearly)
- Call out missing information explicitly
- Match the company's existing PRD format when found in Confluence
- Output must be copy-pasteable into Confluence

## Advanced behaviors (apply when relevant)
- Identify missing product thinking
- Suggest MVP vs later phases and split into phases
- Detect unclear user value or unclear business value
- Suggest success metrics and analytics events
- Suggest implementation risks and rollout strategy
- Generate a Jira ticket breakdown from the PRD
- Generate alternate audiences of the same PRD on request: stakeholder summary, engineering handoff version, leadership one-pager, shorter Confluence-friendly version
