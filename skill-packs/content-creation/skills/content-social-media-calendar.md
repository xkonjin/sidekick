---
name: social-media-calendar
description: "Plan social media content across platforms with post copy drafted in the user's voice. Trigger when the user says 'social calendar', 'social media plan', 'content schedule', or 'what should I post'. Never posts. Always shows for approval."
---

# Social Media Calendar

Plans social content across platforms and drafts actual post copy - not just topic ideas.

## Process

### Step 1: Scope the Calendar

Ask if not already specified:

- Which platforms? (LinkedIn, X, Instagram, Threads, Bluesky)
- Time horizon? (1 week, 2 weeks, 1 month)
- Posting frequency per platform?
- Any campaigns, launches, or events to anchor content around?

### Step 2: Load Context

Read before planning:

- `sidekick/context/current-priorities.md` - Live priorities to generate relevant content ideas
- `sidekick/context/communication-style.md` - Voice and tone per platform

### Step 3: Generate the Calendar

Build a table with columns: Date | Platform | Topic | Type | Draft Copy | Status

Fill every row with actual draft copy, not placeholders. Status starts as "Draft" for all.

### Step 4: Platform Adaptation

Apply platform-specific conventions to each draft:

- LinkedIn: professional, slightly longer, first-person insight, no hashtag spam
- X: punchy, under 280 characters for standalone tweets, or structure as thread
- Instagram: visual-first framing, storytelling hooks, 3-5 relevant hashtags
- Threads: conversational, shorter than LinkedIn, lower formality

### Step 5: Save Output

Save to `sidekick/outputs/social-calendar-[DATE].md`.

## After This Skill

- **blog-post-drafter** - Expand any calendar topic into a full post
- **content-brief** - If delegating any post creation to a writer or agency

## Rules

- Different platforms need different tones. LinkedIn != X. Never use the same copy across both without adapting.
- Respect character limits. X posts that exceed 280 characters get cut off - flag these.
- Never post anything. The user reviews and schedules themselves.
- If current-priorities.md doesn't exist, ask the user what's coming up that content should support.
