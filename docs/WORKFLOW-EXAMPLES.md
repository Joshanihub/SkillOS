# SkillOS — Workflow Examples
## Three complete multi-skill workflows demonstrating the Cross-Tier Routing Map in action

These examples show how skills collaborate to produce output no single skill
could produce alone. Each workflow is a sequence of skill activations where
the output of one skill becomes the structured input of the next.

For the typed handoff fields referenced here, see `docs/CROSS-TIER-ROUTING-MAP.md`.
For the MCP runtime that will execute these automatically, see the v3.0 roadmap.

---

## Workflow 1 — Full Stack SaaS Product Build

**Scenario:** A team is building a B2B SaaS product — a project management tool
for construction companies. They have requirements and need to go from zero to
a production architecture, frontend design, and initial implementation.

**Skills activated:** Software Architect → Security Principles → Frontend Specialist
→ Backend Specialist → Database Specialist → React Expert → Node.js Expert
→ PostgreSQL Specialist

---

### Step 1 — Software Architect (Tier 0)

**Input provided by user:**
```
We're building a B2B SaaS for construction project management.
~500 initial users, expecting 10K in year one. Teams will track
tasks, timelines, documents, and budgets. Multi-tenant. Mobile
access required. Regulatory: construction industry in Kenya, EU clients likely.
```

**Software Architect output (abbreviated):**
```yaml
architecture:
  pattern: Modular monolith (scale to microservices at 50K users if needed)
  api_style: REST + WebSocket for real-time updates
  auth: Multi-tenant JWT with org-scoped permissions
  data_isolation: Row-level security per organization
  file_storage: Object storage (S3-compatible, provider-agnostic)
  search: PostgreSQL full-text initially; Elasticsearch at scale

module_boundaries:
  - auth_service: login, JWT, org management
  - project_service: projects, tasks, timelines
  - document_service: file upload, versioning, access control
  - budget_service: cost tracking, approval workflows
  - notification_service: in-app, email, push

api_contracts:
  - POST /projects → creates project, returns project_id
  - GET /projects/:id/tasks → paginated task list
  - WS /projects/:id/updates → real-time task updates
  - POST /documents/upload → presigned URL flow

performance_budget:
  api_p99: 200ms
  file_upload: streaming (no memory buffering)
  real_time_lag: <500ms

compliance_flags:
  - Kenya Data Protection Act 2019: data residency preference for Kenyan clients
  - GDPR Article 17: right to erasure must be implemented for EU clients
  - File retention: construction documents may have legal hold requirements

routing:
  to_frontend_specialist:
    rendering: SSR for initial load (SEO not critical but fast first paint is)
    real_time: WebSocket for task updates
    mobile: PWA or React Native evaluation needed
  to_backend_specialist:
    api_contracts: [listed above]
    auth_approach: JWT with org-scoped claims
    file_strategy: presigned URLs, not proxy uploads
  to_database_specialist:
    entities: [Organization, User, Project, Task, Document, Budget, Comment]
    access_patterns: [by org, by project, by user, timeline queries]
    compliance: row-level security required
  to_security_principles:
    multi_tenant_isolation: critical
    file_access_control: documents are sensitive
    new_threat_surface: WebSocket connections
```

---

### Step 2 — Security Principles (Tier 0, parallel with Step 1)

**Receives:** Architecture from Software Architect

**Security Principles output (abbreviated):**
```yaml
threat_model:
  assets:
    - Tenant data isolation (highest priority — breach affects all clients)
    - Construction documents (contain sensitive commercial information)
    - Budget data (financial information)
  threat_actors:
    - Malicious tenant trying to access another tenant's data
    - External attacker targeting file storage
    - Insider threat (disgruntled employee)
  attack_vectors:
    - JWT tenant_id manipulation if not validated server-side
    - Insecure direct object reference on document endpoints
    - WebSocket connection hijacking
    - Mass assignment on project update endpoints

mitigations:
  - All queries include WHERE org_id = :claiming_org_id (never trust URL params alone)
  - Row-level security in PostgreSQL as defense in depth
  - Presigned URLs expire in 15 minutes; never serve files through API proxy
  - WebSocket auth validated on connection and re-validated on reconnect
  - Rate limiting on all auth endpoints: 5 attempts per IP per minute

compliance_controls:
  GDPR_erasure: soft-delete with 30-day hard-delete job; document legal holds exempt
  Kenya_DPA: document where PII is stored; implement data subject access request flow
```

---

### Step 3 — Frontend Specialist (Tier 1)

**Receives:** Architecture + Security handoffs

**Frontend Specialist output (abbreviated):**
```yaml
component_hierarchy:
  - AppShell (auth, navigation, org context)
    - ProjectDashboard
      - TaskBoard (real-time WebSocket consumer)
        - TaskCard
        - TaskDetail
      - Timeline
      - DocumentPanel
    - BudgetTracker
    - Settings

state_strategy:
  server_state: React Query (TanStack Query) — API data
  real_time_state: WebSocket connection managed in context
  ui_state: useState/useReducer locally
  auth_state: Context with JWT claims

rendering_approach:
  strategy: Next.js App Router with SSR
  why: Fast initial paint; SEO not critical but time-to-interactive is
  real_time: Client components for WebSocket consumers only
  documents: Lazy loaded; not in initial bundle

accessibility:
  - WCAG 2.2 AA throughout
  - Construction site context: may be used on mobile with gloves
    → larger touch targets (44px minimum), high contrast mode support
  - Keyboard navigation for all task management operations

mobile_strategy:
  approach: Responsive PWA first; evaluate React Native at 5K users
  reasoning: PWA covers 80% of mobile use cases; native adds significant complexity

routing:
  to_react_expert:
    component_hierarchy: [above]
    state_strategy: TanStack Query + WebSocket context
    performance_requirements: TaskBoard may render 500+ cards
    accessibility_requirements: WCAG 2.2 AA; large touch targets
    framework_context: Next.js 15 App Router
```

---

### Step 4 — React Expert (Tier 2)

**Receives:** Frontend Specialist handoff

**React Expert output:** Production TaskCard component, WebSocket hook,
TanStack Query setup, virtualization for large task lists, full
accessibility implementation, test cases.

*(Full code output omitted for brevity — this is where the skill produces
the actual implementation.)*

---

### Workflow Complete

The user now has:
- Architecture decision with compliance considerations for Kenya + EU
- Security threat model with specific mitigations
- Frontend component hierarchy with accessibility notes for construction context
- Production React components

**Total skills activated:** 4 (abbreviated example — full workflow uses 7)
**Context preserved across all handoffs via typed YAML fields**

---

---

## Workflow 2 — API Design and Security Review

**Scenario:** A financial services company needs to expose their core banking
data via a REST API for partner integrations. Security and compliance are
the primary constraints.

**Skills activated:** Software Architect → Security Principles → Backend Specialist
→ Node.js Expert → Security Principles (final review)

---

### Step 1 — Software Architect

**Input:**
```
We need a partner-facing REST API for our core banking platform.
Partners will access account balances, transaction history, and
initiate transfers. ISO 27001 certified environment. Jurisdiction: Nigeria.
~50 partner integrations at launch.
```

**Architect output (key decisions):**
```yaml
api_style: REST with OpenAPI 3.1 spec
auth: OAuth 2.0 with client credentials flow (partner-to-server)
rate_limiting: Per partner, per endpoint, per minute
versioning: URL versioning (/v1/, /v2/) — no breaking changes within version
data_access: Read-only endpoints for balance/history; write endpoints for transfers only
audit_log: Every API call logged with partner_id, timestamp, endpoint, response_code
sandbox: Mandatory sandbox environment before production access
compliance_flags:
  - Nigeria NDPR: data processing agreement required with each partner
  - CBN Open Banking Framework: Nigeria-specific partner onboarding requirements
  - ISO 27001: all endpoints must be covered in scope
```

---

### Step 2 — Security Principles (pre-implementation review)

**Receives:** Architecture from Step 1

**Key security output:**
```yaml
threat_model:
  critical_threats:
    - Partner credential compromise (treat as highest priority)
    - Replay attacks on transfer endpoints
    - Data exfiltration through excessive data access
  mitigations:
    - Client credentials: rotate every 90 days; immediate revocation on compromise
    - Transfer endpoints: idempotency keys required; 30-second replay window
    - Pagination enforced on all list endpoints (max 100 per page); no bulk export
    - IP allowlisting per partner as additional control
    - All transfer requests: dual-check (request + confirm pattern)
compliance_mapping:
  ISO_27001_A9: Access control — OAuth 2.0 satisfies
  ISO_27001_A12: Operations security — audit log satisfies
  NDPR_Article_24: Data processing agreement template required
  CBN_OpenBanking: Partner registration flow required before API access
```

---

### Step 3 — Backend Specialist → Node.js Expert

**Receives:** Architecture + Security handoffs

**Backend output:** API design with middleware stack, rate limiting strategy,
audit logging pattern, error response format.

**Node.js Expert output:** Production Express/Fastify implementation with
OAuth 2.0 middleware, rate limiting, audit logging, idempotency keys,
pagination enforcement, OpenAPI schema validation.

---

### Step 4 — Security Principles (final review)

**Receives:** Completed implementation

**Final review output:** Sign-off on implementation, any remaining gaps,
compliance checklist confirmation.

---

---

## Workflow 3 — Legacy System Security Audit

**Scenario:** An e-commerce company has a 5-year-old platform and needs
a security assessment before a major traffic campaign.

**Skills activated:** Security Principles → Backend Specialist (remediation)
→ DevOps Specialist (infrastructure hardening) → Security Principles (sign-off)

---

### Step 1 — Security Principles (assessment)

**Input:**
```
Audit our e-commerce platform before Black Friday.
Node.js backend, PostgreSQL database, deployed on AWS.
Payment processing via Stripe. User base: 200K accounts.
Last security review: 18 months ago.
```

**Security Principles output:**
```yaml
threat_model:
  assets:
    - 200K user accounts with PII (name, email, address, order history)
    - Payment tokens (Stripe) — not full card data but still sensitive
    - Admin access (high-value target)
  priority_findings:
    - Dependency audit required: 18-month gap guarantees CVEs
    - Session management: needs review at 200K user scale
    - Admin endpoints: likely undertested given growth timeline
    - PostgreSQL: check for SQL injection in any raw queries added during growth
  compliance_flags:
    - GDPR (EU customers likely): right to erasure, data breach notification 72h
    - PCI DSS SAQ-A: Stripe integration must maintain SAQ-A compliance
    - OWASP Top 10 2021: map all findings to OWASP categories

priority_remediations:
  critical:
    - npm audit --fix: run immediately; patch all high/critical CVEs before campaign
    - Rate limiting on auth endpoints: prevent credential stuffing at campaign scale
  high:
    - Session invalidation on password change: common gap in growth-phase apps
    - Admin 2FA: enforce for all admin accounts before high-traffic period
  medium:
    - Content Security Policy headers: missing or permissive in 5-year-old apps
    - Database connection pool limits: may cause instability under campaign load
```

---

### Step 2 — Backend Specialist (remediation)

**Receives:** Security findings

**Backend Specialist output:** Specific code patches for each critical and
high finding — rate limiting middleware, session invalidation on password
change, input validation improvements.

---

### Step 3 — DevOps Specialist (infrastructure hardening)

**Receives:** Security findings + Backend remediation plan

**DevOps Specialist output:** AWS security group review, WAF configuration
for the campaign, auto-scaling limits to prevent cost explosion, CloudTrail
audit logging, backup verification before the campaign.

---

### Step 4 — Security Principles (campaign clearance)

**Receives:** Completed remediation

**Output:** Final clearance or remaining blockers. Campaign go/no-go recommendation.

---

---

## How to Compose Your Own Workflow

Every workflow follows this pattern:

```
1. Identify the primary domain (usually Tier 0 or Tier 1)
2. Activate the foundational skill first — it produces the architecture/plan
3. Route to specialists using the handoff fields from CROSS-TIER-ROUTING-MAP.md
4. Each specialist receives only what it needs — not the full conversation
5. Security Principles reviews at the start and end of any security-sensitive workflow
```

**Rule of thumb:** If a task touches more than one domain, it is a workflow.
Single-domain tasks activate a single skill.

For the full list of routing paths and typed handoff fields, see
`docs/CROSS-TIER-ROUTING-MAP.md`.

---

*WORKFLOW-EXAMPLES.md · SkillOS docs/ · MIT License*
