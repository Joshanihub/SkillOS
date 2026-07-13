# Assumption Documentation Template

When responding to ambiguous or incomplete requests (50-79% clarity), use this template to document assumptions before proceeding. This standardizes how SkillOS skills handle uncertainty across all tiers and domains.

---

## Template Structure

### 1. Request Context Block

```markdown
## Request Context

**What I understood from your request:**
[1-2 sentences summarizing the core intent]

**Clarity level:** 50-79% (ambiguous, multiple interpretations possible)

**What you explicitly told me:**
- [Item 1]
- [Item 2]
- [Item 3]

**What is missing or unclear:**
- [Gap 1]
- [Gap 2]
- [Gap 3]
```

### 2. Constraints Block

```markdown
## Operating Constraints

**Project constraints I'm applying:**
- [Constraint 1 with reason]
- [Constraint 2 with reason]

**Technical assumptions (based on your domain):**
- [Assumption 1]
- [Assumption 2]

**Timeline/scope assumptions:**
- [Assumption 1]
- [Assumption 2]
```

### 3. Explicit Assumptions List

Document 7-10 assumptions with reasoning. Format:

```markdown
## Explicit Assumptions (proceeding with these)

**1. [Assumption title]**
   - What I assume: [Clear statement]
   - Why: [1-2 sentence reasoning]
   - If wrong: [What changes in my output]
   - Override with: [How to correct this]

**2. [Assumption title]**
   - What I assume: [Clear statement]
   - Why: [1-2 sentence reasoning]
   - If wrong: [What changes in my output]
   - Override with: [How to correct this]

**3. [Assumption title]**
   - What I assume: [Clear statement]
   - Why: [1-2 sentence reasoning]
   - If wrong: [What changes in my output]
   - Override with: [How to correct this]

... (7-10 total)
```

### 4. Decision Triggers Block

```markdown
## Decision Triggers

**If you tell me...**
- "Actually, we're using X, not Y" → I will regenerate sections [list sections]
- "This is for Z domain, not what you assumed" → I will restart with [specific approach]
- "Our constraint is [different from assumed]" → I will adjust [specific aspect]
- "The timeline is actually [different]" → I will change scope to [what changes]

**Before I finalize output, tell me if any of these assumptions are wrong.**
```

### 5. Proceeding Statement

```markdown
## Proceeding With

Assuming the above, I will now:
1. [Action 1]
2. [Action 2]
3. [Action 3]

You can interrupt anytime with "Actually, assume..." and I'll adjust.
```

---

## When to Use This Template

Use this template when:

✅ **Definitely use:**
- Request is 50-79% complete (some clear info, some gaps)
- Multiple reasonable interpretations exist
- Project context is partially specified
- Technical approach options exist (caching strategy, database choice, etc.)
- Timeline or scope is implied but not stated

✅ **Consider using:**
- Request is borderline (80% complete but one key gap)
- Assumptions will significantly affect output quality

❌ **Don't use:**
- Request is ≥80% complete (proceed directly)
- Request is <50% complete (ask 1-3 clarifying questions first)
- Request is trivial (just answer)

---

## Example: Real Use Case

### Request:
*"Build a comments system for our platform."*

**Clarity: 40% — Ask clarifying questions first**

---

### Request (After clarification):
*"Build a comments system for our web app. It should support nested replies, upvoting, and moderation. We have React on the frontend and Node.js on the backend."*

**Clarity: 65% — Use this template**

### Response Using Template:

```markdown
## Request Context

**What I understood:**
You need a full comments system (frontend + backend) with nested replies, voting, and moderation for your React + Node.js platform.

**Clarity level:** 65% (good intent, some implementation details missing)

**What you explicitly told me:**
- Frontend: React
- Backend: Node.js
- Features: nested replies, upvoting, moderation
- Existing platform (so I should follow your patterns)

**What is missing or unclear:**
- Database choice (PostgreSQL? MongoDB? )
- Real-time requirements (WebSocket? Polling?)
- Moderation system details (flags? reviewer queue? auto-filtering?)

## Operating Constraints

**Project assumptions I'm applying:**
- Following REST API patterns (common for Node.js + React)
- Assuming modern best practices for security (input validation, authorization)

**Technical assumptions:**
- Database supports ACID transactions (needed for voting consistency)
- Authentication system already exists (I'll assume JWT)

**Scope assumptions:**
- Comments are public (not private DMs)
- Single-level moderation (comments flagged, then reviewed)

## Explicit Assumptions (proceeding with these)

**1. Database: PostgreSQL**
   - What I assume: You use PostgreSQL for relational data consistency
   - Why: Enables transactions for voting, most common with Node.js teams
   - If wrong: I'd adjust to MongoDB (different schema, eventual consistency)
   - Override with: "We actually use [database]"

**2. Real-time not required initially**
   - What I assume: New comments appear after refresh, not live
   - Why: Simplifies initial implementation, WebSocket can be added later
   - If wrong: I'll add Socket.io from the start
   - Override with: "Comments must appear live"

**3. Upvoting is user-per-comment (one vote each)**
   - What I assume: Each user can vote once per comment, can change their vote
   - Why: Prevents vote manipulation, common pattern
   - If wrong: I'll adjust to allow multiple votes or weighted voting
   - Override with: "Actually votes work like [your system]"

**4. Moderation is flag-then-review**
   - What I assume: Users report comments → moderators review in a queue → approve/delete
   - Why: Scalable, human-controlled, clear audit trail
   - If wrong: I'll add auto-filtering, community voting to remove, etc.
   - Override with: "Moderation should work like [your approach]"

**5. Nested depth is unlimited**
   - What I assume: Comments can reply to replies infinitely
   - Why: You said "nested replies" without depth limit
   - If wrong: I'll add max 3-4 levels of nesting
   - Override with: "Limit nesting to [X levels]"

**6. Authentication already exists**
   - What I assume: You have login/user identity working (I won't build auth)
   - Why: You mentioned "our platform" (auth is foundational)
   - If wrong: I'll include basic JWT auth from scratch
   - Override with: "I need you to build auth too" or "We use [system]"

**7. Comments are global (not page-scoped initially)**
   - What I assume: Comments appear in one timeline, can be filtered/sorted
   - Why: Simpler than per-page commenting, more common for discussion platforms
   - If wrong: I'll scope comments to pages/posts
   - Override with: "Comments should be for [specific pages]"

**8. No spam filtering initially**
   - What I assume: You'll use human moderation first, automate spam filtering later
   - Why: Reduces complexity, easier to iterate
   - If wrong: I'll add rate limiting and keyword filtering
   - Override with: "Add spam protection by [method]"

## Decision Triggers

**If you tell me...**
- "Actually, MongoDB, not PostgreSQL" → I'll change schema design to document model
- "Comments must appear instantly (WebSocket)" → I'll add Socket.io + real-time architecture
- "Moderation is automated (AI filtering)" → I'll add ML integration points
- "Comments are page-scoped" → I'll add page context to schema and APIs
- "Users can vote multiple times" → I'll change vote table structure to allow multiple votes per user

**Before I build this, tell me if any of these assumptions are wrong.**

## Proceeding With

Assuming the above, I will now:
1. Design PostgreSQL schema (comments, votes, moderation flags tables)
2. Build Node.js REST APIs (GET, POST comments; vote endpoints; moderation queue)
3. Build React components (comment list, reply form, vote buttons, moderation UI)
4. Include error handling and validation
5. Provide testing strategy

You can interrupt anytime with "Actually, assume..." and I'll regenerate the affected section.
```

---

## Integration in Skills

### For SDS Component 5 (Decision Engine)

When the skill receives a request in Phase 2 (Initial Clarification):

```markdown
### Phase 2: Initial Clarification

If the request is 50-79% complete:
1. Apply the [ASSUMPTION-TEMPLATE.md](../docs/ASSUMPTION-TEMPLATE.md)
2. Document 7-10 domain-specific assumptions with reasoning
3. Provide decision triggers showing what corrections would change output
4. Proceed with output under these assumptions
5. Invite clarification before final delivery

If <50% complete: Ask 1-3 clarifying questions instead, then return to Phase 2.
If ≥80% complete: Skip to Phase 3 (Assessment).
```

### For SDS Component 9 (Output Templates)

Add assumption section to Mode 1 and Mode 2 outputs:

```markdown
## Mode 1: Code Generation

Include this before code:

### Assumptions Behind This Code
- [Assumption 1 with override]
- [Assumption 2 with override]

See [ASSUMPTION-TEMPLATE.md](../docs/ASSUMPTION-TEMPLATE.md) for full reasoning.

[Generated code follows]

## Mode 2: Architecture Review

Include this before recommendations:

### Assumptions in This Review
- [Assumption 1 with override]
- [Assumption 2 with override]

See [ASSUMPTION-TEMPLATE.md](../docs/ASSUMPTION-TEMPLATE.md) for full reasoning.

[Architecture recommendations follow]
```

---

## Key Principles

1. **Assumptions are not apologies.** State them clearly and proceed. Ambiguity is normal; documented uncertainty is professional.

2. **Make them easy to override.** Each assumption includes "If wrong: [what changes]" so corrections are scoped and fast.

3. **Bias toward action.** Document assumptions and move forward. Block indefinitely only on <50% clarity requests.

4. **Domain-specific matters.** The 7-10 assumptions vary by skill; architecture assumptions differ from React assumptions differ from security assumptions. Customize the template.

5. **Transparency builds trust.** Showing your reasoning — what you assumed and why — makes output more credible and easier to correct.

---

## Maintenance

- Review this template quarterly as Phase 1 & 2 skills ship
- Collect feedback on assumption quality from real-world use
- Update decision triggers as common clarifications emerge
- Share this template across all AI platforms (Claude, GPT, Gemini, etc.)

**License:** MIT. This template belongs to everyone.

---

*ASSUMPTION-TEMPLATE.md · SkillOS · Phase 1 Refinement · Last updated: July 2026*
