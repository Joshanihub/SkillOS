# Phase 2: Manual Validation Guide

**Goal:** Run the three test prompts on each pilot skill. Record observations.

**Time:** ~45 minutes (15 min per skill)

---

## For Each of the 3 Skills

### 1. Software Architect (tier-0)

**Install as system prompt:**
- Open Claude.ai / ChatGPT / Gemini
- Create a new conversation
- Paste the Software Architect identity and system prompt from `registry/tier-0/software-architect-v1.0.0.md`

**Run the three test prompts** (already written in the skill's Validation Record):

**Test 1 — Simple (Straightforward domain question):**
```
I'm building a new SaaS application with 3 engineers. We expect 
10K daily active users in year 1, potentially 100K in year 3. 
What's the right initial architecture?
```
**Pass if:** Asks clarifying questions about reliability requirements, 
cost sensitivity, and team constraints before recommending architecture.

**Test 2 — Ambiguous (Underspecified scenario):**
```
We're having scaling problems and need a better architecture.
```
**Pass if:** Routes back with specific clarifying questions rather than 
making assumptions. Doesn't hallucinate requirements.

**Test 3 — Edge Case (Boundary condition):**
```
We have a PostgreSQL query that runs 60 seconds on 1M rows. 
How do we fix it?
```
**Pass if:** Acknowledges this might be a database specialist question, 
defers appropriately, but offers high-level systemic approaches 
(partitioning, read replicas, caching patterns).

---

### 2. Frontend Specialist (tier-1)

**Install as system prompt:**
- Create a new conversation
- Paste the Frontend Specialist identity and system prompt from `registry/tier-1/frontend-specialist-v1.0.0.md`

**Run the three test prompts:**

**Test 1 — Simple:**
```
Should we use CSS Modules, TailwindCSS, or styled-components 
for a new React application?
```
**Pass if:** Acknowledges trade-offs and asks about team preference 
and project constraints before recommending.

**Test 2 — Ambiguous:**
```
Our frontend is slow.
```
**Pass if:** Routes with specific diagnostic questions (time to interactive? 
Which pages slow? Network or rendering?). Doesn't guess.

**Test 3 — Edge Case:**
```
We need to display 50K rows in a table. How do we make 
it performant?
```
**Pass if:** Recommends virtualization, pagination, or lazy loading. 
Acknowledges this might need database specialist input for filtering.

---

### 3. React Expert (tier-2)

**Install as system prompt:**
- Create a new conversation
- Paste the React Expert identity and system prompt from `registry/tier-2/react-expert-v1.0.0.md`

**Run the three test prompts:**

**Test 1 — Simple:**
```
How do I structure a large React application with 50+ components?
```
**Pass if:** Recommends specific patterns (component isolation, feature folders, 
custom hooks library). Asks about scale and team structure.

**Test 2 — Ambiguous:**
```
My React component is rendering too often.
```
**Pass if:** Routes with diagnostic questions (which component? What triggers 
re-renders? Is it a state or context issue?). Offers systematic debugging approach.

**Test 3 — Edge Case:**
```
I need to coordinate state across 20 different components that 
aren't in the same tree. What's the best approach?
```
**Pass if:** Discusses context, state management libraries (Redux, Zustand), 
or architectural patterns. Acknowledges the scope.

---

## Recording Your Results

After running all three tests on each skill, note:

**For each test:**
- ✅ **Pass** — skill stayed in scope, responded helpfully, routed out-of-scope requests cleanly
- ❌ **Fail** — skill hallucinated, made invalid assumptions, or couldn't recognize limits

**Observations:**
- Did the skill follow the Capability Boundaries?
- Did the skill route appropriately to other specialists?
- Any notable errors or gaps?

---

## What to Expect

**If all three tests pass for a skill:** Everything is working as intended. The skill knows its domain, its limits, and how to collaborate.

**If a test fails:** Note what happened. Skills can be updated (Phase 3).

---

## Next Steps

Once you complete Phase 2, tell me your results:
- Software Architect: Test 1 [pass/fail], Test 2 [pass/fail], Test 3 [pass/fail] + observations
- Frontend Specialist: Test 1 [pass/fail], Test 2 [pass/fail], Test 3 [pass/fail] + observations
- React Expert: Test 1 [pass/fail], Test 2 [pass/fail], Test 3 [pass/fail] + observations

I'll update the Validation Record in each skill file with your observations and commit.

---

*Last updated: 2026-07-12*
