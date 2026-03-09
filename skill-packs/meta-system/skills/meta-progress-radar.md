---
name: meta-progress-radar
description: "Scan projects and priorities against timelines to produce a red/yellow/green status radar. Trigger when the user says 'how am I doing', 'progress check', 'am I on track', or 'are we slipping'."
---

# Progress Radar

Scans everything in flight and gives you an honest read: what's on track, what's at risk, what's stalled. Evidence-based status only. No vibes.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - What the work is supposed to serve
- `sidekick/TASKS.md` - In-flight and blocked tasks (if it exists)
- `sidekick/memory/projects/` - Project files with status, timelines, and owners

Also scan `sidekick/outputs/` for recent weekly-update files to understand recent pace (if any exist).

### Step 2: Build the Radar

Run from available data. Ask nothing.

For each priority and active project:

**Status color:**
- Green: on track, last activity recent, no blocking issues
- Yellow: slowing, behind plan, or a dependency is at risk
- Red: blocked, no recent activity, or projected to miss the deadline

**Trend arrow:**
- Up: accelerating or ahead of plan
- Flat: steady pace
- Down: slowing or losing momentum

**Time since last activity:** Pull from project files or task updates. Flag anything with no activity in 7+ days.

**Projected completion:** Based on current pace, when will this actually finish? Compare to stated target.

### Step 3: Generate Output

Save to `sidekick/outputs/progress-radar-[DATE].md`.

```markdown
# Progress Radar: [DATE]

## Priority Status

| Priority | Status | Trend | Last Activity | On Track? | Risk |
|----------|--------|-------|---------------|-----------|------|
| [priority] | 🟢 / 🟡 / 🔴 | ↑ / → / ↓ | [days ago] | [Yes / At risk / No] | [key risk or none] |

## Project Status

| Project | Status | Trend | Owner | Target Date | Projected Completion | Blocker |
|---------|--------|-------|-------|-------------|---------------------|---------|
| [project] | 🟢 / 🟡 / 🔴 | ↑ / → / ↓ | [name] | [date] | [projected date] | [blocker or none] |

## Flags

**Priorities with zero activity:**
- [Priority with no movement and how long it's been stalled]

**Projects off track:**
- [Project]: projected [projected date] vs target [target date]. Gap: [X days/weeks].

**Overdue tasks:**
- [Task]: was due [date], still open.

## Overall Read

[2-3 sentences: honest characterization of where things stand. Are you ahead, behind, or scattered?]
```

## After This Skill

| If... | Suggest... |
|-------|-----------|
| Quarter planning needs to account for slippage | Read `skill-packs/strategy-planning/skills/strat-quarterly-plan.md` |
| Blockers need active escalation | Read `skill-packs/automation/skills/auto-blocker-audit.md` |

## Rules

- Status colors must be based on evidence: activity dates, milestone dates, blocker records. Not on how things feel.
- Flag priorities with zero activity explicitly. Unstated deprioritization is a decision that should be surfaced.
- Compare stated timeline to actual pace. If the pace doesn't support the deadline, say so.
- Never fabricate project status. If no project file exists, note the gap rather than guessing.
- Never fabricate. If you can't find it, say so.
