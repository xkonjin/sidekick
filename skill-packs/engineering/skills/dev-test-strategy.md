---
name: test-strategy
description: "Define a test strategy for a feature, service, or codebase. Trigger when the user says 'test strategy', 'testing plan', 'what to test', 'how should we test this', or 'testing approach'."
---

# Test Strategy

Produces a prioritized testing plan using the test pyramid: focus effort where failures are most costly and least visible.

## Process

### Step 1: Load Context

Read:

- `sidekick/context/current-priorities.md` - Understand what this feature supports
- `sidekick/context/working-preferences.md` - Output preferences (if it exists)

### Step 2: Gather Information

Ask if not provided:

- What feature, service, or system needs a test strategy?
- What does it do? What are the critical paths?
- What already has test coverage?
- What's the tech stack? (Language, framework, test tooling)
- Any specific risk areas or edge cases the team is worried about?
- What level of coverage is realistic given team size and timeline?

### Step 3: Build the Strategy

#### Layer 1: Unit Tests (most, cheapest)

Identify the pure logic that should be unit tested:

- Business logic and calculation functions
- Data transformation and validation
- Edge cases and boundary conditions
- Error handling paths

Ask: what are the inputs and expected outputs for each key function?

#### Layer 2: Integration Tests (some, moderate cost)

Identify integration points that need verified:

- Database read/write operations
- External API calls (with mocked responses)
- Message queue produce/consume paths
- Authentication and authorization flows

#### Layer 3: End-to-End Tests (few, most expensive)

Identify the critical user paths that must work:

- The primary happy path the user cares about most
- The top 2-3 failure modes that would be catastrophic

Do not attempt full E2E coverage. Pick the paths where failure would be worst.

#### Edge Cases and Boundary Conditions

Surface these specifically:

- What happens with empty input, null values, or zero quantities?
- What breaks at scale? (Large payloads, high concurrency, long-running operations)
- Race conditions or ordering dependencies?
- Third-party failures or timeouts?

### Step 4: Output the Strategy

```markdown
## Test Strategy: [Feature or Service Name]

**Stack:** [Language / test framework]
**Coverage baseline:** [Current coverage % if known]
**Target coverage:** [Realistic target]

### Unit Tests

| Priority | What to test        | Input/output notes |
| -------- | ------------------- | ------------------ |
| High     | [Function or logic] | [Key cases]        |
| Medium   | [Function or logic] | [Key cases]        |

### Integration Tests

| What                | How             | Mocks needed   |
| ------------------- | --------------- | -------------- |
| [Integration point] | [Test approach] | [What to mock] |

### End-to-End Tests

| Critical path | Steps                  | Pass criteria        |
| ------------- | ---------------------- | -------------------- |
| [Happy path]  | [1. do X, 2. expect Y] | [Observable outcome] |

### Edge Cases to Cover

- [ ] [Edge case]: [Expected behavior]
- [ ] [Edge case]: [Expected behavior]

### What We're NOT Testing

- [Thing]: [Why it's excluded or tested elsewhere]

### Gaps and Risks

- [Known gap]: [Risk if untested, plan to address]
```

Save to `sidekick/outputs/test-strategy-[feature]-[DATE].md`.

## Rules

- Test pyramid is a ratio guide, not a rigid rule. Adjust based on what's risky.
- "We'll add tests later" rarely happens. Flag it as a gap with a risk level.
- Never recommend 100% unit test coverage as the goal — it optimizes for the wrong thing
- If the user has no existing tests, recommend a starting point, not the ideal end state
- Match tool recommendations to the existing stack — don't introduce new test frameworks without reason
