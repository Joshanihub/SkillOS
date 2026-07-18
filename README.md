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

## What SkillOS Is

SkillOS is the missing execution layer between humans, AI models, tools, workflows,
and autonomous agents. It standardizes how AI systems interact with human knowledge
the same way operating systems standardized how software interacts with hardware.

**Knowledge tells AI what exists.**
**Skills teach AI how to execute.**
**Agents determine who performs the work.**
**Models provide the intelligence.**
**SkillOS orchestrates everything.**

---

## The Eight-Layer Architecture

SkillOS is built as eight connected layers. Each layer is independently useful
and progressively enables more powerful AI-assisted work.

```
┌─────────────────────────────────────────────────────────┐
│  JUDGMENT LAYER    Business context · Risk · Approvals  │
├─────────────────────────────────────────────────────────┤
│  MEMORY LAYER      Project knowledge · Agent context    │
├─────────────────────────────────────────────────────────┤
│  AGENT LAYER       Multi-agent coordination             │
├─────────────────────────────────────────────────────────┤
│  WORKFLOW LAYER    Skills chained into full pipelines   │
├─────────────────────────────────────────────────────────┤
│  SKILL LAYER  ←    SDS · Skill Creator · Registry       │
│  LIVE NOW          The foundation everything builds on  │
├─────────────────────────────────────────────────────────┤
│  TOOL LAYER        MCP servers · APIs · IDEs · Cloud    │
├─────────────────────────────────────────────────────────┤
│  VALIDATION LAYER  Continuous quality evaluation        │
├─────────────────────────────────────────────────────────┤
│  MODEL LAYER       Model-agnostic execution marketplace │
└─────────────────────────────────────────────────────────┘
```

**Build once. Execute anywhere. Improve continuously.**
**Own the workflow — not the model.**

---

## Platform Components

**Skill Layer** — What's live now. Reusable AI skills containing instructions,
workflows, reasoning patterns, validation criteria, templates, and execution metadata.
Any domain: software architecture, UI design, medical documentation, financial analysis,
legal review, marketing, research, data engineering, cybersecurity, and more.

**Workflow Layer** — Skills chained into complete production pipelines.
Research → Plan → Design → Build → Test → Deploy → Monitor.
Rather than isolated prompts, SkillOS executes complete workflows.

**Agent Layer** — Multiple AI agents collaborating using skills.
Architect, Engineer, Designer, Researcher, Reviewer, Tester, Security Auditor,
Product Manager, Technical Writer — each specializing while SkillOS coordinates.

**Model Layer** — Completely model-agnostic. Generate with Claude. Review with GPT.
Optimize with Gemini. Verify with open-source. Skills outlive models.

**Tool Layer** — Skills invoke external capabilities through MCP servers, APIs,
databases, IDEs, browsers, cloud providers, GitHub, Figma, Notion, Slack,
Google Workspace, Microsoft 365, and enterprise systems.

**Validation Layer** — Execution quality continuously evaluated: correctness,
completeness, security, performance, consistency, compliance, user satisfaction.
Skills improve through measurable feedback rather than prompt tweaking.

**Memory Layer** — Projects maintain persistent knowledge. Skills maintain execution
methodology. Agents maintain working context. Enables long-running autonomous work
with human oversight.

**Judgment Layer** — The distinction between "technically correct" and "production ready."
Incorporates business context, user intent, domain expertise, risk analysis, ethics,
scalability, and operational constraints. AI produces possibilities — Judgment
determines what should actually be shipped.

**Project Rules** — A project's constitution. Every project has configurable standards
every skill and agent must follow: coding standards, architecture principles, naming
conventions, testing requirements, security policies, design systems, compliance rules.
Auto-generated from project type with full manual override.

**Agent as a Service (AaaS)** — Organizations assemble AI workforces using skills.
Agent teams plan, research, design, develop, review, deploy, operate, monitor, and improve.
Humans handle strategy, approvals, and high-impact decisions.

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
Skills adapt communication style to the context provided.

**No default AI platform.**
No model vendor is privileged. The standard works on any model
capable of following complex instructions.

**Ethics is infrastructure.**
It runs before output generation, not as a final checkbox.

**Safety is distinct from security.**
Security: auth, encryption, injection prevention.
Safety: data minimalism, reversibility, blast radius,
downstream impact on real people not in the conversation.

---

## Recommended Models (July 2026)

SkillOS favors no vendor. These are community-validated recommendations.
The 2026 landscape has no single best model — only the best model for
a given job. This table is maintained by contributors; update via PR.

**Tier 1 — Skill Creator (complex multi-phase generation):**

| Model | Provider | Strength | Best For |
|---|---|---|---|
| Claude Fable 5 | Anthropic | SWE-Bench Pro leader (80.3%); best long-horizon agentic coding | Code-heavy skills, agentic workflows |
| Claude Opus 4.8 | Anthropic | Intelligence Index leader (61.4); most reliable on complex prompts | Production skill use, highest precision |
| GPT-5.5 | OpenAI | Best all-rounder; leads ARC-AGI-2 reasoning (85.0%) | General skill generation, writing-heavy skills |
| Gemini 3.1 / 3.5 Pro | Google | Leads GPQA Diamond (94.3%); 2M token context | Research skills, multilingual, document-heavy |
| Grok 4.3 | xAI | Competitive benchmarks; real-time web/social context | Skills needing live data |
| Mistral Large | Mistral AI | Strong EU regulatory coverage; open-weight option | GDPR-context skills, self-hosted deployments |
| DeepSeek V4 | DeepSeek | Open-weight; near-frontier code reasoning; cheapest self-hosted | Cost-sensitive or privacy-first deployments |

**Tier 2 — Strong value (generation and daily use):**

| Model | Provider | Notes |
|---|---|---|
| Claude Sonnet 5 | Anthropic | Near-Opus intelligence at Sonnet cost; best daily driver |
| GPT-5.5 mini / GPT-5.6 Sol | OpenAI | High-volume tasks; GPT-5.6 now powers OpenAI Codex |
| Gemini 3.5 Flash | Google | Default in Antigravity 2.0; ~289 tokens/sec; cheapest capable frontier |
| Kimi K2 | Moonshot AI | Best quality-per-dollar in reasoning tasks |

**Tier 3 — Skill consumption (degraded on Skill Creator generation):**
Llama 4, Qwen 3, Gemma 3, smaller Mistral variants, Claude Haiku 4.5.
Generated skills run on these — useful for graceful degradation testing
and resource-constrained environments. Use Tier 1 or 2 for generating skills.

**Validation note:** Cross-model testing is strongly encouraged. If you validate
a skill on any model, add results to the skill's Validation Record.
Tier 3 validation confirms graceful degradation. Tier 1 validation confirms
production readiness. Skills should ideally be tested on both.

---

## Recommended Build Tools (July 2026)

The AI coding tool landscape has four distinct categories in 2026.
SkillOS work spans multiple categories depending on the phase.
No single tool owns everything — use the right tool for the task.

---

### Category 1 — Terminal Agents
*Best for SkillOS registry work: file operations, Git, CI/CD, automation.*

| Tool | Provider | Access | Best For |
|---|---|---|---|
| **Claude Code** | Anthropic | CLI · Desktop · IDE extension | Best overall reasoning; repo context; MCP-native; scripts and automation |
| **OpenAI Codex** | OpenAI | CLI · Desktop App · IDE extension | Open-source CLI; GPT-5.6 powered; parallel cloud agents; ChatGPT ecosystem |
| **OpenCode** | Community | CLI | Open-source; model-agnostic; use any API; no vendor lock-in |
| **Aider** | Community | CLI | Lightweight; Git-native commits; excellent for focused file edits |
| **Gemini CLI / Antigravity CLI** | Google | CLI | New Go-based CLI replacing Gemini CLI; fast; Gemini 3.5 Flash powered |

**For SkillOS through v2.0:** Any terminal agent works. Claude Code is strongest
on complex reasoning; Codex CLI/Desktop is best if you are in the OpenAI ecosystem;
OpenCode is the right choice if you want model-agnostic open-source tooling.

---

### Category 2 — AI IDEs
*Best for SkillOS from v4.0 when building the web platform.*

| Tool | Provider | Agents | Best For |
|---|---|---|---|
| **Cursor** | Anysphere | Up to 8 parallel (v2.0) | Best all-round AI IDE; most widely adopted; strong single-session work |
| **Antigravity 2.0** | Google | Up to 5 parallel | Built-in Chrome browser; visual verification; Gemini 3.5 Flash default |
| **Devin Desktop** | Cognition | Async cloud agents | Formerly Windsurf; rebranded June 2026; supports ACP open protocol |
| **Zed** | Zed Industries | Agent mode | Fast open-source editor; free; works well alongside terminal agents |
| **Kiro** | Amazon | Agent mode | AWS-ecosystem integration; strong for teams on AWS infrastructure |
| **JetBrains AI** | JetBrains | Assistant | Built-in to JetBrains IDEs; free tier available |

**For SkillOS v4.0+ (web platform):** Cursor or Antigravity 2.0 for parallel agent
work. Cursor leads on versatility; Antigravity leads on visual browser verification.
Devin Desktop (formerly Windsurf) is worth watching for its ACP open protocol support.

---

### Category 3 — Visual Workspaces
*For managing multiple agent sessions and reviewing diffs at scale.*

| Tool | Provider | Notes |
|---|---|---|
| **Claude Code Desktop** | Anthropic | Free with Claude subscription; wraps Claude Code with visual interface |
| **Codex Desktop App** | OpenAI | Desktop GUI for Codex; visual diff review |
| **Nimbalyst** | Community | Open-source; model-agnostic; parallel session management; free for individuals |

---

### Category 4 — Cloud Agents
*For delegated long-running tasks without a local environment.*

| Tool | Provider | Notes |
|---|---|---|
| **Devin** | Cognition | Autonomous PR creation; long-running tasks; browser-equipped |
| **Replit Agent** | Replit | Browser-based; best for prototyping without local setup |

---

### Tool Decision Guide for SkillOS Contributors

```
Task: Registry work (skill files, Git, CI, validation recording)
→ Use any terminal agent: Claude Code, Codex CLI, OpenCode, or Aider
→ Feed context.md at the start of every session

Task: Skill generation via Skill Creator
→ Use any capable AI interface with the SKILL-CREATOR.md system prompt
→ Tier 1 models recommended for generation quality

Task: Web platform development (v4.0+)
→ Use Cursor or Antigravity 2.0 for parallel agent work
→ Built-in browser verification matters here

Task: Contributing without a local dev environment
→ Use Replit Agent or GitHub Codespaces with any terminal agent

Task: Testing skill output across models
→ Run the validation harness on your preferred interface
→ Record results in the skill's Component 13 Validation Record
```

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

**v1.0 — Foundation** *(complete)*
- [x] Skill Definition Standard (13 components)
- [x] Skill Creator compiler (10-phase generation)
- [x] 3 pilot skills: Software Architect, Frontend Specialist, React Expert
- [x] Validation test harness
- [x] Validation tests run (7/9 PASS, 92% SDS compliance)
- [x] GitHub Actions: SDS compliance validator on PRs
- [x] context.md session file for AI coding tools
- [x] Observability gap fixed (Software Architect v1.0.1 — now 13/13 SDS compliance)
- [x] GitHub repo live

**v1.1 — Refinement** *(complete)*
- [x] Assumption Documentation Template (converts 2 CONDITIONAL → 2 PASS)
- [x] Cross-Tier Routing Map (Tier 0 → 1 → 2 handoff documentation)
- [x] Testing Strategy Formalization (Tier 0 and Tier 1 testing guidance)
- [x] Cross-model validation on pilot skills (Tier 1 model results recorded)

**v2.0 — Registry** *(in progress)*
- [ ] 20+ skills across all tiers (7/20 complete)
- [x] Rebuilt Security Principles (Tier 0) to 13/13 SDS compliance & validated (3/3 PASS)
- [x] Rebuilt Backend Specialist (Tier 1) to 13/13 SDS compliance & validated (3/3 PASS)
- [x] Rebuilt Database Specialist (Tier 1) to 13/13 SDS compliance & validated (3/3 PASS)
- [x] Rebuilt DevOps Specialist (Tier 1) to 13/13 SDS compliance & validated (3/3 PASS)
- [ ] Community contribution pipeline mature
- [x] Automated SDS compliance check live in GitHub Actions

**v3.0 — Runtime**
- [ ] MCP server exposing skills as activatable tools
- [ ] Multi-skill orchestration with typed context handoffs
- [ ] Skills callable by name from any MCP-compatible interface

**v4.0 — Platform**
- [ ] Web interface for browsing, searching, and testing skills
- [ ] Community ratings and reviews
- [ ] Skill versioning dashboard
- [ ] Visual skill composition tool
- [ ] Parallel agent development begins (Cursor or Antigravity 2.0)

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
- [GitHub Sponsors](https://github.com/sponsors/joshuamwangangi) — support
  the maintainer directly; appears on your GitHub profile
- [Open Collective](https://opencollective.com/skillos) — transparent community
  fund; all income and spending publicly visible; preferred for infrastructure

**Why funding matters:**
Validation testing across multiple AI models has a cost. CI infrastructure
has a cost. The people who maintain the standard and review contributions
deserve support. Funding does not change who owns the project — the world
still owns it. It changes whether the people maintaining it can sustain
that work long-term.

**Contribute without code or money:**
- Run validation tests on existing skills and submit results
- Add regional regulatory guidance not yet covered
- Translate skills or README content into other languages
- Report skills that produce incorrect or outdated output
- Write tutorials, examples, or integration guides
- Update model or tool recommendations as the landscape shifts

**Compute contributions:**
If you have access to compute for multi-model validation testing,
open an issue with the label `compute-offer`.

---

## License

MIT — because this belongs to everyone.

Attribution is required in forks. Not for ownership — for traceability.
When a skill gets forked and modified, its lineage helps future
contributors understand what changed and why.

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

*SkillOS v1.1 · MIT License · Built for the world*
