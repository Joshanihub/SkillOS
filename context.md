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
├── SKILL-DEFINITION-STANDARD.md   → The SDS — 13-component governance contract
├── SKILL-CREATOR.md               → Compiler system prompt — generates skills
├── CONTRIBUTING.md                → Contribution and governance rules
├── CHANGELOG.md                   → Permanent version history
├── context.md                     → This file
│
├── registry/
│   ├── tier-0/                    → Foundational disciplines
│   │   ├── software-architect-v1.0.3.md
│   │   ├── security-principles-v1.0.0.md
│   │   └── systems-thinking-v1.0.0.md
│   ├── tier-1/                    → Domain specialists
│   │   ├── frontend-specialist-v1.0.1.md
│   │   ├── backend-specialist-v1.0.0.md
│   │   ├── database-specialist-v1.0.0.md
│   │   ├── devops-specialist-v1.0.0.md
│   │   └── ml-ai-specialist-v1.0.0.md
│   ├── tier-2/                    → Technology experts
│   │   ├── react-expert-v1.0.1.md
│   │   └── typescript-specialist-v1.0.0.md
│   ├── tier-3/                    → Pattern specialists
│   └── tier-4/                    → Orchestration
│
├── docs/
│   ├── ASSUMPTION-TEMPLATE.md
│   ├── CROSS-TIER-ROUTING-MAP.md
│   ├── TESTING-STRATEGY.md
│   ├── WORKFLOW-EXAMPLES.md
│   └── INDUSTRY-VERTICALS.md
│
└── .github/
    ├── PULL_REQUEST_TEMPLATE.md
    ├── ISSUE_TEMPLATE/
    │   ├── bug_report.yml
    │   ├── new_skill_proposal.yml
    │   ├── skill_improvement.yml
    │   └── config.yml
    └── workflows/
        └── validate-sds.yml
```

---

## Current Status (July 2026)

**Version:** v2.0-beta — Phase 2 (Registry) in progress

**Phase 1 — Complete (v1.1):**
- SKILL-DEFINITION-STANDARD.md — 13 components, fully specified
- SKILL-CREATOR.md — 10-phase compiler system prompt
- GitHub Actions SDS compliance validator on PRs
- README funding links live
- docs/ASSUMPTION-TEMPLATE.md, CROSS-TIER-ROUTING-MAP.md, TESTING-STRATEGY.md
- Software Architect v1.0.3, Frontend Specialist v1.0.1, React Expert v1.0.1 — validated, stable
- Security Principles v1.0.0, Backend Specialist v1.0.0, Database Specialist v1.0.0, DevOps Specialist v1.0.0 — rebuilt to full SDS v1.1, 3/3 PASS each

**Phase 2 — In Progress (v2.0-beta):**
✓ Phase 2.2 Community Infrastructure complete:
  - .github/PULL_REQUEST_TEMPLATE.md (13-component gate)
  - .github/ISSUE_TEMPLATE/ (4 templates: bug, proposal, improvement, config)
  - docs/WORKFLOW-EXAMPLES.md, docs/INDUSTRY-VERTICALS.md
✓ Phase 2.1 New Skills — 10-skill threshold reached:
  - Systems Thinking v1.0.0 (Tier 0) — compiled, 13/13 SDS
  - ML/AI Specialist v1.0.0 (Tier 1) — compiled, 13/13 SDS
  - TypeScript Specialist v1.0.0 (Tier 2) — compiled, 13/13 SDS

**Next (Phase 2.3 — Announcement):**
▢ Enable GitHub Discussions (manual — GitHub Settings)
▢ Add repo topics: ai, agents, mcp, prompt-engineering, open-source, skill-registry
▢ Mobile Specialist (Tier 1) — remaining Tier 1 skill before announcement
▢ Write and publish launch post

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
