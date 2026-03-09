---
name: context-refresh
description: "The adaptation engine. Scans recent activity across connected tools, compares against stored memory, and proposes updates. Activates on: 'refresh context', 'what changed', 'update my memory', 'sync my sidekick', 'is my context up to date', 'things have changed recently'. Also triggers PROACTIVELY when it's been 2+ weeks since the last refresh, suggesting: 'It's been a couple weeks. Want me to scan for changes?'"
---

# Context Refresh

The adaptation engine. Compares reality (recent activity) against memory (stored files) and proposes updates.

## Why This Exists

Memory drifts from reality. People change roles, priorities shift, projects end, new terms appear. Without periodic refresh, Sidekick's context becomes stale and it starts making wrong assumptions.

## Process

### Step 1: Scan Recent Activity

Using connected tools, scan the past 7 days (or since last refresh):

**Messaging (Slack/Teams):**

- Channels the user is active in
- Look for: org announcements, role changes, new projects, strategy shifts, new terminology

**Calendar:**

- New recurring meetings (suggest adding to context)
- Cancelled recurring meetings (suggest removing)
- Meetings with unfamiliar attendees (suggest adding to team directory)

**Meeting Notes:**

- Recent transcripts for decisions and shifts not yet captured

### Step 2: Compare Against Memory

Read all memory files and compare:

| File                                     | What to Check                                                                                                    |
| ---------------------------------------- | ---------------------------------------------------------------------------------------------------------------- |
| `sidekick/context/current-priorities.md` | Are stated priorities still what the user is actually working on? Any new priorities emerging from activity?     |
| `sidekick/context/team-directory.md`     | New people appearing in meetings/Slack? Anyone who's gone quiet (might have left)? Role changes?                 |
| `sidekick/memory/glossary.md`            | New terms appearing in conversations?                                                                            |
| `sidekick/memory/decisions.md`           | Decisions with review dates that have passed? Assumptions that might need revalidation?                          |
| `sidekick/memory/confidence-flags.md`    | Any LOW confidence items that now have more evidence? Any HIGH confidence items contradicted by recent activity? |
| `sidekick/memory/projects/*.md`          | Project status changes? New projects? Completed/cancelled projects?                                              |
| CLAUDE.md                                | Anything in the main file that contradicts recent activity?                                                      |

### Step 3: Generate Diff Report

Present findings as a proposed update:

```markdown
# Context Refresh - [Date]

## Proposed Changes

### Priorities

- [ ] [Priority X] appears stale. No activity in 2 weeks. Confirm or replace?
- [ ] New activity around [topic] suggests emerging priority. Add?

### People

- [ ] [Name] appeared in 3 meetings this week. Not in team directory. Add?
- [ ] [Name] hasn't appeared anywhere in 4 weeks. Still active?
- [ ] [Name]'s role may have changed based on [evidence]. Update?

### Glossary

- [ ] New term "[term]" used in [meeting/channel]. Add definition?

### Decisions

- [ ] Decision D-XXX has a review date of [past date]. Time to review.
- [ ] Assumption A-XXX may be invalidated by [evidence].

### Confidence Updates

- [ ] [Topic] was LOW confidence. Now have [evidence] to upgrade to MEDIUM.
- [ ] [Topic] was HIGH confidence but contradicted by [recent activity]. Downgrade?

### Projects

- [ ] [Project] appears to be completed/stalled. Update status?
- [ ] New project [name] emerging from recent meetings. Track?

## No Change Needed

[List files that look current and accurate]
```

### Step 4: User Approval

**Every change requires explicit user approval.** Present the diff, let the user check/uncheck items, then apply only what's approved.

For each approved change:

1. Update the relevant file
2. If confidence was changed, log it in confidence-flags.md
3. If a decision was reviewed, update its review date

### Step 5: Log the Refresh

If `sidekick/outputs/context-refresh-log.md` doesn't exist, create it with a `# Context Refresh Log` heading.

Append to `sidekick/outputs/context-refresh-log.md`:

```
## [Date]
- Files checked: [list]
- Changes proposed: [count]
- Changes approved: [count]
- Changes rejected: [count]
- Next refresh recommended: [date, typically 7 days from now]
```

## After This Skill

| If...                            | Suggest...                                                                                                      |
| -------------------------------- | --------------------------------------------------------------------------------------------------------------- |
| Priorities changed significantly | "Want me to draft an updated weekly update?" → Read `skills/weekly-update/SKILL.md`                             |
| New people discovered            | Silently update team directory, no chaining needed                                                              |
| Stale decisions found            | "Some decisions need review." → Read `skills/decision-log/SKILL.md` (skip if already chained from decision-log) |
| Major context shift              | "A lot has changed. Want me to re-analyze your communication style?" → Re-run comm analysis                     |

## Rules

- Never auto-apply changes. Every update must be user-approved.
- When uncertain about something, mark it with a question rather than a statement
- If no tools are connected, this skill can still work by asking the user what's changed
- Respect the confidence framework. Don't upgrade to HIGH without strong evidence.
- Keep the diff report scannable. Group by category, use checkboxes.
- If nothing has changed, say so. "Everything looks current" is a valid output.
