---
name: relationship-map
description: "Build a visual relationship map of allies, sponsors, dependencies, and tensions in a professional network or org. Trigger when the user says 'relationship map', 'who do I know', 'network map', 'political landscape', or 'org dynamics'."
---

# Relationship Map

Makes the informal org chart visible. Surfaces who you rely on, who relies on you, where there's political tension, and who has influence you're not yet using.

## Process

### Step 1: Load Context

Read these files:

- `sidekick/context/team-directory.md` - Primary source: every person with their role and relationship context
- `sidekick/context/about-me.md` - Your role and org position (the center of the map)
- `sidekick/context/current-priorities.md` - Which relationships are most critical to active work
- `sidekick/context/working-preferences.md` - Any noted preferences for how to engage different people (if it exists)

### Step 2: Clarify Scope

If not specified, ask:

- Is this the full professional network or a specific context (e.g., a project, a team, an org)?
- Should it include external stakeholders (partners, vendors, clients)?
- Is there a specific purpose - e.g., identifying who to influence, who to develop, where tension exists?

Skip questions if the user's message already answers them.

### Step 3: Build the Map

**Categorize each person:**

- **Allies:** People who actively support your work. Reliably responsive, aligned on priorities.
- **Sponsors:** People with more organizational power who advocate for you or open doors.
- **Dependencies:** People whose output or decisions you need to move forward.
- **Influencers:** People who shape others' views but may not be in your direct network.
- **Tensions:** Relationships with friction - misalignment, conflict, or past breakdowns.
- **Untapped:** People you should know better given current priorities but don't yet.

**Assess relationship health** for critical relationships: strong, developing, at risk, or dormant.

### Step 4: Generate Output

Save to `sidekick/memory/relationship-map.md`.

```markdown
# Relationship Map

**Updated:** [date] | **Context:** [full network / project / team]

## Map

| Person | Role   | Category                                                        | Relationship Health                       | Notes         |
| ------ | ------ | --------------------------------------------------------------- | ----------------------------------------- | ------------- |
| [name] | [role] | [Ally / Sponsor / Dependency / Influencer / Tension / Untapped] | [Strong / Developing / At risk / Dormant] | [key context] |

---

## Critical Relationships (active priorities)

For each relationship critical to a current priority:

**[Name]** - [role]

- Why they matter now: [tied to which priority]
- Current state: [what's working, what's not]
- Next action: [specific step to strengthen or repair]

---

## Tensions

| Relationship | Source of tension   | Impact on work               | Resolution path                        |
| ------------ | ------------------- | ---------------------------- | -------------------------------------- |
| [name]       | [what's causing it] | [how it affects active work] | [path forward or "needs conversation"] |

---

## Untapped Connections

- [Name]: [why they'd be valuable to know better, and what's the entry point]
```

## After This Skill

| If...                                                    | Suggest...                                                          |
| -------------------------------------------------------- | ------------------------------------------------------------------- |
| A specific upcoming meeting with a key person needs prep | Read `skill-packs/automation/skills/auto-meeting-prep.md`           |
| People management context is needed for a direct report  | Read `skill-packs/people-management/skills/mgmt-one-on-one-prep.md` |

## Rules

- Only map people who appear in team-directory.md or who the user has explicitly mentioned. Don't invent people.
- "Tensions" must be flagged honestly. Omitting known friction from the map makes it useless.
- Relationship health is current state, not aspiration. If it's at risk, say so.
- Never fabricate. If you can't find it, say so.
