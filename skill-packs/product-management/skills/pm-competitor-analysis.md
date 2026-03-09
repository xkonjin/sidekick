---
name: pm-competitor-analysis
description: "Deep competitive profile: product, pricing, positioning, strengths, weaknesses, trajectory."
---

Produces a structured competitor profile covering all dimensions relevant to positioning decisions. Designed for ongoing competitive intelligence, not one-shot analysis.

## Context Loading

1. Read `sidekick/context/current-priorities.md` - which priorities does this research serve?
2. Read `sidekick/memory/competitors/` - check if a profile already exists before starting fresh
3. Read `sidekick/context/communication-style.md` - match output style

Ask: "Which competitor and what's driving this research?" before starting.

## Process

1. **Scope the analysis** - full profile vs. specific dimension (pricing, positioning, feature gap)?
2. **Gather signals** - use available search or web tools if connected; note sources
3. **Profile the product** - what does it actually do, for whom, at what price?
4. **Assess positioning** - what story are they telling and to whom?
5. **Identify implications** - what does this mean for us? Don't just describe, analyze.
6. **Save profile** - write to `sidekick/memory/competitors/[name].md` if this is a new or updated profile

## Output Format

```markdown
# Competitor: [Name]

**Last updated:** [date] | **Analyst:** [user name from about-me.md]

## Overview

[2-3 sentences. What do they do, who do they serve, what's their growth story?]

## Product

| Dimension           | Detail |
| ------------------- | ------ |
| Core offering       |        |
| Key differentiators |        |
| Notable features    |        |
| Missing vs us       |        |

## Pricing

| Tier   | Price   | What's included |
| ------ | ------- | --------------- |
| [tier] | [price] | [inclusions]    |

**Pricing model:** [subscription / usage-based / freemium / etc.]

## Positioning

- **Target segment:** [who they say they're for]
- **Primary message:** [what they lead with]
- **Channel emphasis:** [where they show up]

## Strengths

- [Specific, evidence-based strength]
- [Specific, evidence-based strength]

## Weaknesses

- [Specific gap or vulnerability]
- [Specific gap or vulnerability]

## Trajectory

[What direction are they moving? Recent launches, hiring signals, funding, partnerships.]

## Implications for Us

- [Actionable implication 1]
- [Actionable implication 2]

## Sources

- [Source with date]
```

## Rules

- Every strength and weakness must be evidence-based, not assumed
- Implications section is mandatory - pure description is not analysis
- Note data freshness. Stale competitive intel is worse than none.
- If a competitor is already profiled, update the existing file and append to a change log section
