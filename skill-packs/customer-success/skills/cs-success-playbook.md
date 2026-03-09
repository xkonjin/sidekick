---
name: cs-success-playbook
description: "Build a repeatable customer success playbook for a segment or lifecycle stage. Trigger when the user says 'success playbook', 'onboarding playbook', or 'adoption plan'."
---

Produces a milestone-based playbook with touchpoints, risk triggers, escalation criteria, and success metrics. Grounded in patterns from successful accounts, not templates.

## Process

### Step 1: Load Context

Read these files before proceeding:

- `sidekick/memory/accounts/` - identify patterns from existing accounts (if it exists)
- `sidekick/memory/projects/` - check for relevant product or launch context (if it exists)
- `sidekick/memory/playbooks/` - check if a playbook for this segment already exists (if it exists)

### Step 2: Clarify the Playbook Scope

If the user hasn't specified, ask:

- Which customer segment or lifecycle stage is this playbook for?
- What does success look like at the end of this stage?

Skip questions if the user's message already answers them.

### Step 3: Build the Playbook

Base the playbook on observed patterns from successful accounts. Flag any milestones or touchpoints that are assumptions rather than evidence.

### Step 4: Save Playbook

Write to `sidekick/memory/playbooks/[segment].md`.

## Output Format

```markdown
# Success Playbook: [Segment / Stage]

**Last updated:** [DATE] | **Based on:** [accounts or data used]

## Definition of Success

[What does a successful customer look like at the end of this stage?]

## Milestones

| Milestone   | Target Timing     | Owner   | Evidence of Completion    |
| ----------- | ----------------- | ------- | ------------------------- |
| [milestone] | [days from start] | [CS/AE] | [what confirms it's done] |

## Touchpoints

| Touchpoint   | Timing | Channel | Goal                            |
| ------------ | ------ | ------- | ------------------------------- |
| [touchpoint] | [when] | [how]   | [what you're trying to achieve] |

## Risk Triggers

| Signal                   | Severity | Response                       |
| ------------------------ | -------- | ------------------------------ |
| [observable risk signal] | High/Med | [what to do when you see this] |

## Escalation Criteria

- Escalate to [role] when: [condition]
- Escalate to [executive] when: [condition]

## Success Metrics

| Metric   | Target  | Measurement method   |
| -------- | ------- | -------------------- |
| [metric] | [value] | [how you measure it] |

## Assumptions (Unvalidated)

- [Any playbook step not yet confirmed by account data]
```

## After This Skill

- **cs-qbr-builder** — use this playbook as the basis for QBR milestone tracking → Read `skill-packs/customer-success/skills/cs-qbr-builder.md`
- **cs-account-health** — apply this playbook's risk triggers to current accounts → Read `skill-packs/customer-success/skills/cs-account-health.md`

## Rules

- Base milestones and touchpoints on observed patterns from successful accounts, not generic templates.
- Flag every untested assumption in the Assumptions section.
- Escalation criteria must name specific roles and conditions — "contact the team" is not an escalation path.
- Never fabricate account data to justify playbook decisions.
