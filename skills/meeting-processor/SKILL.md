---
name: meeting-processor
description: "Quick meeting follow-up with summary, decisions, and action items. Activates when the user wants a fast meeting recap. Detects: 'meeting follow-up', 'summarize [meeting]', 'quick recap of [meeting]', 'what were the action items from [meeting]', 'give me the highlights from [meeting]', 'what did I miss in [meeting]'. Automatically chosen over transcript-miner when the user wants speed over depth."
---

# Meeting Processor

Lighter and faster than transcript-miner. Produces a quick follow-up doc from a meeting.

## Process

### Step 1: Find the Meeting

Use available meeting note tools to find the meeting:

- If the user specifies a meeting name, search for it
- If no name given, list recent meetings and ask which one

### Step 2: Load Context

Read these files for context:

- CLAUDE.md - Decode shorthand, understand who people are
- `sidekick/context/current-priorities.md` - Assess impact
- `sidekick/context/communication-style.md` - Match output style (if it exists; otherwise match conversational tone)

### Step 3: Generate Follow-Up

Create the follow-up document:

```markdown
# Meeting Follow-Up: [Meeting Name] - [Date]

## Summary

[5 bullet points max. What was this meeting about? What's the one-line takeaway?]

## Decisions

| #   | Decision           | Owner         |
| --- | ------------------ | ------------- |
| 1   | [What was decided] | [Who owns it] |

## Action Items

| #   | Action | Owner    | Due    | Status |
| --- | ------ | -------- | ------ | ------ |
| 1   | [Task] | [Person] | [Date] | Open   |

## Open Questions

- [Questions raised but not resolved]

## Priority Impact

[One line: does this meeting change anything about current priorities? If not, say "No priority impact."]

## Draft Follow-Up Message

[Optional: a short message the user could send to attendees summarizing outcomes. Match their communication style. Mark as DRAFT.]
```

### Step 4: Save and Route

- Save to `sidekick/outputs/meeting-[meeting-name]-[DATE].md`
- Ask if the user wants action items added to `sidekick/TASKS.md`
- If new people or terms were mentioned, ask if they should be added to team directory / glossary

## After This Skill

Suggest the next relevant skill based on what was found:

| If you found...             | Suggest...                                                                                      |
| --------------------------- | ----------------------------------------------------------------------------------------------- |
| Decisions were made         | "Want me to log these decisions?" → Read `skills/decision-log/SKILL.md`                         |
| Action items for the user   | "Want me to add these to your task list?" → Add to `sidekick/TASKS.md`                          |
| Priority-affecting outcomes | "This might change your priorities. Want me to check?" → Read `skills/context-refresh/SKILL.md` |
| Need deeper analysis        | "Want me to do a deeper dive on this meeting?" → Read `skills/transcript-miner/SKILL.md`        |

Don't force chaining. Only suggest if the meeting output genuinely warrants it.

## Rules

- Keep it short. This is a quick follow-up, not a deep analysis.
- Match output style to `sidekick/context/communication-style.md` (if it exists)
- The draft follow-up message is always a DRAFT. Never send without explicit approval.
- If the meeting notes are thin, say so. Don't pad with speculation.
