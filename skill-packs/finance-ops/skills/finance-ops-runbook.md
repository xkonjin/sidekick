---
name: ops-runbook
description: "Create an operational runbook for handling a specific situation: when it triggers, who responds, exact steps, escalation path, and resolution criteria. Trigger when the user says 'runbook', 'how to handle', 'standard procedure', 'when X happens do Y', or 'playbook for'."
---

# Ops Runbook

Produces a step-by-step runbook for handling a specific operational scenario: trigger conditions, response steps, escalation paths, and resolution criteria.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/team-directory.md` - Who can be assigned as responders
- `sidekick/context/current-priorities.md` - Understand severity relative to current work

### Step 2: Define the Scenario

If not specified, ask:

- What situation does this runbook cover?
- How do you know it's happening? (trigger / alert / signal)
- Who is the first responder? (role, not just a name)
- What's the severity level? (P1 drop-everything vs P3 handle-when-available)
- Has this happened before? What went wrong last time?

### Step 3: Build the Runbook

For each phase of the response, capture:

- **Trigger** — What signals that this scenario is active
- **Assessment** — How to confirm severity and scope within the first 5 minutes
- **Response steps** — Numbered steps with specific actions, not vague guidance
- **Escalation criteria** — When to escalate and to whom
- **Communication** — Who to notify, through what channel, with what message
- **Resolution criteria** — How to confirm the situation is resolved
- **Post-incident** — What to document after resolution

### Step 4: Write and Save

Write to `sidekick/memory/runbooks/[scenario-name].md`. Create the directory if it doesn't exist.

```markdown
# Runbook: [Scenario Name]

**Last updated:** [date] | **Owner:** [role]
**Severity:** [P1/P2/P3] | **Expected resolution time:** [timeframe]

## Trigger

[What signals that this scenario is happening. Be specific: alert name, metric threshold, user report pattern.]

## Assessment (first 5 minutes)

1. [Check X to confirm the issue is real]
2. [Check Y to determine scope]
3. [Classify severity: P1 if [criteria], P2 if [criteria], P3 if [criteria]]

## Response Steps

| Step | Action | Owner | Tool / System | Time Limit |
|------|--------|-------|---------------|------------|
| 1 | [Specific action] | [Role] | [Tool] | [time] |
| 2 | [Specific action] | [Role] | [Tool] | [time] |

## Escalation

| Condition | Escalate To | Channel | Within |
|-----------|-------------|---------|--------|
| [When to escalate] | [Role/person] | [Slack/phone/page] | [timeframe] |

## Communication

| Audience | Channel | When | Template |
|----------|---------|------|----------|
| [Internal team] | [Slack channel] | [Immediately / after assessment] | "[Template message]" |
| [Stakeholders] | [Email / Slack] | [After resolution] | "[Template message]" |

## Resolution Criteria

- [ ] [Specific condition that means this is resolved]
- [ ] [Metrics returned to normal range]
- [ ] [Affected parties notified]

## Post-Incident

1. Document what happened in [location]
2. Update this runbook if the response was suboptimal
3. Schedule post-mortem if severity was P1
```

## After This Skill

- **postmortem** — if the incident already happened and needs analysis → Read `skill-packs/engineering/skills/dev-postmortem.md`
- **process-mapper** — if the runbook reveals a process that needs formal documentation → Read `skill-packs/finance-ops/skills/finance-process-mapper.md`

## Rules

- Every step must be a specific action, not a vague instruction. "Investigate the issue" is not a step. "Check CloudWatch dashboard for error rate spike above 5%" is.
- Use role names, not personal names. Runbooks outlive individuals.
- Escalation section is mandatory. A runbook without escalation criteria is incomplete.
- Time limits are required for every step. Response without time pressure is not a response.
- If this runbook is based on a past incident, reference it. If hypothetical, note that it hasn't been battle-tested.
