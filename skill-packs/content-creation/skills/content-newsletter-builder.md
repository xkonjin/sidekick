---
name: newsletter-builder
description: "Build newsletter editions from recent activity, content, and updates. Trigger when the user says 'newsletter', 'weekly edition', 'email newsletter', or 'subscriber update'. Produces full draft for review - never sends."
---

# Newsletter Builder

Assembles newsletter editions from what's actually happened - not generic filler. Structures content for scannability, writes in your voice.

## Process

### Step 1: Identify the Newsletter

Ask if not already clear:

- Who is the audience? (external subscribers, internal team, stakeholders)
- What cadence? (weekly, biweekly, monthly)
- Is there a theme or anchor topic for this edition?

### Step 2: Gather Content

Pull from available sources:

- Recent blog posts or published content
- `sidekick/context/current-priorities.md` - Product updates, campaigns, milestones
- Meeting notes or decisions relevant to the audience
- Any external news or industry developments the user has flagged

List what's available. If sources are thin, say so and ask the user to supply key updates.

### Step 3: Structure the Edition

```
Subject line options: [3 options - direct, curiosity, and value-led]

Header/Hero: [main story or anchor topic]

Section 1: [title] - [2-3 sentences + link if applicable]
Section 2: [title] - [2-3 sentences + link if applicable]
Section 3: [title] - [2-3 sentences + link if applicable]

CTA: [single clear action]

Footer: [standard sign-off]
```

Keep sections curated - 3-5 items max. Comprehensive newsletters don't get read.

### Step 4: Write the Draft

Apply communication-style.md. Match formality to the audience type. External subscribers get a different register than internal team updates.

### Step 5: Save Output

Save to `sidekick/outputs/newsletter-[DATE].md`.

## After This Skill

- **repurpose-content** - Pull strong sections into standalone social posts
- **blog-post-drafter** - Expand a newsletter section into a full post

## Rules

- Subject lines are the most important part. Always offer 3 options.
- Keep sections scannable - short paragraphs, no walls of text.
- Never send. The user reviews, edits, and sends via their email platform.
- If communication-style.md doesn't exist, ask for the newsletter's tone before drafting.
