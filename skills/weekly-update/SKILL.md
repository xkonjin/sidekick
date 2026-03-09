---
name: weekly-update
description: "Generate a weekly progress update referencing the user's priorities. Activates when the user wants a status report. Detects: 'weekly update', 'Friday update', 'write my update', 'status report', 'what did I accomplish this week', 'I need to send my update', 'help me write my recap', 'what did I get done'. Also triggers proactively if it's Friday afternoon and the user has a recurring update pattern."
---

# Weekly Update

Generates a structured weekly progress update that references the user's actual priorities and recent activity.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - What to report against
- `sidekick/context/communication-style.md` - Match the user's voice (if it exists; otherwise match conversational tone)
- `sidekick/context/working-preferences.md` - Output format preferences (if it exists)
- `sidekick/context/team-directory.md` - Who the update might go to

### Step 2: Gather Activity

Using connected tools, scan the past week (Monday through today):

**Calendar:** List meetings attended, note key ones.

**Meeting Notes:** For meetings with transcripts, pull decisions and action items (use transcript-miner logic but lighter).

**Messaging (Slack/Teams):** Scan relevant channels for:

- Things the user shipped or announced
- Blockers raised or resolved
- Decisions made async

**Tasks:** Read `sidekick/TASKS.md` for items completed or in progress.

If tools aren't connected, ask the user what they accomplished.

### Step 3: Generate Update

Format:

```markdown
# Weekly Update - [Date Range]

## Progress

[For each active priority from current-priorities.md:]

### [Priority Name]

- [What moved this week]
- [Key decisions or milestones]
- [Metrics if available]

## Completed

- [Bullet list of things finished this week]

## In Progress

- [Things actively being worked on, with expected completion]

## Blocked

- [Anything stalled, who/what is blocking it, how long it's been stuck]

## Next Week

- [What's planned for next week, key meetings or deadlines]

## Asks

- [Anything the user needs from others to make progress]
```

### Step 4: Review and Save

Present the draft to the user. Ask:

- "Does this accurately capture your week?"
- "Anything to add, remove, or reword?"
- "Who is this going to?" (affects tone and detail level)

After confirmation, save to `sidekick/outputs/weekly-update-[DATE].md`.

**Never send the update anywhere.** The user decides where it goes.

## Audience Awareness

Before generating, ask who this update is for (if not already known):

| Audience       | Tone                     | Detail Level | What to Emphasize                  |
| -------------- | ------------------------ | ------------ | ---------------------------------- |
| Manager/exec   | Concise, outcome-focused | High-level   | Impact, blockers, asks             |
| Team           | Collaborative, open      | Medium       | Progress, shared wins, help needed |
| Stakeholders   | Professional, polished   | Summary      | Results, timeline, decisions       |
| Self (journal) | Honest, reflective       | Full detail  | Everything, including doubts       |

Adjust the output format and tone based on the audience. If the user has a recurring update pattern, remember their audience from last time.

## After This Skill

| If...                            | Suggest...                                                                              |
| -------------------------------- | --------------------------------------------------------------------------------------- |
| Blockers mentioned               | "Want me to draft a message to unblock [item]?" → Use communication style               |
| Priority had zero progress       | "Priority [X] had no movement. Want to discuss why?" → Check if priority is still valid |
| It's been 2+ weeks since refresh | "Your context might be stale." → Read `skills/context-refresh/SKILL.md`                 |
| Decisions were made this week    | "Want me to log these decisions?" → Read `skills/decision-log/SKILL.md`                 |

## Rules

- Always structure around the user's stated priorities, not just a random list of activities
- Match tone and style to `sidekick/context/communication-style.md` (if it exists)
- If a priority had no progress this week, say so honestly. Don't pad.
- Keep it scannable. The recipient should get the picture in 2 minutes.
- Avoid banned words from working preferences
