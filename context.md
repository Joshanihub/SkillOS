# SkillOS — Session Context for AI Coding Tools

Feed this file to any AI coding tool at the start of every automation session.
It prevents re-explaining the project and ensures correct file operations.

```bash
# Claude Code / terminal agent usage
cat context.md | claude "Your task here"

# Codex CLI usage
codex --context "$(cat context.md)" "[your task]"

# OpenCode usage
opencode --system "$(cat context.md)" "[your task]"
```

---

## What This Project Is

**SkillOS** — An open, platform-agnostic AI Skills Operating System.
Not a prompt library. A **standard** for designing, validating, versioning,
and orchestrating specialized AI reasoning systems.

The analogy: what Docker did for containers, SkillOS does for AI agent behavior.

**License:** MIT. Owned by the world. No vendor, region, or company owns it.

---

## Repository Structure

```
skillOS/
├── SKILL-DEFINITION-STANDARD.md   ← The SDS — 13-component governance contract
├── SKILL-CREATOR.md               ← Compiler system prompt — generates skills
├── CONTRIBUTING.md                ← Contribution and governance rules
├── context.md                     ← This file
│
├── registry/
│   ├── tier-0/                    ← Foundational disciplines
│   │   └── software-architect-v1.0.1.md   ← v1.0.1: observability fix
│   ├── tier-1/                    ← Domain specialists
│   │   └── frontend-specialist-v1.0.0.md
│   ├── tier-2/                    ← Technology experts
│   │   └── react-expert-v1.0.0.md
│   ├── tier-3/                    ← Pattern specialists
│   └── tier-4/                    ← Orchestration
│
└── validation/
    └── test-harness.md            ← Standardized tests every skill must pass
```

---

## Current Status (July 2026)

**Version:** v1.1 — Refinement phase complete (92%), Ready for v2.0 launch

**Completed (v1.0):**
- SKILL-DEFINITION-STANDARD.md — 13 components, fully specified
- SKILL-CREATOR.md — 10-phase compiler system prompt
- 3 pilot skills — generated and validated
- validation/test-harness.md — three-test standard
- Validation run: 7/9 PASS, 92% SDS compliance (Haiku graceful degradation test)
- GitHub Actions SDS compliance validator on PRs
- Software Architect v1.0.3: observability fix applied, 13/13 SDS
- Frontend Specialist v1.0.1, React Expert v1.0.1, Security Principles v1.0.0 — stable
- README funding links live
- context.md session file for AI coding tools

**Completed (v1.1 — Refinement):**
✅ Assumption Documentation Template — standardizes ambiguity handling
✅ Cross-Tier Routing Map — documents Tier 0→1→2 handoffs
✅ Testing Strategy Formalization — tier-specific test protocols + quality gates
✅ Phase 1 → Phase 2 Transition Report — readiness assessment for v2.0
✅ Rebuild Security Principles (Tier 0) — 417 lines, 13/13 SDS compliance

**Next (v2.0 — Registry Launch):**
⏳ Generate 3 new Tier 1 skills: Backend Specialist, Database Specialist, DevOps Specialist
⏳ Community infrastructure: GitHub templates, issue templates, good first issues
⏳ Project Rules Engine: documentation + fork examples
⏳ Cross-model validation on pilot skills (Tier 1 models): GPT-5.5, Gemini 3.5 Pro

---

## The SDS Standard — What Every Skill Must Have

Every file in `registry/` must contain all 13 components.
A skill missing any component is INVALID and must not be committed.

```
Component 1  — Skill Metadata (YAML block)
Component 2  — Professional Identity
Component 3  — Knowledge Taxonomy (hierarchical, not flat)
Component 4  — Capability Boundaries (in-scope + out-of-scope + routing table)
Component 5  — Decision Engine (branching logic, not prose)
Component 6  — Constraint Matrix (13 cross-cutting concerns)
Component 7  — Failure Mode Library (minimum 15, domain-specific)
Component 8  — Quality Gate Checklist (universal + domain-specific)
Component 9  — Output Template Library (minimum 4 modes)
Component 10 — Ethical Constraint Layer (universal 3 + domain-specific)
Component 11 — Safety Layer (data minimalism, reversibility, blast radius)
Component 12 — Collaboration Contract (typed YAML I/O)
Component 13 — Validation Record (3 test results required to publish)
```

---

## Tier System

```
Tier 0 → Foundational: Software Architecture, Security, Performance, Systems Thinking
Tier 1 → Domain: Frontend, Backend, DevOps, ML/AI, Database, Cloud, Mobile
Tier 2 → Technology: React, Next.js, TypeScript, Node.js, PostgreSQL, Docker
Tier 3 → Pattern: Auth, Caching, CI/CD, Testing, Real-time, Observability
Tier 4 → Orchestration: Context routing, planning, memory, specialist activation
```

---

## File Naming Convention

```
[skill-name]-v[major].[minor].[patch].md

Examples:
  software-architect-v1.0.0.md
  react-expert-v1.0.0.md
  postgres-specialist-v1.0.0.md
```

---

## Commit Message Convention

```
feat: add [skill-name] to registry (tier-[N])
test: [skill-name] v[version] validation complete
fix: [skill-name] — [what was fixed]
docs: update [file] — [what changed]
ci: add [workflow name]
chore: [maintenance task]
```

---

## Global Rules — Never Violate

These apply to every file in the repository:

1. No skill assumes a default language
2. No skill assumes a default region or jurisdiction
3. No skill assumes a default infrastructure stack
4. No skill is published without all 13 SDS components
5. No skill is published without a completed Validation Record
6. All skills are MIT licensed
7. No vendor, platform, or model is privileged

---

## Key Commands for Automation Tasks

**Initialize repo:**
```bash
git init && git add . && git commit -m "feat: SkillOS v1.0 foundation"
git remote add origin [repo-url] && git push -u origin main
```

**Check SDS compliance (manual):**
Verify each registry file contains all 13 section headers listed above.

**Record validation results:**
Open the skill file, find the `validation_date: pending` block in
Component 13, update result fields to `pass` or `fail` with notes.

**Add a new skill:**
1. Generate via SKILL-CREATOR.md
2. Run three tests from test-harness.md
3. Record results in Component 13
4. Place in correct tier directory
5. Commit: `feat: add [skill-name] to registry (tier-[N])`

---

*context.md · SkillOS v1.0 · MIT License*
