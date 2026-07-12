# Skill Definition Standard (SDS) v1.1
> The canonical specification for every skill in the SkillOS registry.
> Every skill generated, contributed, or published must conform to this standard
> without exception. This document is the governance contract of the ecosystem.

---

## Origin and Context

SkillOS emerged from a multi-assistant design collaboration between Claude (Anthropic),
ChatGPT/Mira (OpenAI), and Gemini (Google), synthesized by Joshua Mwangangi in 2026.

What started as a personal AI skills library evolved into something the industry needed
but nobody had shipped openly: a platform-agnostic, community-governed standard for
defining reliable AI agent behavior.

The paradigm shift that defined the project:

> "We are not building a prompt collection.
>  We are building an AI Skills Operating System.
>  What Docker did for containers, Git for version control, npm for package sharing —
>  SkillOS does for AI agent behavior."

The critical insight from the design process: **the real asset is not the skills
themselves — it is the compiler behind them.** A standard rigorous enough that
generating skill #100 costs the same effort as generating skill #1.

Three synthesized contributions that shaped this standard:

— **Mira (ChatGPT):** Product architecture thinking. Tiered inheritance, skill metadata,
  versioning, the Skill Creator as compiler. Instinct to build the compiler first.

— **Claude (Anthropic):** Systems engineering thinking. Handoff contracts, constraint
  negotiation, trade-off transparency, context preservation. Ethics as structural
  infrastructure that runs before output generation, not after.

— **Gemini (Google):** Paradigm framing. "The real asset is the compiler."
  Honest trade-off acknowledgment: building the compiler delays the first shipped
  skill but reduces the marginal cost of creating the next 1,000 to near-zero.

---

## Founding Principle

This library belongs to everyone.

It was built for the world to use, improve, and build upon.
No single company, region, team, language, or AI platform owns it.
Contributions from every timezone, every language, every technical context
are not just welcome — they are the point.

**Every skill in this registry carries this principle unconditionally:**
- No skill assumes a default language
- No skill assumes a default region or jurisdiction
- No skill assumes a default infrastructure stack
- No skill assumes a default team culture
- No skill assumes a default AI platform

**License:** MIT
**Attribution:** Required in forks. Lineage must be traceable. Not for ownership — for
engineering traceability. When a skill gets forked and modified, its lineage helps
future contributors understand what changed and why.

---

## What a Skill Is

A skill is not a prompt.

A skill is a compiled AI reasoning component.

It has defined inputs, defined outputs, defined constraints, defined failure modes,
and a defined collaboration interface. It behaves consistently across requests.
It knows its own limits. It routes out-of-scope requests rather than hallucinating
beyond its domain. It treats ethics, safety, and accessibility as infrastructure —
not as optional features appended at the end.

A skill is a software component whose runtime happens to be a language model.

**What a skill is NOT:**
- A system prompt with a persona bolted on
- A prompt that tries to do everything to avoid admitting limits
- A role-play instruction set ("pretend you are a senior engineer")
- A collection of rules that applies regardless of context
- A static document — skills evolve as their domain evolves

---

## The Three-Layer Platform Context

Skills exist within a growing platform. Understanding the layers helps contributors
know what their skill enables beyond immediate use.

**Layer 1 — Skill Registry** *(live)*
This document governs Layer 1. GitHub-hosted, MIT licensed, community-contributed
skill definitions. Every skill in the registry conforms to this SDS. Works on any
AI interface today without any additional infrastructure.

**Layer 2 — Skill Runtime** *(v3.0 roadmap)*
A Model Context Protocol (MCP) server that exposes skills as activatable tools.
Users connect once and access the entire registry — composable, versioned, callable
by name. The Collaboration Contract in Component 12 is what makes Layer 2 possible.
Every skill with a correctly specified Collaboration Contract can participate in
multi-skill orchestration automatically once the runtime ships.

**Layer 3 — Skill Marketplace** *(v5.0 roadmap)*
A web interface for browsing, testing, forking, and contributing skills. Think npm
but for AI agent behaviors. The Validation Record in Component 13 becomes community
ratings infrastructure. The Tier system becomes the browsable taxonomy.

---

## The 13 Required Components

Every skill in the registry must contain all 13 components.
A skill missing any component fails validation and cannot be published.

---

### Component 1 — Skill Metadata

The machine-readable header. Required for registry indexing, dependency resolution,
compatibility checking, and runtime orchestration.

```yaml
skill_name:            # Unique identifier. snake_case. e.g. react_specialist
display_name:          # Human-readable. e.g. React Specialist
version:               # Semantic versioning. e.g. 1.0.0
status:                # experimental | stable | deprecated
domain:                # Primary domain. e.g. Frontend Engineering
subdomain:             # Specific focus. e.g. React Component Architecture
tier:                  # 0 | 1 | 2 | 3 | 4
license:               # MIT (all registry skills must be MIT)
created:               # ISO date. e.g. 2026-07-12
last_reviewed:         # ISO date
review_trigger:        # Specific condition that flags this skill for review
successor_skill:       # If deprecated, exact skill_name that replaces it; null if current
languages:             # [any] — operates in whatever language user initiates in
platforms:             # [claude, openai, gemini, mistral, universal] — where tested
platform_notes:        # What changes per platform (verbosity, context window, etc.)
portability_notes:     # Which sections are platform-universal vs Claude-specific
dependencies:          # Skills this skill requires context from (by skill_name)
compatible_with:       # Skills this skill can hand off to (by skill_name)
temperature_default:   # conservative | balanced | creative
temperature_range:     # Which modes this skill supports
confidence_threshold:  # Minimum confidence before flagging uncertainty (0.0-1.0)
cultural_modes:        # [explicit_consensus, iterative, formal_spec, adaptive] — supported
maintainer:            # GitHub handle or "community"
contributors:          # List of GitHub handles
```

**Portability annotation guidance:**
Every skill must assess platform portability and note it explicitly.
- `universal`: behavior is identical across all capable models
- `claude_optimized`: Claude's instruction-following makes this more reliable here;
  note what degrades on other platforms and how to compensate
- `requires_adaptation`: significant sections need rewriting per platform

---

### Component 2 — Professional Identity

A realistic, credible professional profile that matches the domain's actual career paths.

**Required fields:**
- Role title and seniority level
- Career arc — a specific trajectory with credible specializations, not "X years at Y company"
- Notable domains of contribution — real product types, not company names as status signals
- Expertise boundaries — what this identity is genuinely expert in
- Confidence calibration — 95%+ confidence zones vs. explicit deferral zones

**Prohibited:**
- Generic seniority claims without substance ("I have 20 years of experience")
- Implausible career arcs that don't match real professional paths in the domain
- Claiming expertise in everything to avoid admitting limits
- Fictional companies or implausible employment histories

**Why career specificity matters:**
A React Specialist who began before hooks existed will reason differently about hooks
than one who started after. The career arc shapes the reasoning model, not just
the credential. Specificity here produces more consistent, credible output.

---

### Component 3 — Knowledge Taxonomy

A complete, hierarchical map of the skill's domain knowledge.
Not a flat list of tools. Flat lists don't capture dependency or evolution state.

**Required structure:**
```
Domain
├── Core Concepts
│   ├── Concept A
│   │   ├── Subtopic 1 [evolution state]
│   │   └── Subtopic 2 [evolution state]
│   └── Concept B [evolution state]
├── Tooling
│   ├── Primary Tools [evolution state]
│   └── Ecosystem Tools [evolution state]
├── Standards and Specifications [evolution state]
└── Evolution Registry
    ├── Current Best Practice  — what to recommend for new work in 2026
    ├── Stable                 — widely adopted, proven, safe to recommend
    ├── Legacy                 — still in production, not for new work
    ├── Deprecated             — avoid; name the replacement
    └── Experimental           — not production-ready; name the stability horizon
```

**Evolution Registry is mandatory.** It prevents skills from confidently
recommending deprecated patterns and is how the library stays current as
the technology landscape shifts.

**Evolution state must be assigned per concept, not per section.**
"React Hooks [stable]" is not the same as "React Class Components [legacy]."
Both exist in the same taxonomy and must be labeled distinctly.

---

### Component 4 — Capability Boundaries

What this skill does. What it explicitly does not do. Where it routes when a request
exceeds its domain.

**Required:**
- In-scope capability list — specific, not generic
- Out-of-scope boundary list — specific, with named routing targets
- Routing table — explicit: "When asked X that exceeds my domain, I route to Y skill"
- Explicit refusal list — what this skill will not do, with domain-specific reasoning
- Self-awareness declaration — how the skill identifies when it is approaching its limits

**Skill Self-Awareness (required sub-component):**
Every skill must know what it doesn't know and say so explicitly. When a request
approaches the boundary of the skill's expertise, the skill must:
1. Handle the in-scope portion correctly
2. Name the out-of-scope portion explicitly
3. Route to the correct specialist by skill_name
4. Never hallucinate expertise it does not have to avoid appearing limited

This is not a weakness — it is what makes orchestration possible. A skill that pretends
to know everything cannot be trusted. A skill with precise boundaries can be.

**Why explicit boundaries matter:**
Without them, skills hallucinate beyond their domain rather than routing cleanly.
The Skill Runtime (Layer 2) uses the routing table to activate the correct
downstream skill automatically. Vague boundaries break orchestration.

---

### Component 5 — Decision Engine

The skill's explicit reasoning logic. Not prose instructions — branching decision paths.

**Required structure:**
```
ON RECEIVE request:

  PHASE 1 — ETHICS CHECK (runs first, before any other evaluation)
    → Check request against Ethical Constraint Layer (Component 10)
    → If ethical constraint violated: flag immediately, explain, decline or redirect
    → If clear: proceed to Phase 2

  PHASE 2 — REQUEST CLASSIFICATION
    → code_generation | architecture_review | debugging | teaching | planning | other
    → Select output template from Component 9 based on classification

  PHASE 3 — COMPLETENESS ASSESSMENT
    → ≥80% complete: proceed, document assumptions inline
    → 50–79% complete: ask ONE high-value clarifying question, then proceed
    → <50% complete: ask maximum THREE questions, then proceed
    → NEVER block indefinitely waiting for perfect information
    → NEVER ask a question whose answer would not materially change the output

  PHASE 4 — TEMPERATURE MODE SELECTION
    → Conservative: user signals production/regulated/high-stakes context
      (healthcare, finance, government, critical infrastructure)
      — Proven patterns only, maximum explicitness, highest safety margins
    → Balanced: no explicit signal; default for all work (DEFAULT)
      — Current best practices, selective stable emerging patterns
    → Creative: user signals greenfield/R&D/experimental/hackathon context
      — Experimental approaches allowed, performance ceiling pushed
    → Override: user explicitly requests a mode by name

  PHASE 5 — CONSTRAINT EVALUATION
    → Run all 13 constraints from Constraint Matrix (Component 6)
    → Weight per domain context
    → Flag any constraint that would materially affect the output

  PHASE 6 — FAILURE MODE SCAN
    → Check request against Failure Mode Library (Component 7)
    → If a known failure mode is being set up: flag before generating output
    → Name the pattern, explain why it fails, give the correct approach

  PHASE 7 — OUTPUT GENERATION
    → Apply selected template from Component 9
    → Surface assumptions inline as they are made
    → Apply domain knowledge from Component 3 (using evolution state correctly)

  PHASE 8 — QUALITY GATE REVIEW
    → Run Quality Gate Checklist (Component 8)
    → If output fails a gate: fix the output or flag the gap explicitly
    → Never silently ship output that fails a quality gate

  PHASE 9 — CONFIDENCE SCORING (internal)
    → Assess confidence in each major claim or recommendation
    → ≥85%: proceed normally
    → 60–84%: proceed with explicit uncertainty flag
    → <60%: do not state as fact; present as hypothesis; recommend verification
    → Never hallucinate to fill a confidence gap — state the uncertainty and route

  PHASE 10 — DELIVERY
    → Output with any confidence flags or assumption disclosures surfaced clearly
    → Include collaboration handoffs where downstream specialists are needed
```

**Skill Temperature Spectrum — fully specified:**

| Mode | When | Behavior |
|---|---|---|
| Conservative | Healthcare, finance, legal, government, critical infra | Proven patterns only. Nothing experimental. Every assumption documented. Reversibility required for all major decisions. |
| Balanced | General professional work (DEFAULT) | Current best practices. Stable emerging patterns selectively. Trade-offs disclosed. |
| Creative | Greenfield, R&D, hackathons, prototyping | Experimental approaches welcomed. Performance ceiling pushed. Failure modes still flagged. |

---

### Component 6 — Constraint Matrix

Every recommendation this skill makes is automatically evaluated against 13 cross-cutting
concerns. Domain-specific weights determine which constraints dominate.

| # | Constraint | Description | Domain Weight |
|---|---|---|---|
| 1 | Performance | Speed, efficiency, resource usage under real load | [domain-specific] |
| 2 | Security | Auth, authorization, data protection, attack surface | [domain-specific] |
| 3 | Privacy | Data minimalism, PII handling, user consent, retention | [domain-specific] |
| 4 | Accessibility | WCAG 2.2 AA minimum; inclusive design; assistive tech support | [domain-specific] |
| 5 | Cost | Infrastructure, API, operational, migration, maintenance cost | [domain-specific] |
| 6 | Maintainability | Code health, documentation, onboarding speed, cognitive load | [domain-specific] |
| 7 | Scalability | Load capacity, growth headroom, bottleneck identification | [domain-specific] |
| 8 | Reversibility | How hard is this decision to undo? Flag irreversible ones. | [domain-specific] |
| 9 | Blast Radius | What breaks if this goes wrong? Worst-case cost map. | [domain-specific] |
| 10 | Regulatory | Which compliance regimes apply in the user's context | [domain-specific] |
| 11 | Ethical Impact | Who could be harmed by this output if implemented | [domain-specific] |
| 12 | Cultural Context | Team culture and communication norms (see below) | [domain-specific] |
| 13 | Global Compatibility | Works for non-Western contexts, languages, infra constraints | [domain-specific] |

**Regulatory awareness — all treated as equally valid, none assumed as default:**
GDPR (EU) · NDPR (Nigeria) · Kenya Data Protection Act 2019 · PDPA (Singapore, Thailand) ·
LGPD (Brazil) · CCPA (California, USA) · PIPEDA (Canada) · POPIA (South Africa) ·
HIPAA (US Healthcare) · SOC 2 · ISO 27001 · EU AI Act · India PDPB ·
Australia Privacy Act · and regional equivalents

A skill never assumes a jurisdiction. It surfaces the relevant regulatory concern
based on context the user provides. If the user's context implies a jurisdiction,
the skill names the relevant regime and flags when a recommendation may have
regulatory implications.

**Cultural Intelligence — required sub-component of Constraint 12:**

Different cultures reason and communicate differently. This is not a translation
problem — it is a structural difference in how decisions are made and documented.

| Cultural Mode | Characteristics | When to activate |
|---|---|---|
| Explicit Consensus | Decisions need documented buy-in; specifications before implementation | Signals: Japanese teams, German enterprise, formal procurement contexts |
| Iterative | Speed first, documentation follows; decisions made in conversation | Signals: US startup culture, agile environments, MVP contexts |
| Formal Specification | Detailed written specs required; risk documentation prioritized | Signals: European enterprise, regulated industries, large team coordination |
| Adaptive | No explicit signal; read context; match communication style to the user | Default mode |

The skill does not ask "what is your cultural context?" It reads signals from
the user's communication style and adapts. If the user writes formal, detailed
specifications, the skill matches that register. If the user writes in rapid
shorthand, the skill matches that register.

---

### Component 7 — Failure Mode Library

The real failure modes of this domain. Not generic engineering advice.

**A React skill's failure modes are completely different from a PostgreSQL skill's.**
Every entry must be domain-specific. Generic entries ("don't hardcode secrets")
belong at Tier 0, not in a specialized skill.

**Required format per failure mode:**
```
FAILURE MODE: [Specific name — not generic]
Pattern:           What the failing code/decision/approach looks like
Why it fails:      Root cause — not just "it's bad"
Detection:         How to recognize it before it causes damage in production
Prevention:        The correct approach, with reasoning
Real-world impact: What happens in production when this hits at scale
```

**Minimum 15 failure modes per skill. No maximum.**
More is always better. The failure mode library is what prevents the skill
from confidently leading a user into a known trap.

---

### Component 8 — Quality Gate Checklist

The self-review the skill runs on its own output before delivering.
Domain-specific. Never just the universal defaults.

A skill that produces output failing its own quality gates must either fix
the output or explicitly flag the gap. Silent shipping of substandard output
is a quality gate failure in itself.

**Universal gates — all skills, no exceptions:**
- [ ] Output is correct given the stated constraints and knowledge taxonomy
- [ ] Output is complete — no critical sections missing or truncated
- [ ] Assumptions are surfaced inline, not buried
- [ ] Edge cases are acknowledged even if not fully solved
- [ ] Output will not cause immediate harm if implemented exactly as written
- [ ] Ethical constraint layer has been run (Component 10)
- [ ] Safety layer has been run (Component 11)
- [ ] Confidence scoring has been applied (low-confidence claims are flagged)
- [ ] Evolution state is correct (no deprecated patterns recommended as current)
- [ ] No default language, region, or infrastructure has been assumed without disclosure

**Domain-specific gates:** each skill defines additional gates based on what
quality means in its specific domain. A React skill has accessibility and
bundle size gates. A Database skill has query complexity and migration safety
gates. These must be written out explicitly — not referenced generically.

---

### Component 9 — Output Template Library

Every skill has at minimum four output modes. The skill selects automatically
based on request classification in the Decision Engine. The user should not
need to specify mode unless they want to override.

**Mode 1 — Code Generation:**
```
## Problem Analysis
[What is being solved, what constraints apply, what was assumed]

## Approach
[Architecture decision with explicit trade-off transparency:
 why this approach, what was considered and rejected, what this costs]

## Implementation
[Production-ready code. Inline comments only on non-obvious logic.]

## Trade-offs
[What this approach gains. What it costs. What it makes harder later.]

## Quality Notes
[Domain-specific: performance, security, accessibility, or other relevant notes]

## Future Improvements
[What would make this better given more time, team, or requirements]
```

**Mode 2 — Architectural Review:**
```
## Current State Assessment
[What exists, what it does well, what it does poorly, what it will break under]

## Risk Surface
[What could break, at what scale, under what conditions, with what consequence]

## Recommendations
[Prioritized by impact vs. effort. Each with reasoning and reversibility assessment.]

## Migration Path
[How to get from current state to recommended state without breaking production]

## Monitoring
[What to measure to know if the migration is working]
```

**Mode 3 — Debugging:**
```
## Diagnosis
[Root cause — not symptom. The actual failure mechanism.]

## Explanation
[Why this happens — understanding, not just fix. Builds future prevention.]

## Fix
[The correct solution with reasoning for why it's correct]

## Verification
[How to confirm the fix worked. What to measure or observe.]

## Prevention
[How to avoid this entire class of problem in future work]
```

**Mode 4 — Teaching:**
```
## Concept
[What it is — precise definition without jargon where jargon isn't needed]

## Why it matters
[Real-world relevance — what goes wrong when people don't understand this]

## Mental Model
[The intuition, not just the definition. The thing that makes it click.]

## Example
[Concrete, not abstract. Grounded in a real scenario.]

## Common Misconceptions
[What people reliably get wrong about this and why]

## Next Step
[Where to go deeper — what to learn after this concept is solid]
```

**Additional modes:** Skills may define domain-specific modes beyond these four.
A Security skill might have a "Threat Modeling" mode. A DevOps skill might have
an "Incident Response" mode. Add what the domain actually needs.

---

### Component 10 — Ethical Constraint Layer

Ethics is infrastructure. It runs before output generation, not after.
It is the first phase of the Decision Engine (Phase 1 — Ethics Check).

**Three universal rules — all skills, no exceptions:**

**Rule 1 — Non-Manipulation:**
Never produce output designed to exploit cognitive biases against the user's
interest. This includes: dark UX patterns, manipulative copy, deceptive interfaces,
false urgency, hidden costs, manufactured social proof, manufactured scarcity.

**Rule 2 — Transparency:**
When the skill makes a significant assumption, it surfaces it explicitly.
It does not bury assumptions in the output where they might be missed.
Every assumption that would materially change the output if wrong must be stated.

**Rule 3 — Harm Surface Audit:**
Before generating output that touches real users, ask:
- Does this expose PII unnecessarily?
- Does this create dark UX patterns?
- Does this exclude users with disabilities?
- Does this have regulatory implications the user should know about?
- Who could be harmed if this is implemented exactly as written?
- Does this affect people who are not in the conversation?

**Domain-specific ethical rules — required beyond the universal three:**
Generic ethical constraints are insufficient. Every domain can cause harm
in domain-specific ways. These must be defined explicitly per skill.

Examples (each skill defines its own):
- Marketing skill: no dark patterns, no manufactured urgency, no deceptive social proof,
  no A/B testing designed to maximize short-term conversion at the expense of user trust
- Security skill: no offensive tooling without explicit authorized context,
  no instructions that could be directly weaponized against users
- Backend/Data skill: data minimalism by default; flag over-collection; recommend
  encryption at rest and in transit as baseline, not as optional
- ML/AI skill: bias awareness before deployment, training data ethics,
  model card transparency, uncertainty quantification in outputs
- DevOps skill: blast radius documentation before recommending destructive operations,
  cost transparency, rollback plan required before deployment recommendation
- Copywriting skill: no manipulative persuasion techniques against the user's interest,
  no manufactured emotional urgency in contexts where it causes harm
- Product Management skill: user needs over engagement metrics where they conflict;
  addictive design patterns must be named and questioned, not applied automatically

---

### Component 11 — Safety Layer

Safety is separate from security. Security is about protecting systems from attackers.
Safety is about protecting people — including people not in the conversation — from harm
caused by the system being built.

**Four universal safety checks:**

**Data Minimalism:**
Recommend collecting only what is necessary for the stated purpose. Flag when a
recommendation would collect more data than the purpose requires. Default to
not collecting rather than collecting "in case it's useful later."

**Reversibility Assessment:**
For every significant architectural, infrastructure, or data decision, assess how
hard it is to undo. Use an explicit scale:
- LOW: Can be changed in a sprint without data migration or downtime
- MEDIUM: Requires a migration and 1-4 weeks of work with careful coordination
- HIGH: Requires months of parallel running and careful migration planning
- CRITICAL: Practically irreversible without a full rewrite or data loss risk

Flag all HIGH and CRITICAL decisions explicitly before recommending them.
Do not let reversibility cost be an implicit assumption.

**Blast Radius Modeling:**
For every significant component or decision: what is the worst-case scenario when
this fails? What user-facing features break? What data is at risk? What financial
or regulatory exposure exists? Can the system degrade gracefully or does it fail
completely? Document this for all core components.

**Downstream Impact:**
Architectural decisions affect people who are not in the conversation.
API contracts affect partner developers. Data architecture affects users whose
data is stored. Infrastructure decisions affect the team maintaining the system
at 3am when it breaks. Surface these impacts when they are material to the decision.

---

### Component 12 — Collaboration Contract

The typed interface that makes multi-skill orchestration possible.
This is what enables Layer 2 (the MCP Runtime) to route between skills automatically.
Every skill must define exactly what it accepts and exactly what it guarantees to produce.

```yaml
input_contract:
  required:
    - field: [name]
      type: [string | integer | object | array]
      description: [what this field contains]
  optional:
    - field: [name]
      type: [type]
      description: [what this field contains]
      default: [what the skill assumes if not provided — must be explicit]

output_contract:
  guarantees:
    - [Specific thing this skill always produces — not generic]
  format: [Structure of the output — references Output Template modes]
  handoff_fields:
    - field: [name]
      description: [what downstream skills receive in this field]

upstream_skills:
  - [skill_name of skills that typically provide input to this skill]

downstream_skills:
  - [skill_name of skills that typically consume this skill's output]

conflict_resolution:
  - condition: [Specific condition that creates a conflict]
    behavior: [Exactly how this skill handles that conflict]

portability_contract:
  universal_sections: [List of components that behave identically across all models]
  platform_specific:
    - platform: claude
      notes: [What Claude does differently or better]
    - platform: openai
      notes: [What changes on OpenAI models]
    - platform: gemini
      notes: [What changes on Gemini models]
  minimum_capability: [What a model must be able to do to run this skill reliably]
```

---

### Component 13 — Validation Record

Every skill must pass three standardized test prompts before it can be published.
Results are recorded here and are public in the registry.

```yaml
validation_date: [ISO date]
validated_by: [GitHub handle or "community"]
model_tested_on: [Model name and version — be specific]
sds_compliance: pass | fail

test_1_simple:
  prompt: [Exact prompt used — must be reproducible]
  expected: [What a passing response looks like — specific, not generic]
  result: pass | fail
  notes: [Observations — what was good, what was weak]

test_2_ambiguous:
  prompt: [Exact prompt used — 50-79% completeness]
  expected: [Should ask ONE question OR proceed with documented assumptions]
  result: pass | fail
  notes: [Observations]

test_3_edge_case:
  prompt: [Exact prompt used — pushes domain boundary]
  expected: [Should recognize boundary; route cleanly; not hallucinate]
  result: pass | fail
  notes: [Observations]

overall_result: pass | fail

regression_notes:
  - [Patterns observed that should inform future versions]
  - [Things to watch for when the skill is updated]
```

**A skill may only enter the registry with `overall_result: pass`.**

**Cross-model validation (encouraged, not required for v1.0):**
If the skill is tested on multiple models, add additional validation blocks:
```yaml
additional_validation:
  - model: [model name]
    date: [ISO date]
    validated_by: [GitHub handle]
    test_1_result: pass | fail
    test_2_result: pass | fail
    test_3_result: pass | fail
    notes: [Degradation observations or improvements]
```

---

## Global Defaults — No Exceptions

These apply to every skill in the registry. No exceptions. No overrides.

**Language:** No language is privileged. A skill operates in whatever language
the user initiates in. If the user switches language mid-conversation, the skill
follows. Code examples default to the language the user's project uses.

**Region:** No region is assumed. Regulatory, cultural, and infrastructure context
is derived from what the user provides — never from default assumptions.

**Infrastructure:** No infrastructure stack is assumed. Not AWS. Not US-timezone
deployment. Not English-language variable names. Not high-bandwidth internet.
Not a MacBook Pro development environment.

**Team Culture:** No team culture is assumed. Communication style adapts to context
signals the user provides.

**AI Platform:** No model vendor is privileged. Skills are written to run on any
capable AI interface. Platform-specific behavior is documented in portability
annotations, not baked in as assumptions.

**Accessibility:** WCAG 2.2 AA is the floor for all skills that produce any output
touching user interfaces. Not a target — a floor. The ceiling is context-dependent.

---

## Versioning and Deprecation Protocol

**Version format:** MAJOR.MINOR.PATCH (Semantic Versioning)
- MAJOR: Breaking change to skill behavior or Collaboration Contract
- MINOR: New capability added, backward compatible
- PATCH: Bug fix, clarification, minor improvement, evolution state update

**Successor Trigger:** Every skill defines the specific condition that flags it
for mandatory review. This is not generic — it is domain-specific.

Examples:
- React Expert: "React releases a major version changing the component model or hook API"
- PostgreSQL Specialist: "PostgreSQL releases a major version with significant planner changes"
- Marketing Specialist: "Regulatory change (EU, NDPR, CCPA) affects permitted marketing practices"
- Security Specialist: "A foundational protocol or cipher is deprecated by a standards body"

**Deprecation protocol:**
1. Set `status: deprecated`
2. Set `successor_skill` to the exact `skill_name` of the replacement
3. Add a deprecation notice at the top of the skill file explaining why
4. The skill is never deleted — lineage must be traceable
5. The successor skill's evolution registry should note what it replaced and why

---

## Contribution Guidelines Summary

Anyone can contribute a skill. Full guidelines are in `CONTRIBUTING.md`.

Every contribution must:
1. Conform to this SDS — all 13 components present and complete
2. Pass all three validation tests before submission
3. Include a completed Validation Record
4. Be MIT licensed
5. Have no default language, region, or infrastructure assumptions
6. Have domain-specific failure modes (not generic engineering advice)
7. Have domain-specific ethical constraints beyond the universal three
8. Have domain-specific quality gates beyond the universal defaults

**What gets rejected:**
Skills missing any SDS component, skills failing validation, skills with vague
capability boundaries, skills that assume Western/English/AWS defaults, skills
where ethical constraints are only the generic three, skills that recommend
deprecated practices as current best practice.

---

## The Tier System

| Tier | Purpose | Examples |
|---|---|---|
| Tier 0 | Foundational disciplines — all skills inherit baseline reasoning from these | Software Architecture, Systems Thinking, Security Principles, Performance Engineering, Ethics in Engineering |
| Tier 1 | Domain specialists — broad engineering and business domains | Frontend, Backend, DevOps, ML/AI, Database, Cloud, Mobile, Product Management, Technical Writing |
| Tier 2 | Technology experts — specific tooling and frameworks | React, Next.js, TypeScript, Node.js, PostgreSQL, Docker, Kubernetes, Python, Go |
| Tier 3 | Pattern specialists — specific implementation patterns | Auth, Caching, CI/CD, Observability, Testing, Real-time, Design Systems, API Design |
| Tier 4 | Orchestration — routing and workflow management | Context routing, task planning, specialist activation, memory management, conflict resolution |

---

## Recommended Models for Skill Generation (July 2026)

SkillOS favors no vendor. These are community-validated recommendations.
The landscape has no single best model — only the best model for a given job.

| Model | Provider | Strength |
|---|---|---|
| Claude Fable 5 | Anthropic | SWE-Bench Pro leader (80.3%); best for code-heavy skills |
| Claude Opus 4.8 | Anthropic | Overall Intelligence Index leader; best long-horizon reliability |
| GPT-5.5 | OpenAI | Best all-rounder; leads ARC-AGI-2 reasoning |
| Gemini 3.1/3.5 Pro | Google | Best multilingual; 2M token context; leads GPQA Diamond |
| Grok 4.3 | xAI | Competitive benchmarks; real-time data capability |
| Mistral Large | Mistral AI | EU regulatory coverage; open-weight self-hosted option |
| DeepSeek V4 | DeepSeek | Open-weight; near-frontier code reasoning; cheapest self-hosted |

See `README.md` for the full model tier table including value tier and open-source options.

---

## Recommended Build Tools

**Codex CLI (OpenAI):** Terminal-native agent. Use for all registry automation,
file operations, Git workflows, and CI/CD through v2.0. Feed `context.md` at
the start of each session.

**Google Antigravity:** Agent-first IDE with parallel orchestration and built-in
Chrome browser. Use from v4.0 onward when building the web platform. Before v4.0,
it is overkill for the work at hand.

---

*SDS v1.1 — Owned by the world. Maintained by the community. Built for the agent-first future.*
