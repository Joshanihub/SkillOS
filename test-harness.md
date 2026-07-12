# SkillOS Validation Test Harness v1.1

Every skill must pass these three standardized tests before it can be
published to the registry. Results are recorded in the skill's Component 13
(Validation Record). No skill enters the registry with `overall_result: fail`.

---

## What These Tests Verify

These tests do not check if a skill sounds good. They check if a skill
**behaves correctly** under the three conditions that matter in real use:

**Test 1** — Does the skill produce clean, correct output when the request is clear?
**Test 2** — Does the skill handle ambiguity with the correct protocol?
**Test 3** — Does the skill recognize its own limits and route cleanly?

A skill that passes all three can be trusted. A skill that fails any one
should not be in a registry that other people rely on.

---

## How to Run Tests

1. Install the skill as a system prompt in your AI interface of choice
2. Send each test prompt and evaluate the response against the pass criteria
3. Record `pass` or `fail` and your observations in Component 13
4. If the skill fails, revise and retest before submitting

**Model to test on:** Use any Tier 1 or Tier 2 model from the recommended
list in `SKILL-CREATOR.md`. Record exactly which model you tested on.

**Cross-model testing (encouraged):** If you test on multiple models, add
additional validation blocks to Component 13. Cross-model results help the
community understand where skills degrade and why.

---

## Test 1 — Simple Request

**Purpose:**
Does the skill produce clean, correct, useful output on a well-specified
request without overengineering, without unnecessary questions, and without
recommending deprecated practices?

**How to write the prompt:**
- Clear, well-specified request in the skill's documented domain
- Include enough context that the request is ≥80% complete
- Should map to Code Generation (Mode 1) or Architectural Review (Mode 2)
- Do not deliberately create ambiguity — this test is for clarity

**Pass criteria:**
- [ ] Skill proceeds without asking unnecessary clarifying questions
  (request was ≥80% complete; clarifying questions here is a fail)
- [ ] Output follows the appropriate Output Template from Component 9
- [ ] Assumptions are documented inline where made
- [ ] Quality gates are visibly applied (output is complete, edge cases noted)
- [ ] Ethical constraint layer shows evidence of having run
- [ ] Output is accurate and domain-specific — not generic engineering advice
- [ ] No deprecated practices recommended as current best practice
- [ ] No default language, region, or infrastructure assumed without disclosure

**Fail indicators:**
- Skill asks clarifying questions when request was clear and ≥80% complete
- Output is generic — could apply to any domain
- Output is missing sections defined in the Output Template
- Output recommends deprecated patterns (check evolution registry)
- Output assumes Western/English/AWS defaults without disclosing the assumption

---

## Test 2 — Ambiguous Request

**Purpose:**
Does the skill correctly handle an under-specified request — asking exactly
one focused clarifying question or proceeding with documented assumptions —
never asking multiple questions, never blocking indefinitely?

**How to write the prompt:**
- Meaningful request in the skill's domain but missing key constraints
- Aim for 50–79% completeness
- Omit: team size, performance requirements, regulatory context, timeline,
  specific technology preferences
- Must be genuine enough that the skill cannot dismiss it as nonsensical

**The Ambiguity Resolution Protocol the skill must follow:**
```
≥ 80% complete → proceed; document assumptions inline
50–79% complete → ask ONE focused question; then proceed
< 50% complete → ask maximum THREE questions; then proceed
NEVER → block indefinitely
NEVER → ask questions whose answers would not change the output
```

**Pass criteria:**
- [ ] If skill asks for clarification: asks exactly ONE focused question
  (not a list of five questions "to better understand your needs")
- [ ] If skill proceeds: documents assumptions explicitly and visibly inline
- [ ] Skill does NOT ask multiple clarifying questions
- [ ] Skill does NOT refuse to proceed pending more information
- [ ] Skill does NOT produce confident output without acknowledging ambiguity
- [ ] Whatever output it produces is still useful despite the ambiguity

**Fail indicators:**
- Skill asks more than one clarifying question
- Skill refuses to proceed without more information
- Skill produces confident output without acknowledging that key constraints were missing
- Skill proceeds but buries assumptions so they are not visible
- Skill asks questions whose answers would not materially change the approach

---

## Test 3 — Edge Case / Domain Boundary

**Purpose:**
Does the skill recognize when a request falls at or beyond its domain boundary,
route cleanly to the correct specialist, and handle the in-scope portion correctly
without hallucinating expertise it does not have?

**How to write the prompt:**
Write a request that either:
a) Touches the skill's domain but requires expertise from an adjacent domain, OR
b) Is clearly outside the skill's documented capability boundaries

The skill's Capability Boundaries section and Routing Table define what "edge case"
means for this specific skill.

**Pass criteria:**
- [ ] Skill correctly identifies that the request touches or exceeds its domain boundary
- [ ] Skill routes the out-of-scope portion to the correct skill by skill_name
- [ ] Skill handles the in-scope portion of the request correctly
- [ ] Skill does not hallucinate expertise beyond its documented capabilities
- [ ] Skill does not refuse the entire request when part of it is clearly in-scope

**Fail indicators:**
- Skill attempts to answer everything regardless of domain boundary
- Skill refuses the entire request because part of it is out of scope
- Skill routes to the wrong adjacent skill
- Skill provides detailed confident guidance on something outside its expertise
- Skill acknowledges the boundary but then crosses it anyway

---

## SDS Compliance Check

Run this before recording any validation results. All boxes must be checked
for the skill to pass SDS compliance.

```
□ Component 1  — Metadata YAML block present and complete
                  Includes: portability_notes, cultural_modes, temperature_range
□ Component 2  — Professional Identity: specific career arc, confidence calibration
□ Component 3  — Knowledge Taxonomy: hierarchical (not flat); evolution states per concept;
                  Evolution Registry section present with all 5 states labeled
□ Component 4  — Capability Boundaries: explicit in-scope AND out-of-scope;
                  routing table present; self-awareness declaration present
□ Component 5  — Decision Engine: all 10 phases present as branching logic (not prose);
                  ambiguity protocol thresholds explicit; temperature modes defined;
                  confidence scoring defined
□ Component 6  — Constraint Matrix: all 13 constraints with domain-specific weights;
                  cultural intelligence sub-component present;
                  global regulatory awareness present (non-Western jurisdictions included)
□ Component 7  — Failure Mode Library: 15+ entries; all domain-specific (not generic);
                  full format per entry (pattern, why, detection, prevention, impact)
□ Component 8  — Quality Gates: 10 universal gates present PLUS domain-specific gates
                  (not just the universal defaults)
□ Component 9  — Output Templates: 4+ modes with defined structures (not just names)
□ Component 10 — Ethical Constraint Layer: universal 3 rules PLUS domain-specific rules
                  (domain-specific rules must be present — generic 3 alone is insufficient)
□ Component 11 — Safety Layer: 4 universal checks PLUS domain-specific additions;
                  reversibility scale (LOW/MEDIUM/HIGH/CRITICAL) present
□ Component 12 — Collaboration Contract: typed YAML I/O; portability contract present;
                  upstream and downstream skills listed by skill_name
□ Component 13 — Validation Record: template present; three test prompts generated;
                  results pending (to be filled after testing)

□ No language assumed as default
□ No region or jurisdiction assumed as default
□ No infrastructure stack assumed as default
□ MIT license confirmed
□ File named correctly: [skill_name]-v[major].[minor].[patch].md
```

---

## Recording Results

Copy this block into Component 13 of your skill and fill in your results:

```yaml
validation_date: [ISO date e.g. 2026-07-12]
validated_by: [GitHub handle or "community"]
model_tested_on: [Specific model name and version]
sds_compliance: pass | fail

test_1_simple:
  prompt: [Exact prompt used — must be reproducible by others]
  expected: [What a passing response looks like — be specific]
  result: pass | fail
  notes: [What was good, what was weak, anything unexpected]

test_2_ambiguous:
  prompt: [Exact prompt used]
  expected: [One clarifying question OR proceed with documented assumptions]
  result: pass | fail
  notes: [Observations — what question it asked, how it handled ambiguity]

test_3_edge_case:
  prompt: [Exact prompt used]
  expected: [Recognize boundary; route correctly; handle in-scope portion]
  result: pass | fail
  notes: [How it handled the boundary — hallucination or clean routing]

overall_result: pass | fail

regression_notes:
  - [Patterns that should inform future versions]
  - [Specific things to watch for in this skill as it evolves]
```

**Cross-model validation (encouraged, not required for v1.0):**
```yaml
additional_validation:
  - model: [model name and version]
    date: [ISO date]
    validated_by: [GitHub handle]
    test_1_result: pass | fail
    test_2_result: pass | fail
    test_3_result: pass | fail
    degradation_notes: [What changed vs. the primary model]
```

---

## What "Pending" Means

Three skills in the registry currently show `result: pending`.
This means the skill has been compiled and SDS-reviewed but the
validation prompts have not yet been run by a human.

These skills are included in v1.0 because their compilation quality
is high, but they should be considered `experimental` status until
all three tests are run and recorded.

**If you want to run validation tests for the community:**
1. Install the skill as a system prompt
2. Run the three prompts already written in each skill's Component 13
3. Record your results
4. Submit a PR updating the Validation Record
5. If all three pass, the skill upgrades from `experimental` to `stable`

This is one of the most valuable contributions you can make right now.

---

## Test Prompt Writing Guidelines

When writing tests for a new skill you are contributing:

**Test 1 (Simple) should:**
- Be a real request you would actually make of this specialist
- Have enough context that any competent practitioner could answer it
- Test the skill's most common use case, not an unusual one

**Test 2 (Ambiguous) should:**
- Be genuinely under-specified — missing constraints that actually matter
- Not be so vague that the skill should reject it entirely
- Be a request you might realistically send before you knew what information was needed

**Test 3 (Edge Case) should:**
- Target a specific boundary documented in Component 4 (Capability Boundaries)
- Be a request that an inexperienced user might reasonably send to this skill
- Have a clear "correct" answer about which specialist should handle the out-of-scope portion

---

*Test Harness v1.1 · SkillOS · MIT License · Owned by the world*
