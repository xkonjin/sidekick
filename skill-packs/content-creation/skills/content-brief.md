---
name: content-brief
description: "Write content briefs for blog posts, social content, whitepapers, or case studies. Trigger when the user says 'content brief', 'brief for', 'writer brief', 'assign content', or 'content assignment'. Produces a standalone brief requiring no follow-up questions."
---

# Content Brief

Writes briefs that a writer can execute without needing 10 follow-up questions. Includes strategy, structure, voice guidelines, and success criteria.

## Process

### Step 1: Scope the Assignment

Ask if not already specified:

- Topic or working title?
- Target audience?
- Format? (blog post, social post, whitepaper, case study, landing page copy)
- Deadline?
- Who is writing it? (internal writer, freelancer, agency)

### Step 2: Load Context

Read before writing the brief:

- `sidekick/context/current-priorities.md` - Strategic alignment check
- `sidekick/context/communication-style.md` - Voice and tone guidelines to include in the brief

### Step 3: Generate the Brief

Structure:

```
## Content Brief: [Title]

**Objective:** What this piece needs to accomplish (inform, convert, educate, rank)
**Target audience:** Who is reading this and what they care about
**Key message:** The single most important thing the reader should take away
**Format:** Type, approximate word count, structure notes

**Tone and voice:** [Pull from communication-style.md or describe the required register]

**Outline:**
  1. [Section] - [what it covers and why]
  2. [Section] - [what it covers and why]
  3. [Section] - [what it covers and why]

**Required elements:** Specific data, quotes, CTAs, images, or disclaimers to include
**SEO keywords:** [If applicable - primary keyword, secondary keywords, search intent]
**Examples:** Links to pieces that nail the tone or structure you want
**Deadline:** [Date] | Review process: [Who approves and when]
```

### Step 4: Save Output

Save to `sidekick/outputs/brief-[topic]-[DATE].md`.

## After This Skill

- **blog-post-drafter** - If writing the piece yourself instead of assigning it
- **social-media-calendar** - Plan promotion once the piece is published

## Rules

- Briefs must be self-contained. The writer should not need to ask clarifying questions.
- Always include examples where possible - showing beats describing.
- If current-priorities.md doesn't exist, ask what strategic goal this content supports.
- Flag if the brief scope is too broad for the requested format (e.g., "five case studies in one blog post").
