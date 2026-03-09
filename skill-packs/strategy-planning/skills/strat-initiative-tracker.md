---
name: initiative-tracker
description: "Track multi-team initiatives that span multiple project files with status, owners, and blockers. Trigger when the user says 'initiative tracker', 'track this initiative', 'cross-cutting project', or 'program status'."
---

# Initiative Tracker

Creates a persistent tracking record for initiatives that span multiple teams, projects, or workstreams. Prevents cross-functional work from falling through the cracks between individual project files.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - Which priorities this initiative supports
- `sidekick/context/team-directory.md` - People involved across teams
- `sidekick/context/working-preferences.md` - Preferred update format (if it exists)
- `sidekick/memory/decisions.md` - Decisions that govern this initiative (if it exists)
- `sidekick/memory/projects/` - Individual project files that are workstreams within this initiative
- `sidekick/TASKS.md` - In-flight tasks that belong to this initiative

### Step 2: Define the Initiative

If not specified, ask:

- What is the initiative name?
- Which projects or workstreams are part of it?
- Who is the initiative owner? Who are the workstream leads?
- What is the target completion or key milestone?

Skip questions if the user's message already answers them.

### Step 3: Build the Tracker

**Workstreams:** Map each sub-project to an owner, status, and milestone.

**Blockers:** Surface cross-workstream dependencies and blockers from TASKS.md and project files.

**Decisions pending:** Flag any decisions that are holding up multiple workstreams.

**Progress:** Synthesize current state across all workstreams into a single status assessment.

### Step 4: Generate Output

Save to `sidekick/memory/initiatives/[name].md`.

```markdown
# Initiative: [Name]

**Updated:** [date] | **Owner:** [name] | **Target:** [date or milestone]
**Status:** [On track / At risk / Blocked / Complete]

## Objective

[1-2 sentences: what does success look like for this initiative?]

## Workstreams

| Workstream | Owner   | Status                         | Next Milestone | Milestone Date | Blockers          |
| ---------- | ------- | ------------------------------ | -------------- | -------------- | ----------------- |
| [name]     | [owner] | [On track / At risk / Blocked] | [milestone]    | [date]         | [blocker or none] |

## Cross-Workstream Blockers

| Blocker   | Affects       | Owner             | Since  | Recommended Action |
| --------- | ------------- | ----------------- | ------ | ------------------ |
| [blocker] | [workstreams] | [who resolves it] | [date] | [action]           |

## Pending Decisions

| Decision   | Needed by | Who decides | Impact if delayed |
| ---------- | --------- | ----------- | ----------------- |
| [decision] | [date]    | [name]      | [impact]          |

## Change Log

| Date   | Update         |
| ------ | -------------- |
| [date] | [what changed] |
```

## After This Skill

| If...                                      | Suggest...                                                 |
| ------------------------------------------ | ---------------------------------------------------------- |
| Blockers need immediate escalation         | Read `skill-packs/automation/skills/auto-blocker-audit.md` |
| A status update is needed for stakeholders | Read `skill-packs/automation/skills/auto-status-report.md` |

## Rules

- Only track workstreams that can be sourced from existing project files or user-provided information. Don't invent workstream status.
- Update the Change Log every time this tracker is refreshed. Date every entry.
- If a workstream has no owner, flag it - unowned work does not get done.
- Never fabricate. If you can't find it, say so.
