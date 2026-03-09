---
name: postmortem
description: "Write a blameless postmortem. Trigger when the user says 'postmortem', 'incident report', 'root cause analysis', 'write up what happened', or 'incident review'."
---

# Postmortem

Blameless incident analysis: what happened, why it happened, and what changes prevent recurrence. Focus on systems and processes, not individuals.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/communication-style.md` - Match writing style
- `sidekick/context/team-directory.md` - Correct names and roles for participants

### Step 2: Gather Information

Ask for everything not already provided:

- When did the incident start and end?
- What was the user-visible impact? (Error rates, downtime, degraded performance)
- How was it detected? (Alert, user report, internal discovery)
- What was the timeline of key events during the incident?
- What was the root cause?
- What contributing factors made it worse or harder to catch?
- Who was involved in the response?
- What action items came out of the review?

### Step 3: Write the Postmortem

```markdown
# Postmortem: [Short incident title]

**Date:** [Incident date]
**Duration:** [Start time] to [End time] ([total duration])
**Severity:** [P0/P1/P2 or equivalent]
**Status:** [Draft / In Review / Closed]
**Author(s):** [Names]

## Summary

[2-3 sentences. What happened, what broke, and how it was resolved. Written for someone
who knows the system but wasn't in the incident.]

## Impact

- **Users affected:** [Number or percentage]
- **Services affected:** [List]
- **Error rate / downtime:** [Metrics]
- **Revenue or SLA impact:** [If applicable]

## Timeline

| Time (UTC) | Event                      |
| ---------- | -------------------------- |
| HH:MM      | [What happened]            |
| HH:MM      | [Alert fired / team paged] |
| HH:MM      | [Diagnosis step]           |
| HH:MM      | [Mitigation applied]       |
| HH:MM      | [Incident resolved]        |

## Root Cause

[One specific, technical explanation. Not "human error." What system condition, missing
guard, or incorrect assumption allowed this failure?]

## Contributing Factors

- [Factor 1: what made this easier to trigger or harder to catch]
- [Factor 2]
- [Factor 3]

## What Went Well

- [Response or detection that worked]
- [Tool or process that helped]

## What Went Poorly

- [Gap in detection, response, or communication]

## Action Items

| Item                          | Owner  | Due    | Priority       |
| ----------------------------- | ------ | ------ | -------------- |
| [Specific fix or improvement] | [Name] | [Date] | [High/Med/Low] |

## Lessons Learned

[2-4 sentences. What systemic insight does this incident reveal about the system, the
team's processes, or the monitoring setup?]
```

### Step 4: Review and Save

- Present draft to user
- Ask: "Anything inaccurate in the timeline or root cause?"
- Save to `sidekick/outputs/postmortem-[DATE]-[slug].md`

## Rules

- Blameless means systems and processes fail, not people. Rewrite any finger-pointing language.
- Root cause must be specific. "Human error" is not a root cause.
- Action items must have owners and due dates — a list without owners is a wishlist
- Do not minimize impact. Accurate severity builds trust.
- If information is missing, say so explicitly rather than inferring
