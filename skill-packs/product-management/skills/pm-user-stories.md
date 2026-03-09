---
name: pm-user-stories
description: "Write user stories with acceptance criteria for a feature or epic."
---

Produces structured user stories in As a / I want / So that format, each with explicit acceptance criteria. Reads context before generating.

## Context Loading

1. Read `sidekick/context/current-priorities.md` - confirm which initiative these stories serve
2. Read `sidekick/context/communication-style.md` - match voice and detail level

If working from a PRD, ask for it or read from `sidekick/outputs/` if recently generated.

## Process

1. **Identify the epic** - what feature or initiative are these stories for?
2. **Identify user types** - who are the distinct actors? (reference team-directory for internal actors)
3. **Draft stories** - one per distinct user need, not per screen
4. **Write acceptance criteria** - testable conditions, not implementation details
5. **Flag edge cases** - any story that touches payments, auth, or data privacy needs extra AC rows

## Output Format

```markdown
## User Stories: [Epic / Feature Name]

---

### Story [N]: [Short title]

**As a** [specific user type],
**I want** [the action or capability],
**So that** [the outcome or value they get].

**Acceptance Criteria:**

- [ ] [Specific, testable condition]
- [ ] [Specific, testable condition]
- [ ] [Edge case or error state]

**Notes:** [Dependencies, open questions, or flagged risks]

---
```

Repeat for each story. Group by user type if there are multiple actors.

## Rules

- "User" is never specific enough. Name the segment.
- Acceptance criteria must be testable by QA without asking for clarification
- One story = one user need. Split if a story has "and" in the I want clause
- If more than 8 stories emerge, suggest splitting into sub-epics
- Never include implementation details in the story itself (those belong in AC or tech notes)
