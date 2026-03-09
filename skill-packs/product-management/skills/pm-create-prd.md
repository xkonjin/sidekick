---
name: pm-create-prd
description: "Write a complete Product Requirements Document for a feature or initiative."
---

Produces a structured PRD covering problem, audience, goals, scope, success metrics, risks, and out of scope. Read from context before writing.

## Context Loading

Before generating the PRD:

1. Read `sidekick/context/current-priorities.md` - confirm this feature aligns with current focus
2. Read `sidekick/context/team-directory.md` - identify the right owner, stakeholders, and eng lead
3. Read `sidekick/context/communication-style.md` - match output style to how this person writes

If the user hasn't named the feature yet, ask: "What are we speccing?" before starting.

## Process

1. **Clarify scope** - ask: what problem does this solve, for whom, and what does success look like in 90 days?
2. **Identify unknowns** - surface assumptions before writing (use pm-identify-assumptions if needed)
3. **Draft the PRD** - follow the output format below
4. **Review** - flag any sections with low confidence or missing inputs

## Output Format

```markdown
# PRD: [Feature Name]

**Status:** Draft | **Owner:** [Name from team-directory] | **Last updated:** [date]

## Problem

[1-2 sentences. What is broken or missing? Who feels it?]

## Audience

[Primary user segment. Be specific. Not "users" - which users, in what context?]

## Goals

- [Goal 1 - measurable, time-bound]
- [Goal 2]
- [Goal 3]

## Success Metrics

| Metric   | Baseline  | Target | Timeframe |
| -------- | --------- | ------ | --------- |
| [metric] | [current] | [goal] | [when]    |

## Scope

### In scope

- [Feature element 1]
- [Feature element 2]

### Out of scope

- [Explicitly excluded items - prevents scope creep]

## User Stories

[3-5 key stories. Full detail via pm-user-stories skill if needed.]

## Risks & Assumptions

| Risk / Assumption | Confidence   | Mitigation      |
| ----------------- | ------------ | --------------- |
| [item]            | HIGH/MED/LOW | [how to handle] |

## Open Questions

- [Question requiring resolution before build starts]
```

## Rules

- Never leave placeholder text in the final output
- If a metric has no baseline, note "TBD - measure at launch" rather than guessing
- Out of scope section is mandatory - make the team align on what this isn't
- Flag if the feature doesn't map to a current priority
