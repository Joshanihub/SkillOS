# SkillOS Testing Strategy

**For ensuring skill quality, reliability, and production readiness across all tiers.**

This document formalizes how skills are tested, what constitutes "validation complete," and how different model tiers handle different test types.

---

## Overview

| Tier | Model Examples | Test Complexity | Validation Gate | Time per Skill |
|---|---|---|---|---|
| **Tier 0** | Sonnet 5, GPT-5.5, Gemini 3.5 Pro | Full 3-test suite | Required for publication | 2-3 hours |
| **Tier 1** | Sonnet mini, GPT-5.5 mini, Flash | 2-test suite | Required for publication | 1-2 hours |
| **Tier 2** | Haiku, Llama 4, Qwen 3 | 1-test suite | Optional (graceful degradation) | 30-45 min |
| **Tier 3** | Older/smaller models | Smoke test only | Not required | 15 min |

**Goal:** Every published skill has **minimum 3 test results** from Tier 0 or Tier 1 models.

---

## The Three-Test Standard

Every skill **must pass** three test scenarios before publication. Tests exercise different aspects of the Decision Engine.

### Test 1: Simple, Well-Scoped Request

**What this tests:** Can the skill execute straightforward requests correctly?

**Test format:**
```yaml
Request: [Simple, unambiguous request in skill's domain]
Example: "Design a REST API for a blog platform with posts, comments, and users"

Expected output:
- Correct architectural decision (monolith vs. microservices, DB choice)
- No excessive hedging (>90% confidence)
- Actionable recommendations (not vague)
- All 13 SDS components referenced implicitly

Pass criteria:
- Output is architecturally sound ✓
- Output is specific and actionable ✓
- Output matches Tier 0 quality baseline ✓
- Decision reasoning is clear ✓
```

### Test 2: Ambiguous, Real-World Request

**What this tests:** Can the skill handle ambiguity gracefully? Does it surface assumptions?

**Test format:**
```yaml
Request: [70-85% clear request; multiple interpretations possible]
Example: "We're scaling our backend. What should we change?"

Expected output:
- Skill surfaces ambiguity without blocking ✓
- Uses Assumption Documentation Template ✓
- Asks 0-1 clarifying questions (max) ✓
- Lists 7-10 explicit assumptions ✓
- Provides preliminary recommendation (doesn't stall) ✓

Pass criteria:
- Uses assumption template correctly ✓
- Assumptions are specific, not generic ✓
- Decision triggers are actionable ✓
- Output is complete despite ambiguity ✓
```

### Test 3: Edge Case or Constraint-Heavy Request

**What this tests:** How does the skill handle hard constraints? Does it degrade gracefully or fail clearly?

**Test format:**
```yaml
Request: [High-constraint scenario; skill at edge of expertise]
Example: "Design backend for real-time multiplayer game with <50ms latency,
          10,000 concurrent players, sub-$100/month server cost, only 2 engineers"

Expected output:
- Acknowledges constraints explicitly ✓
- Proposes viable architecture despite constraints ✓
- Surfaces trade-offs clearly ✓
- Defers to specialists where needed ✓
- Does NOT make unrealistic promises ✓

Pass criteria:
- Constraints acknowledged and addressed ✓
- Trade-offs are clear (cost vs. latency, for example) ✓
- Recommendation is feasible ✓
- Confidence is appropriately calibrated (not false confidence) ✓
```

---

## Model-Tier-Specific Testing Guidance

### Tier 0 Models (Sonnet 5, GPT-5.5, Gemini 3.5 Pro)

**Use these models for:** Publishing validation. Cross-model quality assurance. Skill Creator execution.

**Testing protocol:**

1. **Execute all 3 tests** on same model
2. **Record results** in Component 13 (Validation Record):
   ```yaml
   model: "Claude Sonnet 5"
   timestamp: 2026-07-14T10:30:00Z
   tests:
     simple_request:
       status: "pass"
       notes: "Straightforward architecture decision, well-reasoned"
     ambiguous_request:
       status: "pass"
       notes: "Surfaced 9 assumptions, asked 0 clarifying questions"
     edge_case_request:
       status: "pass"
       notes: "Handled tight constraints well, acknowledged trade-offs"
   overall_verdict: "pass"
   confidence: 95%
   ```

3. **Re-run on different Tier 0 model** (e.g., test on Sonnet, validate on GPT-5.5)
4. **Compare results** — if all 3 match: Skill is **stable**. If 1-2 diverge: Document divergence; note model dependency.

**Acceptance criteria:**
- All 3 tests pass ✓
- Confidence ≥90% ✓
- No assumptions violated ✓

### Tier 1 Models (Sonnet mini, GPT-5.5 mini, Gemini Flash)

**Use these models for:** Daily production use. Ongoing monitoring. Cost-conscious validation.

**Testing protocol:**

1. **Execute Tests 1 & 2 only** (simple + ambiguous; skip edge case)
2. **Record results** in Component 13
3. **Optional:** Run on second Tier 1 model
4. **Expected outcome:** 90-95% parity with Tier 0 results

**Acceptance criteria:**
- Tests 1 & 2 pass ✓
- Tier 0 vs. Tier 1 divergence <10% ✓
- Confidence ≥85% ✓

### Tier 2 Models (Haiku, Llama 4, Qwen 3)

**Use these models for:** Graceful degradation testing. Learning/educational use. Cost baseline.

**Testing protocol:**

1. **Execute Test 1 only** (simple request)
2. **Record results** in Component 13
3. **Expected outcome:** 80-90% parity with Tier 0

**Acceptance criteria:**
- Test 1 passes ✓
- Output is reasonable (not perfect, but valid) ✓
- No catastrophic failures ✓

### Tier 3 Models (Older models, open-source, bleeding-edge)

**Use these models for:** Smoke testing. Community contribution testing.

**Testing protocol:**

1. **Run Test 1 once**
2. **Smoke test:** Does the skill execute without errors? Does output make sense?
3. **Record:** Pass/Fail only (no detailed Component 13 entry required)

**Acceptance criteria:**
- Skill executes ✓
- No crashes or timeout ✓
- Output is not nonsensical ✓

---

## Cross-Model Validation Protocol

**When:** After a skill achieves Tier 0 validation (3/3 pass), run cross-model validation.

**How:** Test the same skill on 2-3 different Tier 0/1 models. Compare results.

**Compare on:**
- **Output quality** — Is recommendation the same?
- **Reasoning path** — Does the decision logic match?
- **Assumption handling** — Same assumptions surfaced?
- **Confidence calibration** — Does each model rate confidence similarly?

**Record in Component 13:**
```yaml
cross_model_validation:
  model_1:
    name: "Claude Sonnet 5"
    test_1_result: "pass"
    test_2_result: "pass"
    test_3_result: "pass"
  model_2:
    name: "GPT-5.5"
    test_1_result: "pass"
    test_2_result: "pass"
    test_3_result: "pass"
  model_3:
    name: "Gemini 3.5 Pro"
    test_1_result: "pass"
    test_2_result: "pass"
    test_3_result: "pass"
  divergence_analysis: "All three models agreed on core architecture. Minor wording differences only."
  confidence: "Skill is model-agnostic"
```

**Publishing criteria after cross-model validation:**
- All Tier 0 models pass all tests ✓
- Tier 1 model passes Tests 1 & 2 ✓
- Divergence <5% on core recommendation ✓
- Mark skill as **STABLE** in Component 1 metadata

---

## Domain-Specific Testing Extensions

### Tier 0 Skills (Foundation: Architecture, Security, Performance)

**Additional Test 4 (Optional but recommended):**
- **Organizational Impact Scenario** — Does the skill account for team dynamics?
- Example: "Design backend for a 5-person startup transitioning from monolith"
- This tests whether the skill recommends appropriately simple architectures, not over-engineering

### Tier 1 Skills (Domain: Frontend, Backend, DevOps, Database)

**Additional Test 4 (Optional but recommended):**
- **Cross-Tier Coordination** — Can this skill coordinate with complementary Tier 1 skills?
- Example: Frontend Specialist receives API contract from Backend Specialist (routed via Tier 0)
  - Does Frontend Specialist use it correctly?
  - Does recommendation align with Backend design?

### Tier 2 Skills (Technology: React, TypeScript, PostgreSQL)

**Additional Test 4 (Optional but recommended):**
- **Versions & Deprecation** — Does the skill stay current with ecosystem?
- Example: React Expert tested on React 18, 19, 20 (when available)
  - Does recommendation change with version?
  - Are deprecations acknowledged?

---

## Quality Gates Checklist — Before Publication

```yaml
Pre-Publication Quality Gate:
  ✅ All 13 SDS components present
  ✅ Component 5 (Decision Engine) uses branching logic, not prose
  ✅ Component 7 (Failure Mode Library) has ≥15 domain-specific failures
  ✅ Component 13 (Validation Record) has ≥3 test results
  
  ✅ Test 1 (Simple): PASS
  ✅ Test 2 (Ambiguous): PASS  
  ✅ Test 3 (Edge Case): PASS
  
  ✅ Tested on minimum 2 different Tier 0 models
  ✅ Cross-model divergence <5%
  ✅ Assumption Documentation Template used correctly (if Test 2 required it)
  ✅ Ethical constraints reviewed (Component 10)
  
  ✅ README mentions skill (with tier, domain, link)
  ✅ registry/README.md includes skill in matrix
  ✅ Skill file includes compatible_with list (Component 1 metadata)
  
  ✅ Git commit message follows convention: "feat: add [skill] to registry (tier-[N])"
```

---

## Monitoring & Continuous Testing

After publication, skills should be tested periodically:

- **Monthly (Tier 0/1):** Re-run Tests 1 & 2 on latest models to detect regressions
- **Quarterly:** Full 3-test suite
- **When model versions change:** Immediate cross-model validation
- **When component updates:** Test only affected components

---

## Reporting Results

### For Individual Skill Validation

```markdown
## Validation Results — [Skill Name] v[X.Y.Z]

**Skill:** [Name]
**Version:** [X.Y.Z]
**Tested:** [Date]
**Models:** [Model A, Model B, Model C]

### Test Results

| Test | Model A | Model B | Model C | Overall |
|---|---|---|---|---|
| Test 1 (Simple) | ✅ PASS | ✅ PASS | ✅ PASS | ✅ PASS |
| Test 2 (Ambiguous) | ✅ PASS | ✅ PASS | ✅ PASS | ✅ PASS |
| Test 3 (Edge Case) | ✅ PASS | ✅ PASS | ✅ PASS | ✅ PASS |

**Overall Verdict:** ✅ STABLE  
**Cross-Model Divergence:** <2%  
**Confidence:** 96%

### Notes
[Any observations about model-specific behavior, assumption handling, edge cases]
```

### For Registry-Wide Testing Report

```markdown
## Registry Validation Report — [Date]

**Total Skills:** 7
**Tier 0:** 1 (100% validated)
**Tier 1:** 3 (100% validated)
**Tier 2:** 3 (2 validated, 1 in progress)

### Model Coverage

| Model | Skills Tested | Avg Pass Rate | Status |
|---|---|---|---|
| Claude Sonnet 5 | 7/7 | 100% | ✅ |
| GPT-5.5 | 7/7 | 98% | ✅ |
| Gemini 3.5 Pro | 6/7 | 97% | ✅ in progress |

### Skills Ready for Production
✅ Software Architect v1.0.3 (Tier 0)
✅ Frontend Specialist v1.0.1 (Tier 1)
✅ React Expert v1.0.1 (Tier 2)

### Skills In Validation
🔄 [Next skill in queue]
```

---

## Test Failure Protocol

**If a skill fails Test 1 (Simple):**
→ Skill has fundamental flaw. Do not publish. Return to Skill Creator for redesign.

**If a skill fails Test 2 (Ambiguous):**
→ Skill doesn't handle ambiguity well. Likely: Decision Engine logic is too rigid.
→ Fix: Add conditional branches for ambiguous cases; review Assumption Documentation Template integration.

**If a skill fails Test 3 (Edge Case):**
→ Skill doesn't degrade gracefully. Likely: Confidence is miscalibrated or constraints aren't checked.
→ Fix: Add edge case detection to Decision Engine; review Failure Mode Library; calibrate confidence.

**If cross-model divergence >5%:**
→ Skill may be model-dependent. Document in metadata.
→ Possible causes: Skill relies on specific phrasing/jailbreak, Decision Engine has ambiguous branching logic.
→ Fix: Simplify Decision Engine; make it more explicit and less prompt-dependent.

---

## Tool for Tracking Tests

Use SkillOSTests.md (session-local) to track ongoing tests:

```markdown
## SkillOSTests.md — Active Testing Log

### Session: 2026-07-14

**Skill: Security Principles v1.0.0**
- Model: Claude Sonnet 5
- Test 1 (Simple): ✅ PASS — "Design auth system for SaaS" → correct OAuth2 recommendation
- Test 2 (Ambiguous): ✅ PASS — "Secure our database" → surfaced 8 assumptions, asked 0 clarifying Q
- Test 3 (Edge Case): ✅ PASS — "Secure 1000-person org with $5K/year budget" → realistic constraints, no over-engineering

Cross-model validation (GPT-5.5): ✅ PASS (100% alignment on recommendations)

**Ready for publication:** YES → Move to registry/tier-0/

**Skill: Backend Specialist v1.0.0**
[Test results here...]
```

---

## Summary: What "Validation Complete" Means

✅ **Publication-Ready (Tier 0/1 skill):**
- 3/3 tests pass on Tier 0 model ✓
- 2/2 tests pass on at least 1 other Tier 0 or Tier 1 model ✓
- Component 13 (Validation Record) filled with model names, timestamps, results ✓
- Cross-model divergence <5% ✓
- Skill marked as `status: stable` in Component 1 ✓
- Added to README registry matrix ✓
- Committed with message: `feat: add [skill] to registry (tier-[N])`  ✓

✅ **Production-Ready (ongoing):**
- Monthly re-validation on latest models ✓
- No regressions in Tests 1 & 2 ✓
- Updated to handle new model versions ✓
- Receives community feedback & improvement PRs ✓

---

**Testing-Strategy.md · SkillOS v1.1**  
**Version:** 1.1.0  
**Last Updated:** 2026-07-14  

*Formalized testing protocol for all SkillOS skills. Use in conjunction with SKILL-DEFINITION-STANDARD.md, SKILL-CREATOR.md, and validation/test-harness.md*
