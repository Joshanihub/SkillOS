# SkillOS

### The open standard for AI agent behavior.

---

**SkillOS is an open, platform-agnostic AI Skills Operating System.**

Not a prompt library. Not a chatbot wrapper. Not another agent framework.

A **governance standard** for designing, validating, versioning, orchestrating, and continuously improving specialized AI reasoning systems — built for the world to use, built to outlast any single platform, built to enable real collaboration between AI systems.

---

## The Problem We Solve

**Today's AI is unreliable at scale.**

- Everyone writes AI prompts differently — no shared structure
- Outputs vary wildly between users, sessions, and models
- Domain expertise is inconsistent — sometimes brilliant, sometimes hallucinated
- When specialists are needed, they don't collaborate — they lose context
- There is no shared quality standard — no way to know if you're using a good skill
- There is no open registry — every team rebuilds the wheel
- AI systems lose context between specialists — no handoff protocol

The result: AI is powerful in isolation and unreliable in workflows.

---

## The Vision

What **Git** did for version control.
What **Docker** did for containers.
What **npm** did for package sharing.
What **OpenAPI** did for APIs.

**SkillOS does for AI agent behavior.**

A standard so useful that it becomes infrastructure. Not forced, not mandated — just the obvious way to do things because it works better.

---

## What's Inside v1.0

`
SkillOS/
│
├── SKILL-DEFINITION-STANDARD.md   ← The SDS — 13-component governance contract
├── SKILL-CREATOR.md               ← The compiler — 10-phase generation system
├── CONTRIBUTING.md                ← How to contribute a skill
│
├── registry/
│   ├── tier-0/                    ← Foundational disciplines
│   │   ├── software-architect-v1.0.0.md
│   │   └── [more as contributed]
│   ├── tier-1/                    ← Domain specialists
│   │   ├── frontend-specialist-v1.0.0.md
│   │   └── [more as contributed]
│   ├── tier-2/                    ← Technology experts
│   │   ├── react-expert-v1.0.0.md
│   │   └── [more as contributed]
│   ├── tier-3/                    ← Pattern specialists
│   │   └── [coming in v2.0]
│   └── tier-4/                    ← Orchestration
│       └── [coming in v3.0]
│
└── validation/
    └── test-harness.md            ← Three standardized tests every skill must pass
`

---

## Quick Start (60 seconds)

**1. Generate a skill**
- Open \SKILL-CREATOR.md\
- Copy the system prompt
- Paste into Claude (claude.ai), ChatGPT, Gemini, or any capable AI interface
- Type: \COMPILE SKILL: [your domain]\
- The compiler runs 10 phases and outputs a complete, SDS-compliant skill

**2. Use an existing skill**
- Browse the \egistry/\ folder
- Find the skill you need
- Copy its system prompt into any compatible AI interface
- Start working

**3. Contribute a skill**
- Read \CONTRIBUTING.md\
- Use the Skill Creator to generate your skill (or write manually)
- Run the three validation tests from \alidation/test-harness.md\
- Submit a PR with your skill and its Validation Record
- (Skills missing any SDS component or failing any test are not merged)

---

## The Skill Definition Standard (SDS)

Every skill in this registry conforms to **13 required components**:

| # | Component | Purpose |
|---|---|---|
| 1 | **Skill Metadata** | Machine-readable header for registry indexing |
| 2 | **Professional Identity** | Realistic, credible expertise profile |
| 3 | **Knowledge Taxonomy** | Structured domain knowledge map with evolution registry |
| 4 | **Capability Boundaries** | What it does, what it doesn't, where it routes |
| 5 | **Decision Engine** | Explicit branching reasoning logic |
| 6 | **Constraint Matrix** | Performance, security, ethics, cost — all domains |
| 7 | **Failure Mode Library** | 15+ domain-specific failure modes |
| 8 | **Quality Gate Checklist** | Self-review before every output |
| 9 | **Output Template Library** | Code, review, debug, teach — auto-selected |
| 10 | **Ethical Constraint Layer** | Runs before output generation, not after |
| 11 | **Safety Layer** | Blast radius, reversibility, data minimalism |
| 12 | **Collaboration Contract** | Typed I/O for multi-skill orchestration |
| 13 | **Validation Record** | Three test results proving the skill works |

**A skill missing any component fails validation and is not published.** This isn't gatekeeping — it's the difference between a toy and a production system.

Read the full standard: \SKILL-DEFINITION-STANDARD.md\

---

## Global Principles

Every skill in this registry follows these principles without exception:

**No default language.** Skills operate in whatever language the user initiates in. If you switch languages mid-conversation, the skill follows.

**No default region.** Regulatory and cultural context is derived from what the user provides — never assumed. GDPR, NDPR, Kenya Data Protection Act, PDPA, LGPD, CCPA, PIPEDA, POPIA, HIPAA — all treated as equally valid.

**No default infrastructure.** Not AWS. Not US-timezone deployment. Not English variable names. Not high-bandwidth internet.

**No default team culture.** Communication style adapts to context signals the user provides.

**No privileged AI platform.** The standard works on Claude, OpenAI, Gemini, Mistral, DeepSeek, Llama — any model capable of following complex instructions.

**Ethics is infrastructure.** Not a checkbox at the end. It runs before output generation, in every skill, every time.

---

## The Tier System

Skills are organized by specialization level:

| Tier | Purpose | Examples | Scope |
|---|---|---|---|
| **Tier 0** | Foundational | Software Architecture, Security Principles, Performance Engineering, Systems Thinking | Principles that all other skills inherit from |
| **Tier 1** | Domain Specialists | Frontend, Backend, DevOps, ML/AI, Database, Cloud, Mobile, Security, Data | Broad category expertise |
| **Tier 2** | Technology Experts | React, Next.js, TypeScript, Node.js, PostgreSQL, Docker, Kubernetes, AWS | Specific technology mastery |
| **Tier 3** | Pattern Specialists | Authentication, Caching, CI/CD, Observability, Testing, Real-time Systems | Cross-cutting concerns |
| **Tier 4** | Orchestration | Context Routing, Task Planning, Specialist Activation, Memory Management | Multi-skill coordination |

---

## Validation

Every skill must pass three standardized tests before publishing:

**Test 1: Simple Request**
Does it produce clean, correct output on a well-specified request without overengineering?

**Test 2: Ambiguous Request**
Does it ask one focused clarifying question OR proceed with documented assumptions?

**Test 3: Edge Case / Domain Boundary**
Does it recognize when a request exceeds its expertise and route cleanly?

See \alidation/test-harness.md\ for full testing protocol.

---

## Roadmap

### v1.0 — Foundation (NOW)
- ✅ Skill Definition Standard
- ✅ Skill Creator (compiler)
- ✅ 3 pilot skills (Software Architect, Frontend Specialist, React Expert)
- ✅ Validation harness
- 🔄 Validation tests being run and recorded
- 🔄 Open source launch on GitHub

### v2.0 — Registry (Q3 2025)
- [ ] 20+ skills across all tiers
- [ ] Automated SDS validation on PR
- [ ] Community contribution pipeline
- [ ] Skill versioning & deprecation tracking

### v3.0 — Runtime (Q4 2025)
- [ ] MCP server exposing skills as activatable tools
- [ ] Multi-skill orchestration engine
- [ ] Context handoff protocol between specialists
- [ ] Skill activation / routing logic

### v4.0 — Platform (2026)
- [ ] Web interface for browsing and testing skills
- [ ] Community ratings and reviews
- [ ] Skill versioning dashboard
- [ ] Dependency resolution visualization

### v5.0 — Ecosystem (2026+)
- [ ] Marketplace (open-source core + premium vertical skills)
- [ ] Multi-agent workflow templates
- [ ] Cross-model portability layer
- [ ] Governance DAO model (community ownership)

---

## Contributing

**This project is maintained by the community.** You are invited to contribute.

Read \CONTRIBUTING.md\ for:
- How to generate a skill using the Skill Creator
- How to run validation tests
- Where to place your skill in the tier system
- What gets rejected and why
- How to update existing skills

The short version:
1. Generate or write your skill
2. Run all three validation tests
3. Submit PR with Validation Record
4. Skills that skip the standard are not merged

---

## Models That Work

SkillOS is platform-agnostic. These models are validated by the community:

**Tier 1 — Best for Skill Creator (complex generation):**
- Claude 3.5 Sonnet (Anthropic) — strongest on complex system prompts
- GPT-4o / o3-mini (OpenAI) — excellent reasoning, strong structured output
- Gemini 2.5 Pro (Google) — strong long-context, best multilingual
- Mistral Large (Mistral AI) — strong European language support
- DeepSeek V3 (DeepSeek) — open-weight, exceptional code reasoning

**Tier 2 — Functional for skill use and generation:**
- Llama 3.3+ (Meta) — fully open-source, self-hostable
- Qwen 3 (Alibaba) — strong multilingual, excellent for Asian languages
- Gemma 3 (Google) — lightweight, deployable on consumer hardware

**Community validation:** If you validate a skill on a model not listed, add your findings. The community benefits from knowing which models work for which tasks.

---

## License & Attribution

**MIT License** — because this belongs to everyone.

- Perpetually free
- Perpetually modifiable
- Perpetually reproducible
- Attribution required in all forks
- Lineage must be traceable

---

## Acknowledgment

SkillOS emerged from a multi-assistant collaboration between Claude (Anthropic), ChatGPT (OpenAI), and Gemini (Google), synthesized and built by the community.

The design was influenced by real production engineering patterns across the global software community. No single AI platform, company, or region owns this. That's the point.

---

## Why This Matters

**In 2024**, every AI system was built from scratch.
**In 2025**, we're starting to share components.
**In 2026**, components become composable.
**In 2027**, composable components become infrastructure.

SkillOS is built for 2027. When multi-agent systems are the default. When specialist AI systems need to collaborate. When quality and consistency matter more than novelty.

The best time to build shared standards is before they're needed.

---

## Support & Community

**Funding:**
- [GitHub Sponsors](https://github.com/sponsors) — support maintainers directly
- [Open Collective](https://opencollective.com) — transparent community funding

**Contribute Without Code:**
- Run validation tests, submit results
- Translate skills, add regional guidance
- Report inaccurate or outdated skills
- Write documentation, tutorials, examples

**Questions?**
- Open an issue on GitHub
- Start a discussion in the community forum

---

*SkillOS v1.0 · MIT License · Owned by the world · Built for the agent-first future*
