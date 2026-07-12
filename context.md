# SkillOS Context for Sessions

## Project Overview

**SkillOS** — An open-source, platform-agnostic AI Skills Operating System. MIT licensed. Owned by the world.

A governance standard + compiler system that makes AI agent behavior reproducible, composable, and auditable at scale.

## Current Status

- **Version:** v1.0 (Foundation Complete)
- **Foundation:** 5 core files (SDS, Skill Creator, README, Contributing, Test-Harness)
- **Pilot Skills:** 3 implemented (Software Architect Tier 0, Frontend Specialist Tier 1, React Expert Tier 2)
- **GitHub:** https://github.com/Joshanihub/SkillOS
- **License:** MIT

## Core Concepts

### Skill Definition Standard (SDS)

Every skill MUST contain all 13 components. Missing any = validation failure.

1. **Metadata** — YAML header with versioning, tier, compatibility
2. **Identity** — Professional persona with experience level + confidence calibration
3. **Knowledge Taxonomy** — Hierarchical domain knowledge + evolution registry
4. **Capability Boundaries** — In-scope + out-of-scope with routing table
5. **Decision Engine** — Branching logic for request classification
6. **Constraint Matrix** — Weighted priority map for domain-specific decisions
7. **Failure Mode Library** — 15+ domain-specific failure patterns (not generic)
8. **Quality Gates** — Universal + domain-specific checklist
9. **Output Templates** — 4+ structured modes with defined sections
10. **Ethical Constraint Layer** — 3 universal rules + domain-specific rules
11. **Safety Layer** — 4 universal checks + domain-specific additions
12. **Collaboration Contract** — YAML I/O interface for multi-skill orchestration
13. **Validation Record** — Proof the skill was tested and works

### Skill Creator (10-Phase Compiler)

Deterministic process for generating new skills. Each phase depends on previous output.

1. Domain Cartography → 2. Identity Calibration → 3. Failure Mode Library → 4. Decision Engine → 5. Constraint Matrix → 6. Collaboration Contract → 7. Quality Gates → 8. Output Templates → 9. Ethical Constraints → 10. Validation Pass

**Key rule:** Phases cannot be skipped or reordered.

### Tier System

- **Tier 0:** Foundational (principles all inherit from) — e.g., Software Architect
- **Tier 1:** Domain specialists — e.g., Frontend Specialist, Backend Specialist
- **Tier 2:** Technology experts — e.g., React Expert, TypeScript Expert
- **Tier 3:** Pattern specialists — horizontal patterns (not yet implemented)
- **Tier 4:** Orchestration — multi-skill coordinators (not yet implemented)

### Global-First Architecture

No defaults for:
- Language (en/es/fr/zh/ja equally valid)
- Region or jurisdiction (GDPR, NDPR, Kenya DPA, PDPA, LGPD, CCPA all equally valid)
- Infrastructure (no AWS/GCP/Azure bias)
- Platform (Claude, OpenAI, Gemini, Mistral all supported)

## Key Rules

**For any file in `registry/`:**
- MUST contain all 13 SDS components (validated by GitHub Actions)
- MUST use semantic markdown (no custom formats)
- MUST be named `[skill-name]-v[version].md` (e.g., `react-expert-v1.0.0.md`)
- MUST be in correct tier subdirectory (`tier-0/`, `tier-1/`, etc.)
- MUST pass 3-test validation (Simple, Ambiguous, Edge Case)

**For commits:**
- Use conventional commit format: `feat:`, `test:`, `docs:`, `ci:`, etc.
- Example: `feat: add database-specialist skill` or `test: software-architect v1.0.0 validation complete`

## File Structure

```
SkillOS/
├── SKILL-DEFINITION-STANDARD.md    # The governance law
├── SKILL-CREATOR.md                # The 10-phase compiler
├── README.md                        # Project front door
├── CONTRIBUTING.md                 # How to contribute
├── test-harness.md                 # 3-test validation protocol
├── LICENSE                         # MIT
├── .gitignore                      # Markdown project ignores
├── context.md                      # This file
├── .github/
│   └── workflows/
│       └── validate-sds.yml        # Automated SDS compliance checker
└── registry/
    ├── tier-0/
    │   └── software-architect-v1.0.0.md
    ├── tier-1/
    │   ├── frontend-specialist-v1.0.0.md
    │   ├── backend-specialist-v1.0.0.md (future)
    │   └── ...
    ├── tier-2/
    │   ├── react-expert-v1.0.0.md
    │   ├── typescript-expert-v1.0.0.md (future)
    │   └── ...
    ├── tier-3/
    │   └── (reserved for pattern specialists)
    └── tier-4/
        └── (reserved for orchestration)
```

## How to Use This File

- **Start of new session:** Feed this to Claude before explaining the project
- **Before adding skills:** Review SDS components and tier system
- **Before submitting PR:** Ensure your skill has all 13 components
- **Before building features:** Refer to global-first rules

## Immediate Next Steps (v1.0 completion)

1. **Manual validation tests** — Run 3 tests per skill, record results
2. **Record results** — Update Validation Record sections in each skill
3. **GitHub Actions** — SDS compliance checker ready (automated)
4. **Community ready** — v1.0 finalized

## Contact & License

- **License:** MIT
- **Repository:** https://github.com/Joshanihub/SkillOS
- **Owned by:** The world (no vendor lock-in)

---

*Last updated: 2026-07-12 · Version: v1.0 Foundation*
