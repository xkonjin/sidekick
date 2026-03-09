---
name: cost-analyzer
description: "Perform a cost-benefit or ROI analysis for a decision, tool, hire, or initiative. Trigger when the user says 'cost analysis', 'ROI calculation', 'is this worth it', or 'cost benefit'."
---

# Cost Analyzer

Produces a structured cost-benefit analysis: total cost of ownership, expected return, payback period, and a clear go/no-go recommendation.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/current-priorities.md` - Understand what this investment would serve
- `sidekick/memory/decisions.md` - Check for related budget decisions or spending commitments
- `sidekick/memory/budget.md` - Current budget position (if it exists)

### Step 2: Scope the Analysis

Ask if not specified:

- What are you evaluating? (tool, hire, initiative, vendor, project)
- What is the investment amount or range?
- What time horizon? (monthly, quarterly, annual, multi-year)
- What is the expected benefit? (revenue, time saved, risk reduced, quality improved)
- What is the baseline — what happens if you do nothing?

### Step 3: Build the Analysis

Calculate:

- **Total Cost of Ownership (TCO):** Direct costs + implementation + ongoing + hidden costs
- **Expected Benefits:** Quantify where possible, describe where not
- **Payback Period:** When cumulative benefits exceed cumulative costs
- **ROI:** (Total benefit - Total cost) / Total cost

### Step 4: Save Output

Write to `sidekick/outputs/cost-analysis-[topic]-[DATE].md`

## Output Format

```markdown
# Cost Analysis: [What You're Evaluating]

**Date:** [DATE] | **Time horizon:** [period] | **Decision owner:** [name]

## Investment Summary

| Element                 | Amount / Estimate |
| ----------------------- | ----------------- |
| Upfront cost            | [amount]          |
| Implementation cost     | [amount]          |
| Ongoing cost (per year) | [amount]          |
| Hidden costs            | [amount + notes]  |
| **Total (Year 1)**      | [amount]          |
| **Total (3-year TCO)**  | [amount]          |

## Expected Benefits

| Benefit            | Type                     | Estimated Value | Confidence |
| ------------------ | ------------------------ | --------------- | ---------- |
| [Specific benefit] | Revenue / Savings / Risk | [amount]        | HIGH/MED   |
| [Specific benefit] | Time saved               | [hours * rate]  | MED/LOW    |

## Do-Nothing Baseline

[What happens if you don't make this investment. Quantify the cost of inaction where possible.]

## ROI Calculation

| Metric         | Value                |
| -------------- | -------------------- |
| Total benefit  | [sum]                |
| Total cost     | [sum]                |
| Net benefit    | [diff]               |
| ROI            | [%]                  |
| Payback period | [months or quarters] |

## Sensitivity

| If...                     | ROI becomes... | Recommendation changes? |
| ------------------------- | -------------- | ----------------------- |
| Benefits are 50% lower    | [%]            | [Yes/No]                |
| Costs are 30% higher      | [%]            | [Yes/No]                |
| Timeline extends 6 months | [%]            | [Yes/No]                |

## Recommendation

**Go / No-Go / Conditional**

[2-3 sentences. Why this recommendation, what assumptions it depends on, and what would change it.]
```

## After This Skill

- **decision-log** — log the go/no-go decision → Read `skills/decision-log/SKILL.md`
- **budget-tracker** — update budget with committed spend → Read `skill-packs/finance-ops/skills/finance-budget-tracker.md`
- **vendor-evaluator** — if comparing vendors, do a full evaluation → Read `skill-packs/finance-ops/skills/finance-vendor-evaluator.md`

## Rules

- Quantify where possible. "Saves time" is not an analysis. "Saves 5 hours/week at $X/hour" is.
- Separate hard costs from soft benefits. Don't mix them in the same column.
- The do-nothing baseline is mandatory. Every cost analysis is relative to the alternative.
- Sensitivity analysis is mandatory. Single-point estimates create false confidence.
- If key data is missing, say what's needed rather than assuming values.
