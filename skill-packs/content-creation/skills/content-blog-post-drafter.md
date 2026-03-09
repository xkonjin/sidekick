---
name: blog-post-drafter
description: "Draft blog posts matched to the user's actual voice and audience. Trigger when the user says 'blog post', 'draft a post', 'write about', 'article about', or 'blog draft'. Produces structured draft for review - never publishes."
---

# Blog Post Drafter

Writes blog posts in your voice, not a generic template. Structures before drafting, checks supporting data, then writes.

## Process

### Step 1: Clarify Intent

If the user hasn't specified, ask:

- What is the topic?
- Who is the audience? (industry experts, general readers, internal team)
- What is the goal? (inform, persuade, educate, entertain)
- Approximate length? (short 400-600w, standard 800-1200w, long-form 2000+)

Skip questions already answered in the user's message.

### Step 2: Load Context

Read these files before drafting:

- `sidekick/context/communication-style.md` - Voice, vocabulary, banned words (REQUIRED)
- `sidekick/context/current-priorities.md` - What's live now (informs angle and relevance)

### Step 3: Gather Supporting Material

Check available sources for data, examples, or quotes that strengthen the post:

- Recent meeting notes or decisions relevant to the topic
- Any existing content (prior posts, briefs, docs) on this subject
- If nothing exists, flag gaps and ask the user to supply key data points

### Step 4: Generate Structure

Present the structure before writing the full draft:

```
Hook/Opening: [angle + why the reader should care]
Key Points:
  1. [Point] - [supporting evidence]
  2. [Point] - [supporting evidence]
  3. [Point] - [supporting evidence]
CTA/Closing: [what you want the reader to do or think]
```

Confirm the structure before proceeding.

### Step 5: Write the Draft

Apply communication-style.md strictly. Match vocabulary patterns, sentence rhythm, and formality level. No AI slop - no "in today's fast-paced world", no generic openers.

### Step 6: Review and Iterate

Present draft and ask: "Does this sound like you? Anything to adjust?"

Iterate on feedback before saving.

### Step 7: Save Output

Save to `sidekick/outputs/blog-[slug]-[DATE].md`.

## After This Skill

- **repurpose-content** - Turn the post into LinkedIn content, an X thread, or a newsletter section
- **social-media-calendar** - Schedule promotion across platforms

## Rules

- If communication-style.md doesn't exist, ask for a sample of the user's writing before drafting
- One draft per request. Don't offer multiple versions unless asked.
- Never publish. The user copies and posts themselves.
- If no supporting data exists, say so - don't invent statistics
