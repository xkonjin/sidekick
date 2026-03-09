---
name: workflow-builder
description: "Create reusable automated workflows by chaining existing skills with triggers, conditions, and outputs. Trigger when the user says 'automate this', 'build a workflow', 'when X happens do Y', 'recurring task', or 'every Monday'."
---

# Workflow Builder

Turns a recurring pattern into a defined workflow: a trigger, a skill chain, conditions, and an output destination. Reduces cognitive overhead for work you do on a predictable schedule.

## Process

### Step 1: Load Context

Read these files:

- `CLAUDE.md` - The current Skills table to understand what skills are available
- `sidekick/context/current-priorities.md` - Which recurring tasks matter most

### Step 2: Define the Workflow

If not specified, ask:

- What triggers this workflow? (A time, an event, an incoming message, or manual)
- What's the goal? (What should be different after the workflow runs?)
- Are there any conditions or exceptions? (e.g., "only on weekdays", "only if there's a new meeting")

Skip questions if the user's message already answers them.

### Step 3: Map the Skill Chain

Identify which existing skills in the Skills table handle each step of the workflow. Sequence them. Note where one skill's output feeds the next as input.

If a step requires a skill that isn't installed, note the gap and suggest which pack to add.

### Step 4: Write the Workflow Definition

Add the workflow to the `## Scheduled Tasks` or `## Automated Workflows` section of `CLAUDE.md`. If neither section exists, create `## Automated Workflows` at the bottom.

```markdown
### [Workflow Name]

**Trigger:** [time / event / manual]
**Condition:** [optional: "only if..." or "skip when..."]

**Steps:**

1. [Step 1]: Read [source] → Run [skill]
2. [Step 2]: Use output from step 1 → Run [skill]
3. [Output]: Save to [destination] / Present to user

**Output location:** [file path or "present to user"]
```

### Step 5: Confirm Before Writing

Show the workflow definition to the user and ask: "Does this match what you had in mind?"

Only write to CLAUDE.md after confirmation.

## After This Skill

| If...                                           | Suggest...                                                    |
| ----------------------------------------------- | ------------------------------------------------------------- |
| A skill needed in the chain isn't installed yet | Read `skill-packs/meta-system/skills/meta-skill-suggester.md` |

## Rules

- Only chain skills that exist in the Skills table or are being installed alongside this workflow.
- Do not write to CLAUDE.md without explicit user confirmation.
- Every workflow needs an output destination. "Nothing" is not a valid output - if nothing is saved, clarify what the user will do with the result.
- Never fabricate. If you can't find it, say so.
