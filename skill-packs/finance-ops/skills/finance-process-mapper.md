---
name: process-mapper
description: "Document a business process: steps, owners, tools, handoffs, SLAs, and failure modes. Trigger when the user says 'map this process', 'how does X work', 'document the workflow', or 'process documentation'."
---

# Process Mapper

Produces clear process documentation: every step, who owns it, what tool is used, where handoffs happen, how long it should take, and what breaks it.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/team-directory.md` - Confirm role names and who owns what

### Step 2: Identify the Process

If not specified, ask:

- What process are we documenting?
- Where does it start and where does it end?
- Who are the participants? (roles or specific people)
- Does a version of this process already exist somewhere?

### Step 3: Map the Process

Walk through the process step by step. For each step, capture:

- What action is performed
- Who performs it (role, not just a name)
- What tool or system is used
- What triggers the step (previous step output, a schedule, an event)
- What the output is (what moves to the next step)
- SLA — how long this step should take
- Failure mode — what breaks here and what the fallback is

### Step 4: Write and Save

Write to `sidekick/memory/processes/[name].md`. Create the directory if it doesn't exist.

```markdown
# Process: [Process Name]

**Last updated:** [date] | **Owner:** [name]
**Scope:** [What initiates this process and what completing it means]
**SLA (end-to-end):** [total expected time from trigger to completion]

## Process Steps

| Step | Action            | Owner  | Tool / System | Trigger              | Output               | SLA    |
| ---- | ----------------- | ------ | ------------- | -------------------- | -------------------- | ------ |
| 1    | [Specific action] | [Role] | [Tool]        | [What triggers this] | [What gets produced] | [time] |
| 2    | [Specific action] | [Role] | [Tool]        | Step 1 complete      | [What gets produced] | [time] |

## Handoffs

| From        | To          | What transfers       | How (channel / tool)   |
| ----------- | ----------- | -------------------- | ---------------------- |
| [Role/Step] | [Role/Step] | [What is handed off] | [Slack / email / tool] |

## Failure Modes

| Step | What breaks        | Likelihood   | Fallback / Recovery            |
| ---- | ------------------ | ------------ | ------------------------------ |
| [n]  | [Specific failure] | High/Med/Low | [What to do when this happens] |

## Notes

- [Any edge cases, exceptions, or context that doesn't fit the table]
```

## After This Skill

- **policy-drafter** — formalize this process as an enforceable internal policy → Read `skill-packs/legal-compliance/skills/legal-policy-drafter.md`
- **blocker-audit** — check if any steps in this process are currently blocked → Read `skill-packs/automation/skills/auto-blocker-audit.md`

## Rules

- Use role names, not personal names, in the process steps. Processes outlive individuals.
- SLA is required for every step. "ASAP" is not an SLA.
- Failure modes section is mandatory. A process without failure modes documented is incomplete.
- If the process is undocumented and the user is describing it from memory, note that it hasn't been validated with all owners.
- When saving, check if `sidekick/memory/processes/` exists. If not, create it.
