---
name: pm-stakeholder-map
description: "Map stakeholders on a power/interest grid with engagement strategy per person."
---

Produces a stakeholder map with power/interest positioning and a concrete engagement plan. Stops initiatives from being derailed by stakeholders who weren't managed.

## Context Loading

1. Read `sidekick/context/team-directory.md` - this is the primary source for stakeholder data
2. Read `sidekick/context/current-priorities.md` - confirm which initiative this map is for
3. Read `sidekick/context/communication-style.md` - match output style

Ask before generating:

- What initiative or decision is this map for?
- Are there external stakeholders (customers, partners, regulators) not in the team directory?

## Process

1. **Identify all stakeholders** - everyone who has interest in or influence over this initiative
2. **Assess power** - formal authority, budget control, ability to block or accelerate
3. **Assess interest** - how much does this outcome affect their work or goals?
4. **Position on grid** - High/Low for each dimension
5. **Define engagement strategy** - different quadrants need different approaches
6. **Assign owner** - who on the team manages each stakeholder relationship?

## Output Format

```markdown
# Stakeholder Map: [Initiative Name]

**Date:** [date]

## Power / Interest Grid

| Quadrant                                    | Stakeholders |
| ------------------------------------------- | ------------ |
| High Power / High Interest (Manage Closely) | [names]      |
| High Power / Low Interest (Keep Satisfied)  | [names]      |
| Low Power / High Interest (Keep Informed)   | [names]      |
| Low Power / Low Interest (Monitor)          | [names]      |

## Stakeholder Profiles

| Name   | Role   | Power | Interest | Position   | Engagement Strategy | Owner         |
| ------ | ------ | ----- | -------- | ---------- | ------------------- | ------------- |
| [name] | [role] | H/M/L | H/M/L    | [quadrant] | [specific approach] | [team member] |

## Engagement Plan

### Manage Closely (weekly or per milestone)

- **[Name]:** [What they need, how to communicate with them, what could derail their support]

### Keep Satisfied (at key milestones)

- **[Name]:** [What they need to stay bought in]

### Keep Informed (async, regular updates)

- **[Name]:** [Channel and cadence]

## Risks

| Stakeholder | Risk                 | Likelihood | Mitigation |
| ----------- | -------------------- | ---------- | ---------- |
| [name]      | [what they could do] | H/M/L      | [plan]     |
```

## Rules

- Every "Manage Closely" stakeholder needs a named relationship owner
- Engagement strategy must be specific - "keep them updated" is not a strategy
- External stakeholders (customers, regulators, partners) must be included if they exist
- Map is point-in-time. Note the date and plan to revisit if initiative runs >3 months.
