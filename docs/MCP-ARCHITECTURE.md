# SkillOS MCP Runtime — Architecture Document

> **Version:** v3.0-design
> **Phase:** 3.1 — MCP Server Design
> **Status:** Design complete. Implementation begins after MCP prerequisites (see Prerequisites section).
> **Goal:** Turn the SkillOS registry from a collection of text files into a connectable, programmable runtime that any MCP-compatible client can activate.

---

## The Core Insight

Every skill in the registry has a **Collaboration Contract** (Component 12) — a typed YAML I/O specification defining exactly what the skill accepts and what it produces. This is not documentation. This is the interface definition the MCP server reads to route between skills automatically.

The registry is the software. The MCP server is the runtime that executes it.

---

## Prerequisites

Before writing a single line of implementation code, complete these in order:

1. **[Introduction to Model Context Protocol](https://anthropic.com/academy)** (Anthropic Academy — mandatory)
2. **[Model Context Protocol: Advanced Topics](https://anthropic.com/academy)** (Anthropic Academy — mandatory)
3. **[Building with the Claude API](https://anthropic.com/academy)** (Anthropic Academy — recommended)

Rationale: MCP is an evolving protocol. The official Anthropic courses reflect the current canonical implementation. Do not build against blog post tutorials.

---

## What the MCP Runtime Does

```
User (in Claude / VS Code / any MCP client)
  │
  │  "Activate Software Architect"
  ▼
MCP Server (SkillOS Runtime v3.0)
  │
  ├─ Reads registry/tier-0/software-architect-v1.0.3.md
  ├─ Validates: all 13 SDS components present?
  ├─ Extracts: Component 2 (Identity), Component 5 (Decision Engine),
  │            Component 12 (Collaboration Contract)
  │
  ▼
Claude (or any LLM with MCP support)
  │  Now operating under the full Software Architect skill definition
  │
  │  "Design the API layer for this product"
  ▼
Software Architect output
  │
  │  Collaboration Contract output fields:
  │    - api_contract: {...}
  │    - recommended_patterns: [...]
  │    - handoff_to: backend_specialist
  │
  ▼
MCP Server (auto-routing)
  │  Detects handoff_to: backend_specialist
  ├─ Loads registry/tier-1/backend-specialist-v1.0.0.md
  ├─ Injects Software Architect output as Backend Specialist input
  │
  ▼
Backend Specialist (operating with upstream context)
```

---

## Implementation Language Decision

| Option | Pros | Cons |
|---|---|---|
| **Python + FastMCP** | Fastest iteration, great ecosystem, easiest to prototype | TypeScript community is larger for MCP tooling |
| **TypeScript + MCP SDK** | Native to the broader JS/TS ecosystem, easier for web-dev contributors | Slightly more boilerplate |

**Decision: TypeScript + MCP SDK**

Rationale: SkillOS is targeting developer contributors. The majority of frontend/backend skills in the registry are TypeScript-first. Eating your own cooking: the TypeScript Specialist skill in the registry covers the exact patterns needed. Contributors will be more comfortable submitting TypeScript than Python.

---

## MCP Tool Definitions

The runtime exposes four MCP tools:

### Tool 1: `list_skills`

**Purpose:** Returns all available skills with metadata for discovery.

```typescript
// MCP Tool Schema
{
  name: "list_skills",
  description: "List all available SkillOS skills with their tier, domain, and status",
  inputSchema: {
    type: "object",
    properties: {
      tier: {
        type: "number",
        description: "Filter by tier (0, 1, 2, 3, 4). Omit for all tiers."
      },
      domain: {
        type: "string",
        description: "Filter by domain keyword (e.g., 'security', 'mobile')"
      }
    }
  }
}

// Output shape
{
  skills: [
    {
      skill_name: "software_architect",
      display_name: "Software Architect",
      version: "1.0.3",
      tier: 0,
      status: "stable",
      domain: "Software Engineering",
      compatible_with: ["security_principles", "frontend_specialist", ...]
    },
    ...
  ],
  total: 11
}
```

### Tool 2: `activate_skill`

**Purpose:** Loads a skill as the active context for the current session.

```typescript
{
  name: "activate_skill",
  description: "Activate a SkillOS skill. The model will operate under that skill's full identity, decision engine, constraint matrix, and quality gates.",
  inputSchema: {
    type: "object",
    properties: {
      skill_name: {
        type: "string",
        description: "The skill_name from list_skills (e.g., 'software_architect')"
      },
      temperature_override: {
        type: "string",
        enum: ["conservative", "balanced", "creative"],
        description: "Override the skill's default temperature mode"
      }
    },
    required: ["skill_name"]
  }
}

// Output: injects the full skill definition into context
// Validation: refuses if any of the 13 SDS components are missing
```

### Tool 3: `get_skill_info`

**Purpose:** Returns structured metadata and the Collaboration Contract for a specific skill — used for planning workflows before activating them.

```typescript
{
  name: "get_skill_info",
  description: "Get detailed information about a skill including its Collaboration Contract (typed I/O interface)",
  inputSchema: {
    type: "object",
    properties: {
      skill_name: { type: "string" }
    },
    required: ["skill_name"]
  }
}

// Output includes:
// - Full YAML metadata (Component 1)
// - Capability boundaries summary (Component 4)
// - Collaboration Contract (Component 12) — the typed I/O spec
// - Validation record status (Component 13)
```

### Tool 4: `chain_skills`

**Purpose:** Executes a multi-skill workflow in sequence, passing context between skills automatically via their Collaboration Contracts.

```typescript
{
  name: "chain_skills",
  description: "Execute a sequence of skills in order, passing the output of each as input to the next",
  inputSchema: {
    type: "object",
    properties: {
      workflow: {
        type: "array",
        items: { type: "string" },
        description: "Ordered list of skill_names to activate in sequence"
      },
      initial_context: {
        type: "string",
        description: "The user's request to feed into the first skill"
      }
    },
    required: ["workflow", "initial_context"]
  }
}

// Example invocation:
// chain_skills({
//   workflow: ["software_architect", "backend_specialist", "database_specialist"],
//   initial_context: "Design a multi-tenant SaaS billing system for African markets"
// })
```

---

## Skill Registry Loader

The MCP server reads skills dynamically from the registry — no hardcoded skill list:

```typescript
// Pseudocode — implementation will use actual MCP SDK APIs

async function loadSkillRegistry(registryPath: string): Promise<SkillMap> {
  const tiers = ['tier-0', 'tier-1', 'tier-2', 'tier-3', 'tier-4'];
  const skills: SkillMap = {};

  for (const tier of tiers) {
    const tierPath = path.join(registryPath, tier);
    const files = await fs.readdir(tierPath);

    for (const file of files) {
      if (file.endsWith('.md') && file !== '.gitkeep') {
        const content = await fs.readFile(path.join(tierPath, file), 'utf-8');
        const skill = parseSkillFile(content); // parses YAML frontmatter + 13 components
        validateSDS(skill);                    // throws if any component missing
        skills[skill.skill_name] = skill;
      }
    }
  }

  return skills;
}
```

---

## Context Handoff Protocol

When `chain_skills` passes context between skills, it uses the **Collaboration Contract** (Component 12) of the *upstream* skill to structure the handoff:

```yaml
# Example: Software Architect → Backend Specialist handoff
handoff_payload:
  source_skill: software_architect
  target_skill: backend_specialist
  output_fields:
    api_contract:
      endpoints: [...]
      auth_mechanism: JWT_RS256
      rate_limiting: token_bucket
    recommended_patterns:
      - CQRS for write-heavy paths
      - Event sourcing for audit trail
    constraints_from_upstream:
      regional_context: [Kenya, Nigeria]
      compliance: [Kenya_DPA, NDPR]
```

The Backend Specialist's Collaboration Contract defines which of these fields it accepts as `required` vs `optional`. Fields the downstream skill doesn't declare in its `input_contract` are discarded. Fields it declares as `required` but are missing trigger a clarification request before proceeding.

---

## Workflow Definition Format

Workflows are stored as YAML files in `workflows/`:

```yaml
# workflows/new-web-app.yaml
name: New Web Application
description: Full stack product build — from architecture to implementation
version: 1.0.0
steps:
  - skill: software_architect
    context_fields_to_pass: [api_contract, recommended_patterns, constraints_from_upstream]

  - skill: backend_specialist
    context_fields_to_pass: [database_recommendations, api_implementation_notes]

  - skill: database_specialist
    context_fields_to_pass: [schema_design, migration_strategy]

  - skill: frontend_specialist
    context_fields_to_pass: [component_architecture, state_management_approach]
```

---

## Session Memory Design

For multi-turn sessions, the runtime maintains a session context object:

```typescript
interface SessionContext {
  session_id: string;
  active_skill: string | null;
  workflow: string[] | null;
  current_step: number;
  accumulated_context: Record<string, unknown>; // grows as skills hand off
  constraints_carried: {                        // persists across all steps
    regional_context: string[];
    compliance: string[];
    temperature_mode: string;
  };
}
```

`constraints_carried` is critical: if the Software Architect detects Kenya DPA and NDPR compliance requirements, those constraints propagate automatically to every downstream skill in the chain — the Backend Specialist, Database Specialist, and Frontend Specialist all receive and enforce them.

---

## Deployment Plan

| Option | Cost | Latency | Recommended For |
|---|---|---|---|
| Railway | ~$5/mo | Low | Development and community launch |
| Fly.io | ~$3/mo | Low (edge) | Production v3.0 launch |
| Vercel Serverless | Free tier | Cold starts | Prototyping only |
| Self-hosted | ~$0 | Depends | Enterprise / privacy-sensitive |

**Recommendation:** Railway for v3.0 launch (simplest deployment pipeline, clear pricing). Migrate to Fly.io for multi-region edge deployment in v3.5 when latency to African/Asian users matters.

---

## Validation: Refusing Incomplete Skills

The runtime enforces the SDS at activation time — not just at PR review time:

```typescript
function validateSDS(skill: ParsedSkill): void {
  const REQUIRED_COMPONENTS = [
    'identity',           // Component 2
    'knowledge_taxonomy', // Component 3
    'capability_boundaries', // Component 4
    'decision_engine',    // Component 5
    'constraint_matrix',  // Component 6
    'failure_mode_library', // Component 7
    'quality_gates',      // Component 8
    'output_templates',   // Component 9
    'ethical_constraints', // Component 10
    'safety_layer',       // Component 11
    'collaboration_contract', // Component 12
    'validation_record',  // Component 13
  ];

  const missing = REQUIRED_COMPONENTS.filter(
    component => !skill.components[component]
  );

  if (missing.length > 0) {
    throw new SDSValidationError(
      `Skill '${skill.skill_name}' is missing SDS components: ${missing.join(', ')}. ` +
      `Cannot activate an incomplete skill.`
    );
  }
}
```

---

## Phase 3 Build Sequence

Once the MCP prerequisites are complete:

```
3.1 ✅ Architecture design (this document)
3.2 ⏳ Initialize TypeScript MCP server project in /runtime/
3.3 ⏳ Implement skill registry loader (dynamic file reading + SDS validation)
3.4 ⏳ Implement list_skills tool
3.5 ⏳ Implement activate_skill tool
3.6 ⏳ Implement get_skill_info tool
3.7 ⏳ Implement chain_skills tool + context handoff protocol
3.8 ⏳ Write 3 example workflow YAML files
3.9 ⏳ Write tests for all tools
3.10 ⏳ Test end-to-end with Claude + at least one other model
3.11 ⏳ Deploy to Railway
3.12 ⏳ Write connection guides (Claude / VS Code / other MCP clients)
```

---

*docs/MCP-ARCHITECTURE.md · SkillOS v3.0 Runtime Design · MIT License*
*Last updated: 2026-07-19*
