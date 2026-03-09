---
name: vendor-tracker
description: "Generate a multi-vendor status table with project, last contact, next milestone, and blockers. Trigger when the user says 'vendor status', 'agency update', 'agency status', or 'vendor check'."
---

# Vendor Tracker

Produces a consolidated view of all active vendor and agency relationships: where each project stands, when you last talked, what's next, and what's blocking progress.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/current-priorities.md` - Which vendor projects tie to active priorities
- `sidekick/context/team-directory.md` - Vendor contacts, if listed
- `sidekick/context/working-preferences.md` - Preferred output format (if it exists)

### Step 2: Identify Active Vendors

If the user hasn't specified, ask: "Which vendors or agencies should I include?"

If memory files exist with vendor project details (e.g., `sidekick/memory/projects/`), read those first.

For each vendor, gather:

- Project name and current phase
- Last contact date and who it was with
- What was agreed at that contact
- Next deliverable or milestone and its due date
- Any known blockers or outstanding requests

Pull from available sources: calendar, Slack, meeting notes, email. If none are connected, ask the user to fill in the gaps.

### Step 3: Build the Table

```markdown
# Vendor Status - [Date]

| Vendor | Project   | Phase   | Last Contact | Next Milestone | Due    | Blockers            |
| ------ | --------- | ------- | ------------ | -------------- | ------ | ------------------- |
| [Name] | [Project] | [Phase] | [Date + who] | [Milestone]    | [Date] | [Blocker or "None"] |

## Items Needing Action

- [Vendor]: [Specific action required, by when]
- [Vendor]: [Specific action required, by when]
```

### Step 4: Flag Risks

Note any vendor where:

- Last contact was 7+ days ago with no update
- A milestone date has passed without confirmation of delivery
- A blocker has been open for 5+ days

## Rules

- If data isn't available for a field, mark it as "Unknown" rather than leaving it blank or guessing
- Tie vendor projects to priorities where possible. If a vendor is blocking a top priority, flag it prominently.
- Don't draft vendor communications without being asked. Offer to use email-drafter if follow-up is needed.
