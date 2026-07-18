## Skill Contribution — Pull Request

> Complete every section before requesting review.
> A PR missing any section will be closed without merge — not to gatekeep,
> but because incomplete skills produce unreliable output in production.

---

### What This PR Adds or Changes

**Skill name:**
**Tier:** `[ ] 0  [ ] 1  [ ] 2  [ ] 3  [ ] 4`
**Version:** (e.g. `1.0.0`)
**Type:** `[ ] New skill  [ ] Skill update  [ ] Skill deprecation  [ ] Documentation  [ ] Infrastructure`

**One paragraph describing what problem this skill solves and who it helps:**



---

### SDS Compliance — All 13 Components

Every skill in this registry must contain all 13 SDS components.
Check each one confirming it is present and complete in your submission.

- [ ] **Component 1 — Skill Metadata** — YAML block present with `portability_notes` and `cultural_modes`
- [ ] **Component 2 — Professional Identity** — Specific career arc with confidence calibration (not generic seniority)
- [ ] **Component 3 — Knowledge Taxonomy** — Hierarchical structure with evolution states per concept (current/stable/legacy/deprecated/experimental)
- [ ] **Component 4 — Capability Boundaries** — Explicit in-scope AND out-of-scope list with routing table and self-awareness declaration
- [ ] **Component 5 — Decision Engine** — All 10 phases as branching logic (not prose); ambiguity protocol thresholds explicit
- [ ] **Component 6 — Constraint Matrix** — All 13 constraints with domain-specific weights; cultural intelligence sub-component present; non-Western regulatory regimes included
- [ ] **Component 7 — Failure Mode Library** — 15+ entries; every entry is domain-specific (not generic engineering advice); full format per entry
- [ ] **Component 8 — Quality Gates** — Universal 10 gates PLUS domain-specific gates (not just the universal defaults)
- [ ] **Component 9 — Output Templates** — 4+ modes with defined structures (not just named)
- [ ] **Component 10 — Ethical Constraint Layer** — Universal 3 rules PLUS domain-specific ethical rules (domain-specific rules required)
- [ ] **Component 11 — Safety Layer** — 4 universal checks PLUS domain-specific additions; reversibility scale (LOW/MEDIUM/HIGH/CRITICAL) present
- [ ] **Component 12 — Collaboration Contract** — Typed YAML I/O with upstream/downstream skills listed by `skill_name`; portability contract present; routing paths match `docs/CROSS-TIER-ROUTING-MAP.md`
- [ ] **Component 13 — Validation Record** — Three test results recorded (not `pending`); model used specified exactly

---

### Validation Results

**Model used for primary validation:**
(e.g. `claude-sonnet-5-20260401` — be specific, include version where known)

**Validation tier:** `[ ] Tier 1 (production readiness)  [ ] Tier 3 (graceful degradation only)`

> Note: Tier 3 validation (Haiku, Llama, Gemma) confirms the skill works on
> lightweight models. It does not confirm production readiness. Tier 1 validation
> is required for a skill to be marked `stable`.

| Test | Prompt Summary | Result |
|---|---|---|
| Test 1 — Simple | | `[ ] PASS  [ ] FAIL` |
| Test 2 — Ambiguous | | `[ ] PASS  [ ] CONDITIONAL  [ ] FAIL` |
| Test 3 — Edge Case | | `[ ] PASS  [ ] FAIL` |

**Overall result:** `[ ] PASS  [ ] CONDITIONAL (state what would convert to PASS below)`

If CONDITIONAL, explain what converts it to PASS:



---

### Global Defaults Checklist

- [ ] No default language assumed (skill operates in user's language)
- [ ] No default region or jurisdiction assumed (regulatory context from user only)
- [ ] No default infrastructure stack assumed (not AWS, not US-timezone, not high-bandwidth)
- [ ] No default team culture assumed (adapts to context provided)
- [ ] No AI model vendor privileged (platform-agnostic)

---

### License

- [ ] This contribution is submitted under the MIT License
- [ ] I understand this skill belongs to the world and may be used, forked, and built upon by anyone

---

### For Skill Updates Only

If this PR updates an existing skill:

- [ ] Version incremented correctly (MAJOR.MINOR.PATCH — see CONTRIBUTING.md)
- [ ] Evolution registry entry added documenting what changed and why
- [ ] Old evolution entries preserved (lineage must be traceable)
- [ ] Successor Trigger reviewed and updated if needed

---

### Reviewer Notes

Anything the reviewer should know that is not captured above:



---

*By submitting this PR, you confirm that all checked items above are accurate
and that your skill will produce reliable, safe, and globally appropriate output.*
