---
name: vendor-evaluator
description: "Evaluate and compare vendors or tools against defined requirements. Trigger when the user says 'evaluate vendor', 'compare vendors', 'vendor selection', 'which tool', or 'buy vs build'."
---

# Vendor Evaluator

Structured vendor evaluation: define requirements, score options against them, compare pricing, and produce a recommendation with a clear rationale.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/current-priorities.md` - Understand what the vendor must support
- `sidekick/memory/decisions.md` - Check if a prior decision touched this vendor category

### Step 2: Define the Evaluation

Ask if not specified:

- What problem is this vendor solving? (one sentence)
- What are the must-have requirements? (non-negotiable)
- What are the nice-to-have requirements?
- Which vendors or options are being evaluated?
- Is buy vs. build also on the table?
- What is the budget range or ceiling?
- Who is the decision maker and what is the timeline?

### Step 3: Score Each Option

For each vendor, score every requirement on a 1-3 scale:

- **3** — Fully meets the requirement
- **2** — Partially meets or requires workaround
- **1** — Does not meet; would require custom development
- **0** — Explicitly not supported

Weight must-haves higher than nice-to-haves in the final score.

### Step 4: Output the Evaluation

Save to `sidekick/outputs/vendor-eval-[name]-[DATE].md`.

```markdown
# Vendor Evaluation: [Category / Use Case]

**Date:** [date] | **Decision owner:** [name]
**Budget ceiling:** [amount] | **Decision deadline:** [date]

## Problem Statement

[One sentence: what are we buying this to solve?]

## Requirements

| Requirement   | Type         | Weight |
| ------------- | ------------ | ------ |
| [Requirement] | Must-have    | 3x     |
| [Requirement] | Nice-to-have | 1x     |

## Scorecard

| Requirement        | [Vendor A] | [Vendor B] | [Vendor C] | Build   |
| ------------------ | ---------- | ---------- | ---------- | ------- |
| [Requirement]      | 3          | 2          | 1          | 2       |
| ...                |            |            |            |         |
| **Weighted Total** | [score]    | [score]    | [score]    | [score] |

## Pricing Comparison

| Vendor     | Pricing model | Cost (monthly) | Cost (annual) | Notes            |
| ---------- | ------------- | -------------- | ------------- | ---------------- |
| [Vendor A] | [model]       | [amount]       | [amount]      | [contract terms] |

## Reference Check Questions

For shortlisted vendors, ask their references:

- How long have you used this and what were the first 90 days like?
- What has broken or disappointed you?
- What does support response look like in practice?
- Would you buy it again?

## Buy vs. Build Assessment

| Factor            | Buy                         | Build                  |
| ----------------- | --------------------------- | ---------------------- |
| Upfront cost      | [amount]                    | [estimate]             |
| Time to value     | [weeks]                     | [months]               |
| Ongoing cost      | [subscription]              | [maintenance estimate] |
| Strategic control | Dependent on vendor roadmap | Full control           |
| Recommendation    | [Buy / Build / Hybrid]      |                        |

## Recommendation

**Recommended:** [Vendor name or Build]
**Rationale:** [2-3 sentences. Why this option, why not the others.]
**Conditions:** [Any conditions that must be true for this recommendation to hold, e.g. "only if pricing is negotiated below X"]
```

## After This Skill

- **decision-log** — log the vendor selection decision → Read `skills/decision-log/SKILL.md`
- **budget-tracker** — record the new vendor spend against the budget → Read `skill-packs/finance-ops/skills/finance-budget-tracker.md`

## Rules

- Requirements must be defined before scoring. Do not score vendors against vague criteria.
- Must-have requirements with a score of 1 or 0 should disqualify the vendor, regardless of total score.
- Never recommend a vendor based on brand name or familiarity alone.
- If pricing is unavailable, note "Unknown — request quote" rather than estimating.
- The buy vs. build section is mandatory when build is a realistic option.
