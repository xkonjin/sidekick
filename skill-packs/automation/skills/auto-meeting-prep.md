---
name: meeting-prep
description: "Prepare for an upcoming meeting with attendee context, agenda items, talking points, and open questions. Trigger when the user says 'prep for meeting', 'meeting with [person]', or 'meeting prep'."
---

# Meeting Prep

Gets you ready for a meeting using real context: who's in the room, what's been discussed before, what you need from them, and what you should not forget to raise.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/team-directory.md` - Context on attendees
- `sidekick/context/current-priorities.md` - What's active and relevant
- `sidekick/context/working-preferences.md` - How you like prep formatted (if it exists)
- `sidekick/context/communication-style.md` - Tone to use in the meeting

### Step 2: Identify the Meeting

If not specified, ask:

- Who is this meeting with?
- What is the meeting about?
- How long is it?
- Is there an agenda already, or are you setting it?

If calendar tools are connected, pull the event and read the description and attendee list directly.

### Step 3: Gather Pre-Meeting Intelligence

**Attendees:** For each person in team-directory.md, pull relevant context: role, relationship, recent interactions, anything they're blocked on or waiting for.

**Recent History:** Check available sources (meeting notes, Slack, Granola) for the last conversation with these attendees. What was decided? What was promised?

**Open Items:** Check `sidekick/TASKS.md` for any items that involve these people or this topic.

### Step 4: Build the Brief

```markdown
# Meeting Prep: [Meeting Title]

[Date] | [Duration] | [Attendees]

## Context

[1-2 sentences: why this meeting exists and what's at stake]

## Agenda

1. [Item] - [time allocation]
2. [Item] - [time allocation]

## Your Talking Points

- [Point tied to a priority or open item]
- [Point tied to a priority or open item]

## Open Questions to Raise

- [Question you need answered]
- [Question you need answered]

## Watch For

- [Anything sensitive, a known tension, or a topic that may come up unexpectedly]

## After the Meeting

- [What you'll need to do or follow up on]
```

## Rules

- If an attendee isn't in team-directory.md, note that and ask the user for context on them
- Don't fabricate history. If no prior meeting notes exist, say so.
- Flag if the meeting conflicts with something in current-priorities.md (e.g., you're attending a meeting that pulls you away from a stated top priority)
