---
name: research-knowledge-base
description: "Save a piece of research, insight, or reference material to a persistent, indexed knowledge entry. Trigger when the user says 'save this for later', 'remember this research', 'file this', or 'add this to the knowledge base'."
---

# Knowledge Base

Turns one-off research into retrievable knowledge. De-duplicates before filing. Tags for future retrieval.

## Process

### Step 1: Load Context

Read these files before starting:

- `sidekick/memory/knowledge/` (if any exist) - check for similar existing entries before creating a new one
- `sidekick/memory/projects/` (if any exist) - identify which project(s) this knowledge is relevant to

### Step 2: Receive Content

If content is provided in the message, proceed. If not, ask:

- What should I save to the knowledge base?

Skip this question if the content is already in the user's message.

### Step 3: Check for Duplicates

Search `sidekick/memory/knowledge/` for entries on the same topic. If a similar entry exists:

- Offer to update the existing entry rather than create a new one
- Append new information to the existing file under a `## Updates` section

### Step 4: Draft the Knowledge Entry

```markdown
# [Topic Title]

**Saved:** [DATE] | **Source:** [URL, author, or "User-provided"] | **Source date:** [Date of original content]
**Tags:** [tag1, tag2, tag3]

## Key Insight

[One sentence: the most important thing to know from this source]

## Detail

[2-4 sentences or bullet points with the core content worth preserving]

## Relevant To

| Project / Priority              | Why it's relevant     |
| ------------------------------- | --------------------- |
| [Project from projects/ folder] | [Specific connection] |
| [Priority from priorities file] | [How this informs it] |

## Review Date

[Date when this fact may become stale — or "Evergreen" if it won't]

## Source

[Full citation: author, title, publication, URL, date]
```

### Step 5: Save

Save to `sidekick/memory/knowledge/[topic-slug].md`. Confirm the filename with the user before saving.

## After This Skill

| Condition                                  | Suggestion                                                                                   |
| ------------------------------------------ | -------------------------------------------------------------------------------------------- |
| Multiple saved entries might connect       | **insight-connector** → `skill-packs/research-learning/skills/research-insight-connector.md` |
| Entry feeds a structured research question | **research-brief** → `skill-packs/research-learning/skills/research-brief.md`                |

## Rules

- De-duplicate before creating a new entry — check knowledge/ first
- Include source URL and date; knowledge without provenance becomes unreliable over time
- Flag perishable facts with a review date; market data, competitor info, and pricing go stale quickly
- Never fabricate source details; if the URL is unavailable, note "URL unavailable — user-provided"
- Tags must be meaningful; avoid generic tags like "interesting" or "research"
