---
name: scenario-planner
description: "Map 2-4 alternative scenarios with probability, impact, and response plans for a given situation. Trigger when the user says 'what if', 'scenario plan', 'if X happens', 'contingency plan', or 'plan B'."
---

# Scenario Planner

Prevents tunnel vision by mapping what could actually happen, not just what you're hoping for. Produces a scenario set with probability estimates, impact analysis, and ready-to-execute response plans.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - What's at stake and what the scenarios need to protect
- `sidekick/context/working-preferences.md` - Preferred output format (if it exists)
- `sidekick/memory/decisions.md` - Prior decisions that constrain or inform the scenarios (if it exists)
- `sidekick/memory/projects/` - Active projects that the scenarios might affect

### Step 2: Define the Situation

If not specified, ask:

- What decision or situation is this scenario plan for?
- What is the timeframe? (What's the window before you must act?)
- What are the 1-2 biggest uncertainties that would change your response?

Skip questions if the user's message already answers them.

### Step 3: Build Scenarios

Generate 2-4 distinct scenarios. Each should represent a meaningfully different version of what could happen - not just "good", "medium", "bad". Ground each in specific variables that differ.

For each scenario:

- Assign a rough probability (sum should approximate 100%)
- Assess impact on the user's current priorities
- Define the trigger signal: what early indicator would tell you this scenario is unfolding?
- Draft a response plan: concrete first actions if this scenario materializes

### Step 4: Generate Output

Save to `sidekick/outputs/scenario-[topic]-[DATE].md`.

```markdown
# Scenario Plan: [Topic]

**Built:** [date] | **Decision window:** [timeframe]

## The Core Uncertainty

[1-2 sentences on what unknown variable is driving these scenarios]

## Scenarios

### Scenario 1: [Name]

**Probability:** [%] | **Impact on priorities:** [High / Medium / Low]

[2-3 sentences describing what happens in this scenario]

**Trigger signal:** [What you'd see 1-2 weeks before this is confirmed]

**Response plan:**

- [First action]
- [Second action]
- [Who to loop in and when]

---

### Scenario 2: [Name]

[Same structure]

---

### Scenario 3: [Name] _(if applicable)_

[Same structure]

---

## Recommended Default Stance

[Given the probabilities and impacts, what's the default position to take NOW that preserves optionality across scenarios?]

## Decisions This Resolves

[List any decisions that were blocked pending this scenario analysis]
```

## After This Skill

| If...                                                 | Suggest...                                                    |
| ----------------------------------------------------- | ------------------------------------------------------------- |
| A decision needs to be logged following this analysis | Read `skills/decision-log/SKILL.md`                           |
| A specific scenario is a project risk                 | Read `skill-packs/product-management/skills/pm-pre-mortem.md` |

## Rules

- Scenarios must be meaningfully distinct - don't just relabel optimistic/pessimistic versions of the same world.
- Every scenario needs a trigger signal. You can't respond to what you can't detect.
- Probability estimates are rough - the point is relative likelihood, not false precision.
- The "Default Stance" section is mandatory. The whole point is to enable action under uncertainty.
- Never fabricate. If you can't find it, say so.
