---
name: status-report
description: "Generate a formatted progress update covering done, in-progress, blocked, and next steps. Trigger when the user says 'status report', 'standup prep', 'update for [person]', or 'progress update'."
---

# Status Report

Generates a structured progress update organized around your stated priorities. Calibrated to the audience and matched to your communication style.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - Structure the report around these, not a random activity list
- `sidekick/context/communication-style.md` - Match tone and format to your voice
- `sidekick/context/working-preferences.md` - Length, bullet preference, sign-off style (if it exists)
- `sidekick/context/team-directory.md` - Context on the recipient (affects formality and detail level)
- `sidekick/TASKS.md` - Source of truth for what's in-progress and completed

### Step 2: Clarify Scope

If not specified, ask:

- Who is this for? (Affects formality and what to include vs. omit)
- What time period does it cover? (Today, this week, since last update)
- Any specific projects or priorities to focus on?

### Step 3: Gather Activity

Scan available sources for the period:

**TASKS.md:** Completed items, in-progress items, blocked items.

**Calendar (if connected):** Key meetings that produced decisions or outputs.

**Messaging (if connected):** Decisions made async, things shipped or announced.

If tools aren't connected, ask the user to confirm what to include.

### Step 4: Generate the Report

Structure around priorities, not chronology.

```markdown
# [Status Report / Standup / Update for [Person]] - [Date]

## Done

- [Completed item tied to a priority]
- [Completed item tied to a priority]

## In Progress

- [Item]: [current state, expected completion]
- [Item]: [current state, expected completion]

## Blocked

- [Item]: blocked by [who/what], since [date], [impact if not resolved]

## Next

- [What you're working on next, in priority order]

## Asks

- [Anything you need from the recipient or others]
```

Adjust length and formality based on who it's for:

- Peer standup: brief, bullet-forward
- Manager update: slightly more context on why items matter
- Cross-functional: include priority context so they understand relative importance

### Step 5: Review Before Sharing

Present the draft. Ask: "Anything to add, remove, or adjust before you share this?"

Never post or send the report. The user decides where it goes.

## Rules

- Always organize around priorities. If an activity doesn't tie to a stated priority, put it at the bottom or omit it.
- If a priority had no progress, include it and say so. Don't hide stalled priorities.
- Match tone to communication-style.md (if it exists). A status report that doesn't sound like the user will get edited anyway.
- Keep it scannable. The recipient should get the picture in under 2 minutes.
- Avoid banned words from working-preferences.md (if it exists).
