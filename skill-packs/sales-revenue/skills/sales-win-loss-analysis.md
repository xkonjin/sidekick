---
name: sales-win-loss-analysis
description: "Run a structured post-deal review. Trigger when the user says 'win loss', 'why did we lose', or 'deal review' after a deal closes."
---

Produces a structured analysis of what happened in a deal: timeline, what worked, what didn't, competitor involvement, and systemic takeaways. No spin on losses.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/memory/deals/[company].md` - load full deal history including stage changes and contacts (if it exists)
- `sidekick/memory/competitors/` - check if competitors were involved (if it exists)
- `sidekick/memory/objection-bank.md` - note which objections appeared in this deal (if it exists)

### Step 2: Clarify the Deal Outcome

If the user hasn't specified, ask:

- Which deal is this for?
- What was the outcome? (Won / Lost / No decision)
- What do you believe were the key factors?

Skip questions if the user's message already answers them.

### Step 3: Build the Analysis

Reconstruct the deal timeline from available data. Identify what drove the outcome. Separate deal-specific factors from systemic patterns.

### Step 4: Update Downstream Memory

- Save analysis to `sidekick/outputs/win-loss-[company]-[DATE].md`
- Update `sidekick/memory/objection-bank.md` with any new objection patterns
- Note systemic findings in `sidekick/memory/decisions.md` if they should inform process changes

## Output Format

```markdown
# Win/Loss Analysis: [Company] — [Outcome]

**Date closed:** [DATE] | **Deal value:** [amount] | **Sales cycle:** [duration]

## Timeline

| Date   | Event                                              |
| ------ | -------------------------------------------------- |
| [date] | [Stage change, key interaction, or decision point] |

## What Worked

- [Specific tactic, message, or move that helped]

## What Didn't Work

- [Specific gap, mistake, or missed signal]

## Competitor Involvement

**Competitors evaluated:** [names or "none identified"]

[What role did competitors play in the outcome?]

## Decision Factors

| Factor   | Weight       | Our Performance |
| -------- | ------------ | --------------- |
| [factor] | High/Med/Low | Strong/Weak/N/A |

## Systemic Takeaways

- [Pattern that applies beyond this deal — process, messaging, or positioning]

## Recommended Actions

- [Concrete change to make based on this review]
```

## After This Skill

- **decision-log** — log any process changes that should stick → Read `skills/decision-log/SKILL.md`
- **sales-objection-bank** — update the objection library with new patterns → Read `skill-packs/sales-revenue/skills/sales-objection-bank.md`

## Rules

- Be honest about losses. No spin. The analysis is only useful if it's accurate.
- Distinguish deal-specific factors (this prospect was unusual) from systemic ones (we always lose on price).
- Never fabricate deal activity that isn't in the source files or confirmed by the user.
- If the deal file doesn't exist, ask the user to walk through the timeline before analyzing.
