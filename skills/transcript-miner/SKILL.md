---
name: transcript-miner
description: "Deep meeting transcript analysis with signal classification and routing. Activates when the user wants thorough meeting analysis. Detects: 'process meeting', 'mine transcript', 'deep dive on [meeting]', 'what happened in [meeting]', 'analyze the transcript', 'pull out everything from that call', 'what did we cover in [meeting]', 'go through the [meeting] notes carefully'. Automatically chosen over meeting-processor when the user wants depth, detail, or routing to memory files."
---

# Transcript Miner

Deep analysis of meeting transcripts. Classifies signals into categories and routes them to the right memory files.

## Process

### Step 1: Find the Meeting

Use available meeting note tools (Granola, Otter, Fireflies, etc.) to find the meeting:

- If the user specifies a meeting name, search for it
- If no name given, list recent meetings and ask which one
- If the tool returns a summary, also try to get the full transcript for deeper analysis

### Step 2: Load Context

Before analyzing, read these files to understand what matters:

- `sidekick/context/current-priorities.md` - What to evaluate impact against
- `sidekick/context/team-directory.md` - Who these people are
- `sidekick/memory/glossary.md` - Decode internal shorthand
- `sidekick/memory/decisions.md` - Check for contradictions with existing decisions
- `sidekick/context/communication-style.md` - Match output to user's style (if it exists; otherwise match the user's conversational tone)

### Step 3: Classify Signals

Read through the transcript and classify every significant signal:

| Category                  | What to Look For                                                                    | Confidence Required                       |
| ------------------------- | ----------------------------------------------------------------------------------- | ----------------------------------------- |
| **Decisions**             | Explicit "we decided", "let's go with", "the plan is". Must be stated, not implied. | HIGH - must be explicitly stated          |
| **Action Items (User)**   | Tasks assigned to or accepted by the user. "I'll do X", "[Name] can you handle Y"   | HIGH - must be clearly assigned           |
| **Action Items (Others)** | Tasks assigned to other people. Track for follow-up.                                | MEDIUM - may be informal                  |
| **Competitive Mentions**  | References to competitors, their products, pricing, moves                           | MEDIUM                                    |
| **Strategy Shifts**       | Changes in direction, pivots, reprioritization. "Actually, let's focus on..."       | HIGH - distinguish from brainstorming     |
| **Assumption Updates**    | New evidence for or against tracked assumptions                                     | MEDIUM - flag for review                  |
| **People Mentions**       | New people, role changes, org changes                                               | MEDIUM - verify before updating directory |
| **Blockers**              | Things preventing progress. "We can't do X until Y"                                 | HIGH - distinguish blocker from challenge |
| **Dates/Deadlines**       | New or changed deadlines, milestone dates                                           | HIGH - get the exact date                 |

**Classification rules:**

- A **decision** requires explicit statement. "We should probably..." is NOT a decision.
- An **action item** requires clear ownership. "Someone should..." is NOT an action item.
- A **blocker** prevents progress entirely. A **challenge** makes it harder but doesn't stop it.
- A **strategy shift** changes what the team is doing. A **suggestion** is just an idea.

### Step 4: Assess Priority Impact

For each signal, assess impact against the user's current priorities:

| Impact Level | Meaning                                  |
| ------------ | ---------------------------------------- |
| **Direct**   | Directly affects a stated priority       |
| **Adjacent** | Affects something related to a priority  |
| **FYI**      | Good to know but doesn't change anything |

### Step 5: Generate Output

Present the analysis to the user. Format:

```markdown
# Meeting Analysis: [Meeting Name] - [Date]

## Attendees

[List of people in the meeting, with roles from team directory]

## Summary

[3-5 bullet summary of what the meeting was about]

## Decisions

| #   | Decision           | Owner         | Impact                | Confidence    |
| --- | ------------------ | ------------- | --------------------- | ------------- |
| 1   | [What was decided] | [Who owns it] | [Direct/Adjacent/FYI] | [HIGH/MEDIUM] |

## Action Items

### Assigned to You

| #   | Action | Source Quote                    | Due                 | Priority                   |
| --- | ------ | ------------------------------- | ------------------- | -------------------------- |
| 1   | [Task] | "[exact words from transcript]" | [Date if mentioned] | [Based on priority impact] |

### Assigned to Others (for follow-up)

| #   | Action | Owner    | Due                 |
| --- | ------ | -------- | ------------------- |
| 1   | [Task] | [Person] | [Date if mentioned] |

## Competitive Signals

[Any competitor mentions, with context]

## Flags

- [Anything that contradicts an existing decision]
- [Anything that might invalidate a tracked assumption]
- [Anything uncertain that needs verification]

## Priority Impact

[How this meeting affects the user's stated priorities, if at all]
```

### Step 6: Confirm Before Writing

**Show the analysis to the user first. Do not write to any files until they confirm.**

Ask: "Here's what I found. Should I route these to your memory files?"

### Step 7: Route to Memory

After confirmation, update the relevant files:

| Signal Type           | Destination                                                                                |
| --------------------- | ------------------------------------------------------------------------------------------ |
| Decisions             | Append to `sidekick/memory/decisions.md`                                                   |
| Action items (user)   | Append to `sidekick/TASKS.md`                                                              |
| Action items (others) | Append to `sidekick/TASKS.md` with owner noted, for follow-up tracking                     |
| Blockers              | Append to `sidekick/TASKS.md` as blocked items with blocker details                        |
| Dates/Deadlines       | Update relevant entries in `sidekick/TASKS.md` or `sidekick/context/current-priorities.md` |
| New people            | Append to `sidekick/context/team-directory.md` (MEDIUM confidence)                         |
| New terms             | Append to `sidekick/memory/glossary.md`                                                    |
| Competitive mentions  | Update/create file in `sidekick/memory/competitors/`                                       |
| Strategy shifts       | Flag for priority review, update `sidekick/context/current-priorities.md` if confirmed     |
| Assumption updates    | Update relevant entry in `sidekick/memory/decisions.md` assumptions register               |

## After This Skill

Suggest based on what was mined:

| If you found...            | Suggest...                                                                              |
| -------------------------- | --------------------------------------------------------------------------------------- |
| Decisions routed to memory | "Want to review the full decision log?" → Read `skills/decision-log/SKILL.md`           |
| Strategy shifts detected   | "This might affect your priorities." → Read `skills/context-refresh/SKILL.md`           |
| Competitive signals        | "Want me to update competitor profiles?" → Update `sidekick/memory/competitors/`        |
| Multiple action items      | "Here's your updated task list." → Show `sidekick/TASKS.md`                             |
| It's Friday                | "Want me to include this in your weekly update?" → Read `skills/weekly-update/SKILL.md` |

## Rules

- Never fabricate quotes. If you can't find the exact wording, paraphrase and mark as `[paraphrased]`
- When uncertain about a classification, mark it and let the user decide
- Match output style to `sidekick/context/communication-style.md` (if it exists) - no banned words, correct formatting
- If the transcript is incomplete or low quality, say so rather than guessing
- Cross-reference new decisions against existing ones in `sidekick/memory/decisions.md` and flag contradictions
