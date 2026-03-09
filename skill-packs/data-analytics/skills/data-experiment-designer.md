---
name: data-experiment-designer
description: "Design a structured experiment or A/B test with hypothesis, variants, sample size guidance, and success criteria. Trigger when the user says 'design an experiment', 'A/B test plan', 'hypothesis', or 'run a test on'."
---

# Experiment Designer

Structures experiments so they can actually be evaluated. Forces hypothesis clarity, guard rails, and a rollback plan before any test runs.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/context/current-priorities.md` - confirm the test serves an active priority
- `sidekick/memory/decisions.md` (if it exists) - check if related decisions have already been made
- `sidekick/memory/metrics/` (if any exist) - identify existing metrics to use as success criteria

### Step 2: Clarify

Ask for anything not already provided:

- What are you trying to test?
- What does success look like — what metric moves, by how much?
- How much traffic or users are available for this test?

Skip questions if the user's message already answers them.

### Step 3: Draft the Experiment Plan

```markdown
# Experiment: [Experiment Name]

**Created:** [DATE] | **Owner:** [Name]

## Hypothesis

If we [change], then [metric] will [increase/decrease] by [amount] because [mechanism].

## Null Hypothesis

[What we expect to see if the change has no effect]

## Variants

| Variant | Description                 | Traffic split |
| ------- | --------------------------- | ------------- |
| Control | [Current state — no change] | [X%]          |
| Variant | [What changes and how]      | [Y%]          |

## Success Criteria

| Metric           | Direction | Minimum detectable effect | Confidence threshold |
| ---------------- | --------- | ------------------------- | -------------------- |
| [Primary metric] | [Up/Down] | [X%]                      | 95%                  |
| [Guard rail 1]   | No change | [threshold]               | —                    |

## Sample Size & Duration

- **Estimated sample needed:** [N per variant] — based on [baseline rate] and [MDE]
- **Estimated duration:** [X days] at [Y daily volume]
- **Note:** [Flag if sample size is likely insufficient]

## Guard Rails

These metrics must NOT move negatively. If they do, stop the test:

- [Guard rail metric 1]: must stay within [threshold]
- [Guard rail metric 2]: must stay within [threshold]

## Stop-Early Conditions

- Stop if [metric] moves more than [X%] in the negative direction
- Stop if guard rail metrics breach thresholds
- Stop if [other critical signal]

## Rollback Plan

[What happens if we need to revert. How fast, who does it, what's the impact.]

## Timeline

| Phase         | Date   | Owner  |
| ------------- | ------ | ------ |
| Build / setup | [date] | [name] |
| Launch        | [date] | [name] |
| Read results  | [date] | [name] |
| Decision      | [date] | [name] |
```

### Step 4: Save

Save to `sidekick/outputs/experiment-[name]-[DATE].md`.

## After This Skill

| Condition                                       | Suggestion                                                                      |
| ----------------------------------------------- | ------------------------------------------------------------------------------- |
| Experiment concludes and a decision is made     | **decision-log** → `skills/decision-log/SKILL.md`                               |
| Metric used in test isn't formally defined      | **metric-definer** → `skill-packs/data-analytics/skills/data-metric-definer.md` |
| Results need to be communicated to stakeholders | **data-storyteller** → `skill-packs/data-analytics/skills/data-storyteller.md`  |

## Rules

- Always state the null hypothesis — it forces honest framing of what "no effect" looks like
- Flag when the available sample size is likely insufficient to detect the minimum detectable effect
- Include a "stop early" condition — experiments without exit criteria run indefinitely
- Guard rails are mandatory; secondary metric degradation invalidates a primary metric win
- Never fabricate expected effect sizes; use "TBD — estimate from historical data" if unknown
