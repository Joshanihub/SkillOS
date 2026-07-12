# SkillOS

### The open standard for AI agent behavior.

---

SkillOS is an open, platform-agnostic AI Skills Operating System.

Not a prompt library. Not a chatbot wrapper. Not another agent framework.

A **standard** for designing, validating, versioning, orchestrating, and
continuously improving specialized AI reasoning systems — built for the
world to use, built to outlast any single platform, owned by no one.

---

## The Problem

Everyone writes AI prompts differently.
No standardized structure exists.
Outputs vary wildly between users and sessions.
Domain expertise is inconsistent.
Skills cannot collaborate with each other.
There is no shared quality standard.
There is no open skill registry.
AI systems lose context between specialists.
Nobody has open-sourced the standard.

The result: AI is powerful in isolation and unreliable at scale.

---

## The Vision

What Git did for version control.
What Docker did for containers.
What npm did for package sharing.
What OpenAPI did for APIs.
What Kubernetes did for orchestration.

**SkillOS does for AI agent behavior.**

The real asset is not the skills themselves.
The real asset is the compiler behind them — a standard so rigorous
that generating skill #100 costs the same effort as generating skill #1.

---

## Founding Principle

This library belongs to everyone.

It was built for the world to use, improve, and build upon.
No single company, region, team, language, or AI platform owns it.
Contributions from every timezone, every language, every technical
context are not just welcome — they are the point.

Every skill carries this principle. No skill in this registry assumes
a default language, a default region, a default jurisdiction, or a
default infrastructure stack. Ever.

**License:** MIT — the most permissive open-source license available,
because this belongs to the world.

---

## What's Inside

```
skillOS/
│
├── SKILL-DEFINITION-STANDARD.md   ← The SDS — the governance contract
├── SKILL-CREATOR.md               ← The compiler — generates SDS-compliant skills
├── CONTRIBUTING.md                ← How to contribute a skill
├── context.md                     ← Feed this to your AI coding tool each session
│
├── registry/
│   ├── tier-0/                    ← Foundational disciplines
│   │   └── software-architect-v1.0.0.md
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

## Architecture

SkillOS is built in three layers. They are independent and can be
adopted incrementally.

**Layer 1 — Skill Registry** *(live now)*
GitHub-hosted, MIT licensed, community-contributed. Versioned skill
definitions conforming to the SDS. Works on any AI interface today.

**Layer 2 — Skill Runtime** *(v3.0 roadmap)*
A Model Context Protocol (MCP) server that exposes skills as activatable
tools. Users connect once and get access to the entire registry —
composable, versioned, callable by name. MCP is an open standard supported
natively by Claude and a growing number of AI interfaces. This is buildable
today and is the technology that turns the registry into a connectable
application.

**Layer 3 — Skill Marketplace** *(v5.0 roadmap)*
A web interface for browsing, testing, forking, and contributing skills.
Think npm but for AI agent behaviors. Community ratings, premium vertical
skills for regulated industries, enterprise packs with compliance templates.

---

## Quick Start

**Use an existing skill:**
1. Browse the `registry/` folder
2. Copy the skill's system prompt into any compatible AI interface
3. Start working — no setup, no account, no vendor lock-in

**Generate a new skill:**
1. Open `SKILL-CREATOR.md`
2. Copy the system prompt into any capable AI interface
3. Type: `COMPILE SKILL: [your domain]`
4. The compiler runs 10 phases and outputs a complete, SDS-compliant skill

**Contribute a skill:**
1. Read `CONTRIBUTING.md`
2. Use the Skill Creator to generate your skill
3. Run all three validation tests from `validation/test-harness.md`
4. Submit a PR with your skill and its completed Validation Record

---

## The Skill Definition Standard (SDS)

Every skill in this registry conforms to 13 required components.
A skill missing any component fails validation and is not published.

| # | Component | Purpose |
|---|---|---|
| 1 | Skill Metadata | Machine-readable header for registry indexing and dependency resolution |
| 2 | Professional Identity | Realistic, credible expertise profile with confidence calibration |
| 3 | Knowledge Taxonomy | Hierarchical domain knowledge map with evolution state per concept |
| 4 | Capability Boundaries | Explicit in-scope and out-of-scope with clean routing table |
| 5 | Decision Engine | Branching logic — not prose. Ambiguity protocol and mode selection |
| 6 | Constraint Matrix | 13 cross-cutting concerns mapped to domain-specific weights |
| 7 | Failure Mode Library | 15+ real, domain-specific failure modes — not generic engineering advice |
| 8 | Quality Gate Checklist | Self-review the skill runs on its own output before delivering |
| 9 | Output Template Library | Code, review, debug, teach — auto-selected based on request type |
| 10 | Ethical Constraint Layer | Runs before output generation, not after. Domain-specific rules required |
| 11 | Safety Layer | Blast radius, reversibility, data minimalism, downstream impact |
| 12 | Collaboration Contract | Typed I/O interface for multi-skill orchestration |
| 13 | Validation Record | Three test results required before a skill can be published |

---

## Skill Tier System

Skills are organized in a dependency hierarchy that enables orchestration.

| Tier | Purpose | Examples |
|---|---|---|
| Tier 0 | Foundational disciplines — all skills inherit from these | Software Architecture, Systems Thinking, Security, Performance |
| Tier 1 | Domain specialists | Frontend, Backend, DevOps, ML/AI, Database, Cloud, Mobile |
| Tier 2 | Technology experts | React, Next.js, TypeScript, Node.js, PostgreSQL, Docker |
| Tier 3 | Pattern specialists | Auth, Caching, CI/CD, Observability, Testing, Real-time |
| Tier 4 | Orchestration | Context routing, task planning, specialist activation, memory management |

---

## How Skills Collaborate

Skills are not isolated. They pass typed context to each other.

```
Example: Building a new SaaS product

Software Architect (Tier 0)
  → Outputs: architecture decision, module boundaries,
    data ownership map, API contract shapes

Frontend Specialist (Tier 1) receives architect output
  → Outputs: component hierarchy, state architecture,
    rendering strategy, API requirements

React Expert (Tier 2) receives frontend specialist output
  → Outputs: production component code, hook patterns,
    performance optimization, test cases

Each specialist works within its domain.
Each handoff is a typed contract, not a vague summary.
```

---

## Global Principles

**No default language.**
Skills operate in whatever language the user initiates in.
If the user switches language mid-conversation, the skill follows.

**No default region.**
Regulatory and cultural context is derived from user-provided information —
never assumed. All of the following are treated as equally valid:
GDPR (EU) · NDPR (Nigeria) · Kenya Data Protection Act ·
PDPA (Singapore, Thailand) · LGPD (Brazil) · CCPA (California) ·
PIPEDA (Canada) · POPIA (South Africa) · HIPAA (US Healthcare) ·
SOC 2 · ISO 27001 · EU AI Act · and regional equivalents.

**No default infrastructure.**
Not AWS. Not US-timezone deployment. Not high-bandwidth internet.
Not English-language variable names.

**No default team culture.**
A Japanese engineering team values explicit consensus documentation.
A US startup values speed and iteration.
A German enterprise values formal specification.
Skills adapt to the context provided, not to cultural assumptions.

**No default AI platform.**
No model vendor is privileged. The standard works on any model
capable of following complex instructions.

**Ethics is infrastructure.**
It runs before output generation, not as a final checkbox.
Every skill has domain-specific ethical constraints, not just the
universal three rules. A marketing skill's ethics differ from a
security skill's ethics.

**Safety is distinct from security.**
Security: auth, encryption, injection prevention.
Safety: data minimalism, reversibility awareness, blast radius,
downstream impact on real people who are not in the conversation.

---

## Recommended Models

SkillOS favors no vendor. These are the models the community has
validated as capable of producing reliable skill output as of July 2026.
The list is maintained by contributors — add your findings to the registry.

The most important insight from 2026 benchmarks: **there is no single
best model — only the best model for a given job.**

**Frontier — Skill Creator (complex multi-phase generation):**

| Model | Provider | Strength | Best For |
|---|---|---|---|
| Claude Fable 5 | Anthropic | SWE-Bench Pro leader (80.3%); strongest on long-horizon agentic coding | Skill generation, code-heavy skills |
| Claude Opus 4.8 | Anthropic | Overall Intelligence Index leader (61.4); best coding reliability | Production skill use, agentic workflows |
| GPT-5.5 | OpenAI | Best all-rounder; leads ARC-AGI-2 reasoning (85.0%); largest ecosystem | General skill generation, writing-heavy skills |
| Gemini 3.1 Pro / 3.5 Pro | Google | Leads GPQA Diamond reasoning (94.3%); 2M token context window | Research skills, multilingual, document-heavy |
| Grok 4.3 | xAI | Competitive benchmarks; real-time web/social context | Skills needing live data |
| Mistral Large | Mistral AI | Strong European regulatory coverage; open-weight option | GDPR-context skills, self-hosted deployments |

**Strong value — functional for both generation and use:**

| Model | Provider | Notes |
|---|---|---|
| Claude Sonnet 5 | Anthropic | Near-Opus intelligence at Sonnet cost; best daily-driver |
| GPT-5 mini | OpenAI | High-volume tasks at low cost |
| Gemini 3.5 Flash | Google | Cheapest capable option at $1.50/$9 per MTok |
| DeepSeek V4 | DeepSeek | Open-weight; exceptional code reasoning; cheapest frontier-class |
| Kimi K2 | Moonshot AI | 99.1% AIME; best quality-per-dollar in reasoning |

**Open-source / self-hostable (privacy-sensitive deployments):**

| Model | Provider | Notes |
|---|---|---|
| Llama 4 | Meta | Fully open; strong for regulated environments needing self-hosting |
| Qwen 2.5 / 3 | Alibaba | Outstanding multilingual; best for Asian-language deployments |
| DeepSeek R1 | DeepSeek | MIT license; self-hostable; near-frontier reasoning |
| Gemma 3 | Google | Lightweight; deployable on consumer hardware |

**Community note:** If you validate a skill on a model not listed here,
add your findings to the skill's Validation Record. Add a row to this
table via PR. The community benefits from knowing which models produce
reliable output for which skill types.

---

## Recommended Build Tools

Different phases of SkillOS development call for different tools.
No single tool owns all phases.

**Codex CLI (OpenAI) — Use from v1.0 through v2.0**
Terminal-native coding agent powered by o4-mini and GPT-5 variants.
Open-source. Lives entirely in your shell. Reads and writes files,
executes sandboxed shell commands, handles Git operations natively.

Use Codex for:
- Initializing the GitHub repo and directory structure
- Automating validation test recording into Markdown files
- Writing GitHub Actions workflows for SDS compliance checking on PRs
- Any CI/CD, registry automation, or file-manipulation task
- Scripted batch operations across multiple skill files

**Google Antigravity — Use from v4.0 onward**
Agent-first IDE (VS Code fork) with parallel orchestration of up to
five autonomous AI agents via the Manager View. Built-in Chrome browser
lets agents spin up localhost, interact with UI elements, and visually
verify changes before presenting a diff.

Use Antigravity for:
- Building the web platform for browsing and testing skills (v4.0)
- Parallel agent workflows: one agent refining the skill browser UI
  while another visually verifies component output in Chrome
- Full-stack feature development once the platform layer exists
- Any task where visual verification and parallel orchestration matter

**Decision rule:** If the task is terminal-native (files, Git, CI),
use Codex CLI. If the task is visual and benefits from parallel agents
and a browser, use Antigravity. Before v4.0, Codex CLI handles
everything. Antigravity before that point is overkill.

---

## Ambiguity Resolution Protocol

Every skill in the registry uses this exact decision rule.
No skill blocks indefinitely waiting for perfect information.

```
Request completeness ≥ 80%  → Proceed. Document assumptions inline.
Request completeness 50–79% → Ask ONE focused clarifying question. Then proceed.
Request completeness < 50%  → Ask maximum THREE questions. Then proceed.
NEVER                       → Block indefinitely waiting for perfect information.
```

---

## Roadmap

**v1.0 — Foundation** *(current)*
- [x] Skill Definition Standard (13 components)
- [x] Skill Creator compiler (10-phase generation)
- [x] 3 pilot skills: Software Architect, Frontend Specialist, React Expert
- [x] Validation test harness
- [ ] Validation tests run and recorded on pilot skills
- [ ] GitHub repo launch

**v2.0 — Registry**
- [ ] 20+ skills across all tiers
- [ ] Community contribution pipeline
- [ ] GitHub Actions: automated SDS compliance check on every PR
- [ ] `context.md` session file for AI coding tools

**v3.0 — Runtime**
- [ ] MCP server exposing skills as activatable tools
- [ ] Multi-skill orchestration with typed context handoffs
- [ ] Context handoff protocol between specialists
- [ ] Skills callable by name from any MCP-compatible interface

**v4.0 — Platform** *(Antigravity phase begins here)*
- [ ] Web interface for browsing, searching, and testing skills
- [ ] Community ratings and reviews
- [ ] Skill versioning dashboard
- [ ] Visual skill composition tool

**v5.0 — Ecosystem**
- [ ] Marketplace: open-source core + premium vertical skills
  (HIPAA-aware medical skills, GDPR-compliant data skills, etc.)
- [ ] Multi-agent workflow templates
- [ ] Cross-model portability annotation system
- [ ] Compiler extended to generate agents, MCP servers, evaluation
  suites, and multi-agent team templates from the same SDS standard

---

## Contributing

Read `CONTRIBUTING.md` before submitting.

**The quality bar:** Would a senior engineer in this domain look at this
skill and trust it to represent their field accurately? If not — revise.

**What gets merged:**
- All 13 SDS components present and complete
- Validation Record showing all three tests passed
- MIT license
- No default language, region, or infrastructure assumed
- Domain-specific failure modes (not generic engineering advice)
- Domain-specific ethical constraints (beyond the universal three)

**What gets rejected:** anything that skips the standard.

Every contributor is a maintainer of the world's shared AI infrastructure.

---

## Supporting the Project

SkillOS is community-maintained and free forever. If it saves you time,
helps your team, or advances a project you care about — consider supporting it.

**Fund the project:**
- [GitHub Sponsors](https://github.com/sponsors) — support individual
  maintainers directly; appears on contributor profiles
- [Open Collective](https://opencollective.com) — transparent community
  fund where all income and spending is publicly visible; preferred for
  community infrastructure costs (hosting, CI, domain)

**Why funding matters:**
This project has real operational constraints. Validation testing across
multiple AI models has a cost. CI infrastructure has a cost. The people
who maintain the standard and review contributions deserve support.
Funding doesn't change who owns the project — the world still owns it.
It changes whether the people maintaining it can sustain that work.

**Contribute without code or money:**
- Run validation tests on existing skills and submit the results
- Add regional regulatory guidance not yet covered in the Constraint Matrix
- Translate skills or README content into other languages
- Report skills that produce incorrect or outdated output
- Write tutorials, examples, or integration guides
- Share the project — awareness is its own contribution

**Compute contributions:**
If you have access to compute you can share for multi-model validation
testing, open an issue on GitHub with the label `compute-offer`.

---

## License

MIT — because this belongs to everyone.

Attribution is required in forks. Not for ownership — for traceability.
When a skill gets forked and modified, knowing its lineage helps
future contributors understand what changed and why.

---

## Acknowledgment

SkillOS emerged from a multi-assistant collaboration between Claude
(Anthropic), ChatGPT / Mira (OpenAI), and Gemini (Google), synthesized
and built by Joshua Mwangangi and the SkillOS community.

The design was influenced by real production engineering patterns from
across the global software engineering community — not from any single
company, region, or team.

No single assistant, company, or region owns this. That's the point.

---

*SkillOS v1.0 · MIT License · Built for the world*
