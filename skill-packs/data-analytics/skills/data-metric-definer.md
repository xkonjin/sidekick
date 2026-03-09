---
name: data-metric-definer
description: "Define a metric rigorously: formula, data source, ownership, baseline, target, and edge cases. Trigger when the user says 'define this metric', 'what should we measure', 'KPI definition', or 'how do we track'."
---

# Metric Definer

Turns a vague metric idea into a rigorous spec that two different people would measure the same way.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/context/current-priorities.md` - confirm the metric connects to an active priority
- `sidekick/memory/projects/` (if it exists) - identify which project this metric serves
- `sidekick/context/team-directory.md` - identify who owns the data source

### Step 2: Clarify

Ask for anything not already provided:

- What metric are we defining?
- What decision does this metric inform?
- Who is the primary audience for this metric?

Skip questions if the user's message already answers them.

### Step 3: Draft the Metric Spec

```markdown
# Metric: [Metric Name]

**Last defined:** [DATE] | **Owner:** [Name from team-directory]

## Definition

[One sentence. What does this number represent?]

## Formula
```

[Numerator] / [Denominator] × [Multiplier if applicable]

```

**Example:** [Concrete example with numbers]

## Data Source

| Field         | Detail                              |
| ------------- | ----------------------------------- |
| Source system | [Database, tool, or API]            |
| Table / event | [Specific table or event name]      |
| Granularity   | [Daily / weekly / per-user / etc.]  |
| Refresh rate  | [Real-time / hourly / daily / etc.] |

## Baseline & Target

| Baseline | Current | Target | Timeframe |
| -------- | ------- | ------ | --------- |
| [value]  | [value] | [goal] | [period]  |

## Edge Cases

- [What counts and what doesn't — be explicit]
- [Nulls, duplicates, partial periods]
- [Segment exclusions if any]

## What This Metric Does NOT Capture

- [Important limitation 1]
- [Important limitation 2]

## Related Metrics

- [Metric that should move with this one]
- [Leading or lagging indicator]
```

### Step 4: Save and Confirm

Save to `sidekick/memory/metrics/[metric-slug].md`. Confirm with the user before saving.

## After This Skill

| Condition                                   | Suggestion                                                                          |
| ------------------------------------------- | ----------------------------------------------------------------------------------- |
| User wants to track progress against metric | **dashboard-spec** → `skill-packs/data-analytics/skills/data-dashboard-spec.md`     |
| PM pack installed and metric maps to an OKR | **brainstorm-okrs** → `skill-packs/product-management/skills/pm-brainstorm-okrs.md` |
| Metric shows unexpected movement            | **anomaly-brief** → `skill-packs/data-analytics/skills/data-anomaly-brief.md`       |

## Rules

- Flag any metric name that two people would measure differently — ambiguity here breaks dashboards
- Include what the metric does NOT capture; gaps are as important as what it measures
- Specify who owns the data source — metrics without owners become stale
- Never fabricate baseline numbers; mark as "TBD — measure at launch" if unknown
- If the formula has more than one valid interpretation, document all variants and pick one explicitly
