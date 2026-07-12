# SkillOS Validation Test Harness v1.0

Every skill must pass these three tests before it can be published to the registry.

Record results in the skill's Component 13 (Validation Record).

---

## How to Run Tests

1. **Install the skill** as a system prompt in a Claude Project, ChatGPT, Gemini, or compatible interface
2. **Send each test prompt** exactly as written
3. **Evaluate the response** against the pass criteria below
4. **Record results:** pass | fail + observations
5. **Submit** Validation Record with your PR

---

## Test 1 — Simple Request

**Purpose:** Does the skill produce clean, correct, useful output on a well-specified request without overengineering?

This tests: core competence, appropriate complexity, template adherence, quality gates.

### Generic Template

\\\
[Clear, well-specified request squarely within the skill's documented domain]
[Include sufficient context for the skill to proceed without asking questions]
[Request should map to Mode 1 (Code Generation) or Mode 2 (Architecture Review)]
[Make it realistic — something a real engineer would ask]
\\\

### Example: React Specialist

\\\
Build me a reusable React form component with TypeScript that:
- Accepts field definitions (name, type, validation rules)
- Handles form state internally with hooks
- Shows validation errors inline
- Provides a clean API for parent components

Make it production-ready and explain the design decisions.
\\\

### Pass Criteria

- [ ] Skill produces output without unnecessary clarifying questions
- [ ] Output follows the appropriate Output Template (Component 9)
  - Mode 1 (Code Generation) should include: Problem Analysis, Approach, Implementation, Trade-offs, Quality Notes
  - Mode 2 (Architecture Review) should include: Current State, Risk Surface, Recommendations, Migration Path
- [ ] Quality gates are visible (output is complete, assumptions documented, edge cases acknowledged)
- [ ] Ethical constraint layer shows evidence of having run
- [ ] Output is accurate and domain-appropriate
- [ ] Output does not assume a default language, region, or infrastructure
- [ ] If TypeScript: types are specific (no excessive \ny\)
- [ ] If accessibility-relevant: WCAG considerations are mentioned
- [ ] Code/output is production-ready (not pedagogical)

### Fail Indicators

- ❌ Skill asks clarifying questions when the request was ≥80% complete
- ❌ Output is generic rather than domain-specific
- ❌ Output is missing critical sections from the Output Template
- ❌ Output recommends deprecated practices as current
- ❌ Code has obvious bugs or security issues
- ❌ Output ignores stated constraints

---

## Test 2 — Ambiguous Request

**Purpose:** Does the skill correctly handle an under-specified request — asking ONE focused question OR proceeding with documented assumptions?

This tests: ambiguity resolution, constraint handling, assumption documentation, decision logic.

**The core rule:** NEVER block indefinitely. Either ask one focused question OR proceed with documented assumptions. No exceptions.

### Generic Template

\\\
[Request with 50-70% completeness — meaningful but missing key constraints]
[Do NOT specify some critical context: team size, performance requirements, regulatory context, timeline, budget]
[Make it genuine — something that actually has ambiguity, not nonsense]
\\\

### Example: React Specialist

\\\
I need to optimize my React application's performance. It's currently slow on mobile devices. 
How should I approach this?
\\\

(This is ambiguous: What's slow? Where's the bottleneck? What devices? What's "slow" — 5s, 10s? 
What's the priority: load time or runtime performance? Users or clicks matter? etc.)

### Pass Criteria

- [ ] If skill asks for clarification: **asks exactly ONE focused question**, not a list
  - ✅ "What's your primary performance bottleneck: initial load time or runtime responsiveness?"
  - ❌ "Tell me: (1) your metrics (2) team size (3) timeline (4) budget (5) current stack"
- [ ] If skill proceeds without asking: documents assumptions explicitly and inline
  - ✅ "I'm assuming your bottleneck is runtime performance (not load time), based on your mention of mobile. If that's wrong, let me know."
- [ ] Skill does NOT ask five clarifying questions before doing anything
- [ ] Skill does NOT refuse to proceed, saying "I need more information"
- [ ] Whatever the skill produces is still useful despite the ambiguity
- [ ] Assumptions are surfaced prominently, not buried

### Fail Indicators

- ❌ Skill asks more than one clarifying question
- ❌ Skill refuses to proceed ("I need more information before proceeding")
- ❌ Skill proceeds but buries assumptions without surfacing them
- ❌ Skill produces confident output without acknowledging ambiguity
- ❌ Skill asks "What do you want me to do?" or similar non-specific follow-ups

---

## Test 3 — Edge Case / Domain Boundary

**Purpose:** Does the skill recognize when a request falls at or beyond its domain boundary, and route cleanly rather than hallucinating?

This tests: boundary awareness, routing logic, refusal pattern, collaboration protocol.

### Generic Template

\\\
[Request that touches the skill's domain but requires expertise from an adjacent domain]
OR
[Request that is clearly outside the skill's documented capability boundaries]

The skill should recognize the boundary, route appropriately, not pretend it can handle everything.
\\\

### Example: React Specialist

\\\
Build me a React component that tracks user behavior and sends analytics data to our backend, 
plus integrate it with our authentication system so only logged-in users see this data.
\\\

(This touches React — the component itself. But it involves: backend integration, authentication 
system design, data privacy/compliance. The skill should handle the React part, route the auth 
part, and mention data privacy considerations.)

### Pass Criteria

- [ ] Skill correctly identifies which part is in-scope and which is out-of-scope
- [ ] Skill routes the out-of-scope portion to the correct adjacent skill
  - React → Performance issue → DevOps Specialist
  - React → Auth design → Security Principles / Authentication Pattern skill
  - React → Data compliance → Security Principles / Data Privacy skill
- [ ] Skill handles the in-scope portion of the request correctly
- [ ] Skill does not hallucinate expertise it doesn't have
- [ ] Skill does not refuse the entire request when part of it is in-scope
- [ ] Routing is specific (not just "ask a backend engineer")

### Fail Indicators

- ❌ Skill attempts to answer everything regardless of domain boundary
- ❌ Skill refuses the entire request because part of it is out-of-scope
- ❌ Skill routes to the wrong adjacent skill
- ❌ Skill provides confident but incorrect guidance outside its domain
- ❌ Skill has no routing logic (no idea where to send things)

---

## SDS Compliance Check

Before recording validation results, verify all 13 components:

`
COMPONENT PRESENCE
□ Component 1 — Skill Metadata: YAML block present and complete
□ Component 2 — Professional Identity: Realistic, specific, confidence calibration present
□ Component 3 — Knowledge Taxonomy: Hierarchical structure. Evolution registry subsection present.
□ Component 4 — Capability Boundaries: Explicit in-scope AND out-of-scope with routing table
□ Component 5 — Decision Engine: Branching logic, not prose. Ambiguity protocol explicit.
□ Component 6 — Constraint Matrix: All 13 constraints mapped with domain-specific weights
□ Component 7 — Failure Mode Library: 15+ entries, all domain-specific (not generic)
□ Component 8 — Quality Gates: Universal + domain-specific. Not just generic defaults.
□ Component 9 — Output Templates: 4+ modes with defined structures (Code, Review, Debug, Teach)
□ Component 10 — Ethical Constraint Layer: Universal 3 + domain-specific rules (not just the 3)
□ Component 11 — Safety Layer: 4 universal checks + domain-specific additions
□ Component 12 — Collaboration Contract: Typed I/O in YAML format
□ Component 13 — Validation Record: Template present (results filled in after testing)

GLOBAL COMPLIANCE
□ No language assumed as default
□ No region or jurisdiction assumed as default
□ No infrastructure stack assumed as default (not AWS, not US-timezone, etc.)
□ License: MIT
□ Professional Identity includes confidence calibration
□ Failure modes are domain-specific (not generic)
□ Output templates are domain-specific
□ Ethical constraints include domain-specific rules beyond universal three

All boxes must be checked for SDS compliance: PASS
`

---

## Recording Validation Results

**Template for Component 13 (Validation Record):**

\\\yaml
validation_date: 2025-07-12
validated_by: [GitHub handle or "community"]
model_tested_on: [Model name and version. e.g., "Claude 3.5 Sonnet"]
sds_compliance: pass | fail

test_1_simple:
  prompt: "[Exact test prompt used — copy from test harness]"
  result: pass | fail
  evidence:
    - "[Specific observation from the output]"
    - "[Did it follow Output Template correctly?]"
    - "[Were assumptions documented?]"
  notes: "[Any other observations]"

test_2_ambiguous:
  prompt: "[Exact test prompt used]"
  result: pass | fail
  evidence:
    - "[Did it ask one question or proceed with assumptions?]"
    - "[Were assumptions surfaced prominently?]"
    - "[Was the output still useful despite ambiguity?]"
  notes: "[Any other observations]"

test_3_edge_case:
  prompt: "[Exact test prompt used]"
  result: pass | fail
  evidence:
    - "[Did it correctly identify the domain boundary?]"
    - "[Did it route to the correct skill?]"
    - "[Did it handle the in-scope part correctly?]"
  notes: "[Any other observations]"

overall_result: pass | fail
regression_notes:
  - "[Any patterns observed across tests]"
  - "[Recommendations for future versions]"
  - "[Anything that should inform the evolution registry]"
\\\

---

## Submission Checklist

Before submitting your skill:

- [ ] All three tests run and recorded
- [ ] Overall result: **pass**
- [ ] SDS compliance: **all boxes checked**
- [ ] Skill file placed in correct \egistry/tier-X/\ directory
- [ ] File name follows convention: \[skill_name]-v[version].md\
- [ ] Validation Record is complete and accurate
- [ ] PR includes one-paragraph description of what the skill solves

---

## Interpreting Results

**All three tests pass?** ✅ Ready to submit.

**One or more tests fail?** ❌ Fix and re-test.
Common reasons:
- Missing output template sections
- Assumptions not documented
- Boundary not recognized (skill hallucinated outside domain)
- Excessive clarifying questions
- Generic guidance instead of domain-specific

**SDS compliance check catches issues?** ❌ Review SKILL-DEFINITION-STANDARD.md for the missing component.

---

## Community Validation

After a skill is merged, the community may run additional tests:
- Testing on models not in the original validation (e.g., Gemini, Mistral)
- Testing in non-English languages
- Long-running usage patterns
- Production edge cases

If you discover a skill producing incorrect or outdated output:
- Open an issue describing the problem
- Include the test prompt, expected behavior, actual behavior
- The maintainer will review and update the skill

---

*Test Harness v1.0 · SkillOS · MIT License · Built for reliability at scale*
