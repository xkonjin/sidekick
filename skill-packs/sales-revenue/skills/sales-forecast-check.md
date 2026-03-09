---
name: sales-forecast-check
description: "Run pipeline math to produce a weighted revenue forecast. Trigger when the user says 'forecast', 'revenue forecast', or 'pipeline math'."
---

Produces a weighted forecast by stage, risk flags, deals at risk, and gap to target. Runs from pipeline data — no inputs required if pipeline is current.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/memory/pipeline.md` - primary source for all active deals and stages (if it exists)
- `sidekick/memory/deals/` - individual deal files for detail on each opportunity (if it exists)
- `sidekick/context/current-priorities.md` - check if a revenue target or quota is defined

### Step 2: Clarify Target and Timeframe

If not already defined in pipeline.md or priorities, ask:

- What is the target revenue for this period?
- What timeframe are we forecasting? (this month / this quarter / custom)

Skip questions if the user's message already answers them.

### Step 3: Run the Pipeline Math

Apply conservative probability defaults by stage:

| Stage       | Default Probability |
| ----------- | ------------------- |
| Prospecting | 10%                 |
| Discovery   | 20%                 |
| Proposal    | 40%                 |
| Negotiation | 70%                 |
| Closed Won  | 100%                |

Override defaults only if the user has specified deal-level probabilities.

### Step 4: Flag Risks

Identify:

- Deals with no activity logged in 14+ days
- Deals with close dates past due and still open
- Stage concentration risk (e.g., everything in one stage)

### Step 5: Save Output

Write to `sidekick/outputs/forecast-[DATE].md`.

## Output Format

```markdown
# Revenue Forecast — [DATE]

**Period:** [timeframe] | **Target:** [amount] | **Forecast:** [weighted total]

## Pipeline by Stage

| Stage       | # Deals | Total Value | Probability | Weighted Value |
| ----------- | ------- | ----------- | ----------- | -------------- |
| Prospecting | [n]     | [amount]    | 10%         | [amount]       |
| Discovery   | [n]     | [amount]    | 20%         | [amount]       |
| Proposal    | [n]     | [amount]    | 40%         | [amount]       |
| Negotiation | [n]     | [amount]    | 70%         | [amount]       |
| **Total**   |         |             |             | **[total]**    |

## Gap to Target

**Target:** [amount] | **Forecast:** [amount] | **Gap:** [amount] | **Coverage:** [%]

## Deals at Risk

| Company   | Stage   | Last Activity | Risk                            |
| --------- | ------- | ------------- | ------------------------------- |
| [company] | [stage] | [date]        | [No activity / Past close date] |

## Notes

- [Any assumptions or data quality flags]
```

## After This Skill

- **sales-deal-tracker** — update a specific deal that's driving risk → Read `skill-packs/sales-revenue/skills/sales-deal-tracker.md`

## Rules

- Use conservative probability defaults unless deal-level overrides are confirmed.
- Flag deals with no activity in 14+ days before including them in the forecast.
- Never show a forecast without pipeline data. If pipeline.md doesn't exist, ask the user to run deal-tracker first.
- State all assumptions explicitly in the Notes section.
- Never fabricate deal values or pipeline figures.
