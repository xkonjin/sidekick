---
name: meta-context-handoff
description: "Generate a comprehensive context document for handing off a project or role to someone else. Trigger when the user says 'hand this off', 'bring someone up to speed', 'context transfer', or 'transition doc'."
---

# Context Handoff

Produces a complete context document for handing off a project, role, or area of work. Captures what's known, what's been decided, what's in flight, and what would trip up someone coming in cold.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/team-directory.md` - People involved and who the new owner will work with
- `sidekick/context/current-priorities.md` - What the work is serving
- `sidekick/memory/decisions.md` - Key decisions made and their rationale (if it exists)
- `sidekick/memory/projects/` - Project files relevant to the handoff
- `sidekick/TASKS.md` - In-flight and blocked tasks (if it exists)

Also scan outputs for recent deliverables relevant to the topic (if any exist).

### Step 2: Clarify the Handoff

If not specified, ask:

- What is being handed off? (project, role, area of work)
- Who is receiving it? (level of detail changes based on their starting context)
- Is this a permanent transfer or a temporary cover?

Skip questions if the user's message already answers them.

### Step 3: Build the Document

**Background:** What is this work, why does it exist, what problem does it solve?

**Current state:** What's done, what's in progress, what's blocked?

**Key decisions:** Not just what was decided, but why. Include alternatives that were rejected.

**Open items:** Tasks, questions, and commitments that the new owner must pick up.

**Contacts:** Who to call for what. Note relationship nuances from team-directory.md.

**Pitfalls:** What a reasonable person would get wrong when coming in cold.

**Tribal knowledge:** Things that exist only in someone's head, not in any document.

### Step 4: Save the Document

Save to `sidekick/outputs/handoff-[topic]-[DATE].md`.

```markdown
# Handoff: [Topic]

**Date:** [date] | **From:** [user's name] | **To:** [recipient]
**Type:** [permanent / temporary cover until [date]]

## What This Is

[2-3 sentences: what the work is, why it matters, what success looks like]

## Current State

**Done:**
- [completed items]

**In progress:**
- [active work with status]

**Blocked:**
- [blocked items with blocker named]

## Key Decisions (and Why)

| Decision | Rationale | Alternatives Rejected |
|----------|-----------|-----------------------|
| [decision] | [why] | [what was considered and rejected] |

## Open Items

| Item | Owner | Priority | Due | Notes |
|------|-------|----------|-----|-------|
| [task] | [new owner / TBD] | [H/M/L] | [date] | [context] |

## Key Contacts

| Person | Role | What to go to them for | Relationship notes |
|--------|------|------------------------|--------------------|
| [name] | [role] | [when to contact] | [any nuance] |

## Watch Out For

- [Pitfall 1: what a reasonable person gets wrong]
- [Pitfall 2]

## Things Not Written Down Anywhere

- [Tribal knowledge item 1]
- [Tribal knowledge item 2]
```

## After This Skill

| If... | Suggest... |
|-------|-----------|
| People management pack is installed and a direct report is involved | Read `skill-packs/people-management/skills/mgmt-delegation-planner.md` |

## Rules

- Decision rationale is mandatory. Handing off conclusions without reasoning forces the recipient to re-litigate every decision.
- Flag undocumented tribal knowledge explicitly. If it exists only in someone's head, name it.
- Tailor detail level to the recipient. A peer needs less background than someone external.
- Never fabricate. If you can't find it, say so.
