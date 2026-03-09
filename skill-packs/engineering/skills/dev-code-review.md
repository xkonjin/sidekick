---
name: code-review
description: "Perform a structured code review. Trigger when the user says 'review this code', 'code review', 'review my PR', 'look at this diff', or pastes code and asks for feedback."
---

# Code Review

Structured review covering quality, security, performance, and readability. Produces line-level feedback, not general impressions.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/communication-style.md` - Match feedback tone to user's style
- `sidekick/context/working-preferences.md` - Directness and formatting preferences (if it exists)

### Step 2: Gather the Code

If the user hasn't already provided it, ask:

- What code or diff should be reviewed?
- What language/framework?
- What should the code do? (If not obvious from context)
- Any specific concerns to focus on?

### Step 3: Review in Four Passes

Run each pass independently. Do not blend them.

**Pass 1: Correctness & Logic**

- Does the code do what it claims to do?
- Are there off-by-one errors, null pointer risks, or missed edge cases?
- Are error conditions handled? What happens on failure?
- Any race conditions or state mutation bugs?

**Pass 2: Security**

- User input validated and sanitized before use?
- SQL injection, XSS, path traversal, or deserialization risks?
- Secrets, credentials, or tokens hardcoded or logged?
- Authentication/authorization enforced at the right layer?
- Overly permissive CORS, headers, or file permissions?

**Pass 3: Performance**

- N+1 queries or redundant database calls?
- Missing indexes for query patterns shown?
- Unbounded loops or recursion without exit conditions?
- Large objects held in memory longer than needed?
- Expensive operations inside hot paths?

**Pass 4: Readability & Maintainability**

- Variable and function names that communicate intent?
- Functions doing more than one thing?
- Dead code, unused imports, commented-out blocks?
- Inconsistencies with apparent project conventions?
- Missing or misleading comments on non-obvious logic?

### Step 4: Output

```markdown
## Code Review

**File / Scope:** [What was reviewed]
**Language:** [Language/framework]

### Critical (must fix before merge)

- [Line X] [Issue] — [Why it matters] [Suggested fix if applicable]

### Important (should fix)

- [Line X] [Issue] — [Why it matters]

### Minor (nice to have)

- [Line X] [Suggestion]

### Looks Good

- [What's done well — be specific, not generic]

**Summary:** [1-2 sentences on overall quality and readiness]
```

## Rules

- Reference specific lines or code snippets, not vague descriptions
- Separate what is broken from what is style preference
- If something is opinion-based, say so: "This is a preference, but..."
- Never review more than ~500 lines in a single pass without asking to focus
- Match tone to `sidekick/context/communication-style.md` — direct feedback, not harsh
