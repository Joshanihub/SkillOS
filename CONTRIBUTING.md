# Contributing to SkillOS

Thank you for contributing. Every skill you add becomes part of the world's shared AI infrastructure.

---

## Before You Start

**Read the \SKILL-DEFINITION-STANDARD.md\ completely.** Every skill must conform to all 13 SDS components. There are no exceptions. 

Why? Because incomplete skills produce unreliable output, and unreliable output is the problem this project exists to solve.

---

## How to Contribute a Skill

### Step 1 — Generate

Use the **Skill Creator** to generate your skill.

**If using Claude (recommended):**
1. Open \SKILL-CREATOR.md\
2. Create a new Claude Project at claude.ai
3. Project Settings → System Prompt → Paste the system prompt
4. Type: \COMPILE SKILL: [your domain]\
5. Wait for the 10-phase compilation to complete

**If using ChatGPT, Gemini, or other compatible AI:**
1. Create a new custom GPT / Gem / assistant
2. Paste the system prompt from \SKILL-CREATOR.md\
3. Type: \COMPILE SKILL: [your domain]\
4. Wait for output

**If writing manually:**
You can write the skill directly, but every component must still be present and complete. This is harder than using the Skill Creator — you're responsible for all 13 components meeting the standard's requirements.

### Step 2 — Validate

Run **all three validation tests** from \alidation/test-harness.md\ against your generated skill.

**For each test:**
1. Copy the test prompt
2. Paste it into the skill (same interface you generated the skill in)
3. Evaluate the response against the pass criteria
4. Record: pass | fail + observations

**A skill failing any test must be revised before submission.** Do not submit incomplete work. The review process will catch it, but you save everyone time by validating first.

**SDS Compliance Checklist:**
Run through every checkbox in the test-harness before submitting:
- [ ] All 13 components present
- [ ] Skill Metadata complete in YAML format
- [ ] Professional Identity includes confidence calibration
- [ ] Knowledge Taxonomy includes Evolution Registry
- [ ] Capability Boundaries have explicit routing table
- [ ] Failure Mode Library has 15+ domain-specific entries
- [ ] Quality Gates include universal + domain-specific
- [ ] Output Templates have 4+ modes
- [ ] Ethical Constraints include domain-specific rules
- [ ] Collaboration Contract is typed (YAML format)
- [ ] No language assumed as default
- [ ] No region or infrastructure assumed as default
- [ ] License is MIT

### Step 3 — Place

Put your skill in the correct tier directory:

\\\
registry/tier-0/   ← Foundational (Architecture, Security, Performance, Systems)
registry/tier-1/   ← Domain (Frontend, Backend, DevOps, ML, Database, Cloud, Mobile)
registry/tier-2/   ← Technology (React, TypeScript, PostgreSQL, Docker, Kubernetes)
registry/tier-3/   ← Pattern (Auth, Caching, Testing, Observability, etc.)
registry/tier-4/   ← Orchestration (Routing, Planning, Memory, Context)
\\\

**Naming convention:** \[skill_name]-v[version].md\

Examples:
- \eact-specialist-v1.0.0.md\
- \postgresql-expert-v2.1.0.md\
- \uthentication-pattern-v1.0.0.md\

Uncertain about tier? Look at the Tier System section in README.md or ask in your PR.

### Step 4 — Submit

Open a PR (Pull Request) with:

1. Your skill file in the correct \egistry/tier-X/\ directory
2. A completed Validation Record (Component 13) showing all three tests passed
3. A one-paragraph description of what problem this skill solves

**PR Template:**
\\\
## Skill Contribution: [Skill Name]

**Domain:** [Primary domain]
**Tier:** [Tier number]
**Problem Solved:**
[One paragraph describing the value and use case]

**Tests:**
- [ ] Test 1 (Simple): pass
- [ ] Test 2 (Ambiguous): pass
- [ ] Test 3 (Edge Case): pass

**SDS Compliance:** All 13 components present
\\\

---

## What Gets Rejected

Skills are rejected if they:

- ❌ Are missing any of the 13 SDS components
- ❌ Fail any of the three validation tests
- ❌ Assume a default language, region, or infrastructure
- ❌ Use a proprietary license (must be MIT)
- ❌ Have vague capability boundaries
- ❌ Have generic failure modes (not domain-specific)
- ❌ Recommend deprecated practices as current best practice
- ❌ Were generated without the Skill Creator or equivalent rigor
- ❌ Have ethical constraints that are only the universal three (need domain-specific rules)

**What to do if your PR is rejected:**
1. Read the reviewer comments carefully
2. Fix the issues (usually: add missing components, run validation tests, add domain-specific constraints)
3. Re-submit

Rejection is not personal — it's the standard protecting itself.

---

## Updating an Existing Skill

Use the **Skill Creator's update command:**

Type: \UPDATE SKILL:\ [paste the skill] \REASON:\ [why it needs updating]

**Version increments (Semantic Versioning):**
- **MAJOR** (1.0.0 → 2.0.0): Breaking change to skill behavior or output contract
- **MINOR** (1.0.0 → 1.1.0): New capability added, backward compatible
- **PATCH** (1.0.0 → 1.0.1): Bug fix, clarification, minor improvement

**In your PR:**
1. Update the skill file with new version number
2. Add entry to the evolution registry (Component 3) documenting what changed
3. Include the Validation Record for the new version
4. Do NOT delete old evolution entries — lineage must be traceable

---

## Deprecating a Skill

Deprecated skills are **never deleted.** This preserves lineage.

To deprecate:
1. Change status in Skill Metadata to: \status: deprecated\
2. Set \successor_skill\ pointing to the replacement
3. Add a clear deprecation notice in the skill header
4. Keep the skill in the registry with full history

Example:
\\\yaml
status: deprecated
successor_skill: react-specialist-v2-hooks-first
deprecation_reason: "React Hooks are now the standard; class components are legacy"
deprecation_date: 2025-07-15
\\\

---

## Quality Bar

**The question to ask before submitting:** Would a senior engineer in this domain look at this skill and trust it to represent their field accurately?

If not — revise. The bar is high because the use is real.

---

## Language & Regionalization

**If contributing a skill in a language other than English:**
It is welcomed without reservation. The registry is explicitly multilingual.

Update the Skill Metadata:
\\\yaml
languages: [es, pt, fr]  # Spanish, Portuguese, French
\\\

---

**If contributing domain-specific regulatory guidance for a region not currently covered:**
NDPR, Kenya Data Protection Act, PDPA, regional equivalents — these contributions are especially valuable. They fill real gaps.

The project is better with your region represented.

---

## Code of Conduct

**One foundational rule:** This project belongs to everyone.

- No contributor, company, or region has authority over what is or isn't included based on origin
- Contributions are evaluated on quality against the SDS — nothing else
- Diversity of origin is a feature, not a bug
- Every voice is equally weighted

---

## Getting Help

- **Questions about the SDS?** Open an issue labeled \question\
- **Need feedback before submitting?** Open a draft PR with your skill
- **Unsure about tier placement?** Ask in an issue or draft PR
- **Want to contribute but don't know what?** Look for issues labeled \good first issue\

---

## Recognition

Every contributor is named in the skill's metadata and in this project's hall of fame.

Your contribution endures. Future versions of your skill carry your name.

---

*CONTRIBUTING.md · SkillOS v1.0 · MIT License · Owned by the world*
