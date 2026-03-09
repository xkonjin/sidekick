---
name: data-anomaly-brief
description: "Investigate a data anomaly: observation, timeline, ranked causes, impact assessment, and monitoring plan. Trigger when the user says 'something looks off', 'spike in', 'drop in', 'data anomaly', or 'why did [metric] change'."
---

# Anomaly Brief

Structures anomaly investigations so they don't jump to conclusions. Always considers multiple causes — including the possibility the data source itself is broken.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/memory/metrics/` (if any exist) - understand the metric definition and known edge cases
- `sidekick/memory/projects/` (if any exist) - identify recent changes that could explain the shift
- `sidekick/memory/decisions.md` (if it exists) - check for recent decisions that might have caused the movement

### Step 2: Clarify

Ask for anything not already provided:

- What changed, and by how much?
- When did you first notice it?
- What is the business impact?

Skip questions if the user's message already answers them.

### Step 3: Check the Data Source First

Before investigating business causes, verify the data is real:

- Is the tracking or pipeline working correctly?
- Did anything change in how this metric is calculated?
- Are there gaps in the raw data (nulls, duplicate events, missing time periods)?

Flag this prominently if the data source may be broken.

### Step 4: Draft the Anomaly Brief

```markdown
# Anomaly Brief: [Metric] — [DATE]

**Reported by:** [Name] | **Impact level:** [Critical / High / Low]

## Observation

[What changed, by how much, over what period. Include the specific numbers.]

## Timeline

| Time       | Event                                               |
| ---------- | --------------------------------------------------- |
| [datetime] | [When the anomaly started]                          |
| [datetime] | [Related product change, deploy, or external event] |
| [datetime] | [When it was first noticed / reported]              |

## Data Integrity Check

- [ ] Tracking events firing correctly
- [ ] No pipeline outages or data gaps in this period
- [ ] Metric definition unchanged
- [ ] **Verdict:** [Data appears valid / Data source may be broken — investigate before proceeding]

## Possible Causes

| Cause                      | Likelihood   | Evidence for / against         |
| -------------------------- | ------------ | ------------------------------ |
| [Most likely cause]        | High         | [Supporting signal]            |
| [Second most likely]       | Medium       | [Supporting signal]            |
| [Less likely but possible] | Low          | [Why it can't be ruled out]    |
| Data source broken         | [likelihood] | [Check result from step above] |

## Impact Assessment

- **Users affected:** [Number or segment]
- **Revenue / business impact:** [If quantifiable]
- **Priority it threatens:** [Link to current-priorities.md]

## How to Know if This Is a False Alarm

[What signal or check would confirm the data is fine and this is noise, not a real problem]

## Recommended Actions

| Action                      | Owner  | Due    | Priority |
| --------------------------- | ------ | ------ | -------- |
| [Investigate leading cause] | [Name] | [date] | High     |
| [Monitor for X days]        | [Name] | [date] | Med      |

## Monitoring Plan

[How will we know when this is resolved? What metric threshold signals recovery?]
```

### Step 5: Save

Save to `sidekick/outputs/anomaly-brief-[topic]-[DATE].md`.

## After This Skill

| Condition                                         | Suggestion                                                                                               |
| ------------------------------------------------- | -------------------------------------------------------------------------------------------------------- |
| A decision is made based on the investigation     | **decision-log** → `skills/decision-log/SKILL.md`                                                        |
| Anomaly reveals a blocked priority                | **blocker-audit** → `skill-packs/automation/skills/auto-blocker-audit.md` (if automation pack installed) |
| Metric needs a formal definition before next time | **metric-definer** → `skill-packs/data-analytics/skills/data-metric-definer.md`                          |

## Rules

- Always list multiple possible causes — never jump to one explanation before ruling out others
- Check the data source first; a broken pipeline is often the real cause
- Include "how would we know if this is a false alarm" — prevents over-reacting to noise
- Never fabricate causal explanations; use "unknown — requires investigation" if evidence is absent
- Flag when the impact is unquantifiable rather than estimating without data
