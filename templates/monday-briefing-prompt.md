# Monday Briefing Task Prompt

Use this as the base prompt when creating the monday-briefing scheduled task. Customize the bracketed sections during onboarding.

---

You are generating a Monday morning briefing for [USER_NAME], [USER_ROLE]. This should help them walk into the week prepared and focused.

Read `sidekick/context/current-priorities.md` for priority context.
Read `sidekick/context/communication-style.md` for output tone.
Read `sidekick/context/working-preferences.md` for formatting preferences.

## What to do

Scan connected sources to build a picture of what the week ahead looks like and what carried over from last week.

### 1. This Week's Calendar

Use the connected calendar tool to pull all events from today (Monday) through Friday.

- List each meeting with time, attendees, and purpose (if discernible from the title or description)
- Flag any new meetings that weren't on last week's calendar
- Note any large blocks of free time (potential deep work windows)
- Highlight external meetings or meetings with leadership

### 2. Unfinished Business from Last Week

Use the connected meeting notes tool to check last week's meetings for unresolved items.
Look for:

- Action items assigned to [USER_NAME] that may still be open
- Decisions that were deferred to "next week"
- Follow-ups that were promised but may not have happened

### 3. Messaging Catch-Up

Read the following channels for messages from Friday afternoon through now: [CHANNEL_LIST]
Look for:

- Anything posted over the weekend or early Monday
- Decisions made without [USER_NAME] present
- Questions directed at [USER_NAME] that need a response
- Announcements that affect this week's plans

### 4. Priority Check

Reference `sidekick/context/current-priorities.md`.

- Are the stated priorities still accurate based on what you've seen?
- Flag if any priority seems stale or overtaken by events

### 5. CRM (if connected)

Check for any deal updates, upcoming renewals, or contacts that need attention this week.

## Output Format

Write the briefing in markdown. Save to `sidekick/outputs/monday-briefing-[YYYY-MM-DD].md`.

Structure:

```
# Monday Briefing - [Date]

## Week at a Glance
[Quick calendar summary: X meetings, Y hours of meetings, Z hours of open time. Any notable external meetings.]

## Carry-Over Items
[Action items and follow-ups from last week that appear to still be open]

## What You Missed
[Anything significant from messaging or other sources since you last checked (Friday evening onward)]

## Today's Prep
[Specific prep needed for today's meetings. Who's attending, what's the context, anything to review beforehand.]

## This Week's Focus
[Based on priorities and calendar, a suggested focus for the week. Flag any conflicts between priorities and calendar load.]

## Heads Up
[Upcoming deadlines, scheduled decisions, or events later this week that need advance prep]
```

## Rules

- NEVER send any messages, post to Slack, or reply to anything. This is a read-only scan.
- If something is ambiguous, flag it as uncertain rather than stating it as fact.
- If a source is unavailable or returns an error, note it in the summary and move on.
- Keep the tone forward-looking and actionable. This is about starting the week strong, not rehashing the past.
- The briefing should take 2-3 minutes to read. Shorter is better on Monday mornings.
- Match output tone to `sidekick/context/communication-style.md`.
