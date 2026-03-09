---
name: pm-pre-mortem
description: "Identify risks before a project starts: probability, impact, and mitigation plans."
---

Runs a structured pre-mortem to surface failure modes before they happen. Produces a risk register with ownership and mitigation plans.

## Context Loading

1. Read `sidekick/context/current-priorities.md` - understand what's at stake if this initiative fails
2. Read `sidekick/context/team-directory.md` - assign risk owners to the right people
3. Read `sidekick/context/communication-style.md` - match output style

Ask before generating:

- What project or launch is this pre-mortem for?
- What is the target date or milestone?
- Who are the key participants? (diverse perspectives catch more failure modes)
- Is there a PRD or plan to reference?

## Process

1. **Set the frame** - "Imagine it's [date]. The project failed. What happened?"
2. **Brainstorm failure modes** - technical, team, market, dependency, communication, resourcing
3. **Score each risk** - probability (H/M/L) and impact (H/M/L) independently
4. **Prioritize** - High/High risks get full mitigation plans. Low/Low get monitored only.
5. **Assign ownership** - every risk needs someone accountable for watching it
6. **Define tripwires** - what early signal tells you a risk is materializing?

## Output Format

```markdown
# Pre-Mortem: [Project / Launch Name]

**Date:** [date] | **Target date:** [launch date] | **Facilitator:** [name]

## Risk Register

| Risk                    | Category                               | Probability | Impact | Priority | Owner  |
| ----------------------- | -------------------------------------- | ----------- | ------ | -------- | ------ |
| [Specific failure mode] | Technical / Team / Market / Dependency | H/M/L       | H/M/L  | H/M/L    | [name] |

## Mitigation Plans (High Priority Risks)

### Risk: [Name]

- **What happens:** [Describe the failure scenario]
- **Early signal (tripwire):** [What would you see 2 weeks before this becomes a crisis?]
- **Mitigation:** [Specific steps to prevent or reduce probability]
- **Contingency:** [If it happens anyway, what's the response plan?]
- **Owner:** [name]

## Monitor List (Medium / Low Priority)

| Risk   | Signal to watch | Review cadence           | Owner  |
| ------ | --------------- | ------------------------ | ------ |
| [risk] | [indicator]     | [weekly / per milestone] | [name] |

## Success Conditions

[What does a successful outcome look like? This anchors the team on what they're protecting.]
```

## Rules

- Every High/High risk must have a mitigation plan AND a contingency
- Tripwires are mandatory for High risks - you need to catch them early, not at the deadline
- Risk categories to always check: external dependencies, key-person risk, scope creep, data/privacy, launch timing
- Never assign "team" as a risk owner. One person owns each risk.
- Revisit this register at each major milestone. Risks evolve.
