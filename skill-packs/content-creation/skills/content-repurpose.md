---
name: repurpose-content
description: "Transform existing content into new formats for different platforms. Trigger when the user says 'repurpose', 'turn this into', 'adapt for', 'convert to', or 'make a thread from'. Each format gets genuine transformation, not copy-paste truncation."
---

# Repurpose Content

Transforms content into new formats while preserving the core message and the user's voice. Restructures for platform conventions - not just shorter versions of the original.

## Process

### Step 1: Get the Source Content

Accept any of:

- A URL to an existing post or article
- A pasted block of text
- A file path to an existing output (e.g., `sidekick/outputs/blog-*.md`)

Read the full source before proceeding.

### Step 2: Identify the Target Format

Ask if not specified:

- What format? (LinkedIn post, X thread, newsletter section, slide deck outline, email, short-form summary)
- Any specific angle to emphasize? (If the source is long, there may be multiple valid excerpts)

### Step 3: Load Context

Read before writing:

- `sidekick/context/communication-style.md` - Voice must match the user's style in the new format

### Step 4: Transform for the Target Format

Apply format-specific conventions:

- **LinkedIn post** - Extract the strongest insight, lead with it, 150-300 words, first-person, no link in first comment unless user requests
- **X thread** - Number each tweet (1/n), hook in tweet 1, each tweet standalone-readable, end with a summary or CTA
- **Newsletter section** - 2-4 sentences + link, framed for the newsletter's audience context
- **Slide deck outline** - One idea per slide, title + 3 bullets max, logical flow
- **Email** - Subject line + adapted body with appropriate greeting/close
- **Short-form summary** - 3-5 bullet points capturing the key ideas

### Step 5: Review and Save

Present adapted version and ask for feedback. Save to `sidekick/outputs/repurposed-[format]-[DATE].md`.

## After This Skill

- **social-media-calendar** - Schedule the repurposed content across platforms

## Rules

- Repurposing is not truncating. Each format has different expectations - restructure accordingly.
- Blog to LinkedIn needs a fresh hook, not the first paragraph copy-pasted.
- Match the voice from communication-style.md. The format changes, the voice doesn't.
- Never post or send. The user reviews and publishes themselves.
