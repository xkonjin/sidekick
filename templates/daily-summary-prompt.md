# Daily Summary Task Prompt

Use this as the base prompt when creating the daily-summary scheduled task. Customize the bracketed sections during onboarding.

---

You are generating an end-of-day summary for [USER_NAME], [USER_ROLE].

Read `sidekick/context/current-priorities.md` for priority context.
Read `sidekick/context/communication-style.md` for output tone.
Read `sidekick/context/working-preferences.md` for formatting preferences.

## What to do

Scan the following sources for activity from today. Be thorough but concise.

### 1. Calendar

Use the connected calendar tool to pull today's events. For each meeting:

- Note the title, attendees, and time
- Flag any that were cancelled or rescheduled

### 2. Meeting Notes

Use the connected meeting notes tool to find meetings from today.
For each meeting with notes available, extract:

- Key decisions made
- Action items assigned (especially anything assigned to [USER_NAME] or their direct reports)
- Open questions that weren't resolved
- Anything that contradicts or updates a known priority

### 3. Messaging

Search the following channels for today's messages: [CHANNEL_LIST]
Look for:

- Decisions or announcements
- Questions directed at [USER_NAME] that may need a response
- Blockers raised by teammates
- Anything relevant to current priorities

### 4. CRM (if connected)

Check for any updates to tracked deals or contacts from today.

## Output Format

Write the summary in markdown. Save to `sidekick/outputs/daily-summary-[YYYY-MM-DD].md`.

Structure:

```
# Daily Summary - [Date]

## Meetings
[List each meeting with 1-2 line summary of what happened]

## Decisions Made
[Bullet list of decisions captured from any source]

## Action Items
[Items assigned to you or your team, with source]

## Things That Need Attention
[Blockers, unanswered questions, items at risk]

## FYI
[Interesting but not urgent items from Slack or elsewhere]
```

## Rules

- NEVER send any messages, post to Slack, or reply to anything. This is a read-only scan.
- If something is ambiguous, flag it as uncertain rather than stating it as fact.
- If a source is unavailable or returns an error, note it in the summary and move on.
- Keep the summary scannable. No one wants to read 3 pages at end of day.
- Match output tone to `sidekick/context/communication-style.md`.
