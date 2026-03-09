---
name: data-dashboard-spec
description: "Design a dashboard: metrics grouped by theme, layout, comparisons, drill-downs, refresh cadence, and alert thresholds. Trigger when the user says 'dashboard spec', 'what should be on the dashboard', 'design a dashboard', or 'dashboard layout'."
---

# Dashboard Spec

Designs dashboards that drive action, not dashboards that accumulate metrics. Every number on the page must have a clear action when it moves.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/memory/metrics/` (if any exist) - use formally defined metrics, not informal descriptions
- `sidekick/context/current-priorities.md` - metrics on the dashboard should connect to active priorities

### Step 2: Clarify

Ask for anything not already provided:

- Who uses this dashboard? (exec, team lead, analyst, ops)
- What questions should someone be able to answer in under 30 seconds?
- What time ranges matter? (daily, weekly, rolling 30-day)

Skip questions if the user's message already answers them.

### Step 3: Flag Vanity Metrics

Before writing the spec, review requested metrics and flag any that:

- Can't be acted on when they move
- Are outputs (page views, emails sent) not outcomes
- Would look good in a board deck but don't drive decisions

### Step 4: Draft the Dashboard Spec

```markdown
# Dashboard Spec: [Dashboard Name]

**Owner:** [Name] | **Primary audience:** [Role] | **Last updated:** [DATE]

## Purpose

[One sentence: what decisions does this dashboard support?]

## Metrics

### Theme 1: [Group name — e.g., Acquisition]

| Metric        | Definition ref                   | Comparison       | Alert threshold | Action if breached |
| ------------- | -------------------------------- | ---------------- | --------------- | ------------------ |
| [Metric name] | [sidekick/memory/metrics/[file]] | [vs. prior week] | [< X or > Y]    | [Who does what]    |

### Theme 2: [Group name — e.g., Engagement]

| Metric | Definition ref | Comparison | Alert threshold | Action if breached |
| ------ | -------------- | ---------- | --------------- | ------------------ |

### Theme 3: [Group name — e.g., Revenue]

| Metric | Definition ref | Comparison | Alert threshold | Action if breached |
| ------ | -------------- | ---------- | --------------- | ------------------ |

## Layout
```

[Row 1: headline metrics — 3-4 big numbers, most important]
[Row 2: trend charts — key metrics over time]
[Row 3: segment breakdowns or drill-downs]
[Row 4: supporting / diagnostic metrics]

```

## Drill-Downs

| Top-level metric | Drill-down available | By dimension          |
| ---------------- | -------------------- | --------------------- |
| [Metric]         | Yes / No             | [Country, plan, cohort] |

## Refresh Cadence

| Data type   | Refresh rate | Source                |
| ----------- | ------------ | --------------------- |
| [Event data] | Real-time   | [System]              |
| [Aggregates] | Daily       | [System]              |

## Flagged Vanity Metrics (excluded)

- [Metric name] — reason: [why it was excluded]
```

### Step 5: Save

Save to `sidekick/outputs/dashboard-spec-[name]-[DATE].md`.

## After This Skill

| Condition                                        | Suggestion                                                                      |
| ------------------------------------------------ | ------------------------------------------------------------------------------- |
| A metric on the dashboard isn't formally defined | **metric-definer** → `skill-packs/data-analytics/skills/data-metric-definer.md` |
| Dashboard shows an unexpected move               | **anomaly-brief** → `skill-packs/data-analytics/skills/data-anomaly-brief.md`   |

## Rules

- Every metric on the dashboard must have a defined action when it moves — "interesting" is not an action
- Limit to 7-10 metrics per view; more than that and nothing gets attention
- Flag vanity metrics explicitly and explain why they were excluded
- Never fabricate metric definitions; reference `sidekick/memory/metrics/` or ask the user to define first
- Drill-down capability must be confirmed available, not assumed
