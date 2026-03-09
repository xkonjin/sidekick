---
name: cs-escalation-handler
description: "Structure an escalation response for an urgent customer issue. Trigger when the user says 'escalation', 'customer escalation', or 'angry customer'."
---

Produces an escalation brief covering severity classification, timeline, internal and external communication plans, resolution tracking, and post-resolution review. Sets follow-up checkpoints.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/memory/accounts/[customer].md` - load account history, health, and contacts (if it exists)
- `sidekick/context/team-directory.md` - identify the right internal owner and escalation path

### Step 2: Clarify the Escalation

If the user hasn't specified, ask:

- What happened? Describe the issue.
- How severe is it? (system down, data loss, SLA breach, relationship risk, other)
- Who is affected and how many users?

Skip questions if the user's message already answers them.

### Step 3: Classify Severity

| Level | Criteria                                            | Response target |
| ----- | --------------------------------------------------- | --------------- |
| P1    | System down, data loss, significant business impact | Immediate       |
| P2    | Major feature broken, deadline at risk              | Same day        |
| P3    | Significant frustration, workaround exists          | 24-48 hours     |
| P4    | Relationship friction, no operational impact        | This week       |

### Step 4: Build the Escalation Brief

Produce the output below. Set explicit follow-up checkpoints.

### Step 5: Save Output

Write to `sidekick/outputs/escalation-[customer]-[DATE].md`. Update `sidekick/memory/accounts/[customer].md` with a note.

## Output Format

```markdown
# Escalation: [Customer Name] — [DATE]

**Severity:** P[1/2/3/4] | **Issue owner:** [Name] | **Exec sponsor:** [Name if needed]

## What Happened

[2-3 sentences. What broke, when, what's the customer impact?]

## Timeline

| Time   | Event                               |
| ------ | ----------------------------------- |
| [time] | [What happened or was communicated] |

## Stakeholders

| Name   | Role   | Internal / External |
| ------ | ------ | ------------------- |
| [name] | [role] | [internal/external] |

## Internal Communication Plan

- [Who needs to know internally and by when]
- [Escalation path if not resolved by X]

## External Communication Plan

- **Immediate message:** [What to tell the customer now]
- **Update cadence:** [How often to check in until resolved]
- **Resolution message:** [Template for when it's fixed]

## Resolution Tracking

| Action   | Owner  | Status | Due    |
| -------- | ------ | ------ | ------ |
| [action] | [name] | Open   | [date] |

## Follow-Up Checkpoints

- [DATE + TIME]: [First check-in]
- [DATE + TIME]: [Escalation trigger if not resolved]

## Post-Resolution Review

**Scheduled:** [date] | **Goal:** prevent recurrence
```

## After This Skill

- **email-drafter** — draft the customer-facing communication → Read `skill-packs/automation/skills/auto-email-drafter.md`
- **blocker-audit** — surface any related blockers stalling resolution → Read `skill-packs/automation/skills/auto-blocker-audit.md`
- **cs-account-health** — update account health after resolution → Read `skill-packs/customer-success/skills/cs-account-health.md`

## Rules

- Always define severity level before any other step. It determines the response speed.
- Internal and external communication plans are both mandatory. Silence is not a plan.
- Set explicit follow-up checkpoints with times, not just "check back later."
- Never fabricate resolution steps or commitments. Only include what the team can actually deliver.
