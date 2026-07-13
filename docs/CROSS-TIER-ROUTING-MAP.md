# Cross-Tier Routing Map

**How SkillOS skills coordinate and hand off context across tiers.**

This document makes visible the Workflow Layer of SkillOS — the glue that turns individual skills into orchestrated production pipelines.

---

## Quick Navigation

- **Tier 0 → Tier 1:** When architects hand off to domain specialists
- **Tier 1 → Tier 2:** When domain specialists hand off to technology experts
- **Tier 1 → Tier 0:** When domain specialists escalate for architectural review
- **Cross-Tier 1:** Frontend ↔ Backend ↔ DevOps coordination
- **Full Workflow Example:** Multi-skill pipeline from architecture to production

---

## Tier 0 → Tier 1 Routing Paths

### When to Route: Architect → Domain Specialist

The Software Architect proposes high-level design. Implementation requires domain expertise.

---

### Route 1: Architecture → Frontend

**Trigger:** "We need a new dashboard for real-time data visualization. Architect suggests React SPA with WebSocket connection."

**Information Passed:**

```yaml
# From Software Architect (Tier 0)
system_context:
  current_scale: "10K concurrent users"
  target_scale: "100K concurrent users"
  
architecture_decision:
  frontend_approach: "React single-page application"
  real_time_protocol: "WebSocket with fallback to polling"
  state_management_approach: "Centralized store (Redux/Zustand)"
  performance_target: "LCP < 2.5s, FID < 100ms"
  
interface_boundary:
  api_type: "REST with WebSocket for real-time updates"
  payload_structure: "Normalized JSON, max 1MB per message"
  cache_strategy: "Client-side cache with server-side invalidation"
  
constraints:
  browser_support: "Chrome 100+, Firefox 98+, Safari 16+"
  bundle_size_budget: "150KB gzipped"
  team_expertise: "Intermediate React, no GraphQL experience"
```

**Frontend Specialist (Tier 1) Receives:**
- Architecture overview
- Performance targets
- API contract
- Browser/device constraints

**Frontend Specialist (Tier 1) Decides:**
- Exact component architecture
- State management library choice
- Code splitting strategy
- Testing approach

**Handoff Return (Mode 2):**

```yaml
implementation_plan:
  component_hierarchy: |
    App
    ├── DashboardContainer (hooks: useWebSocket, useSelector)
    ├── RealTimeMetricCard (memoized)
    └── ChartLibrary (recharts or d3, evaluated)
    
  state_management:
    library: "Zustand"
    rationale: "Lighter than Redux, simpler than Context. WebSocket updates → store → components"
    
  performance_optimizations:
    - Code split: Dashboard routes → separate chunk
    - Memoization: Chart components only re-render if data actually changes
    - Virtualization: If metrics list > 50 items, use react-window
    
  testing_strategy:
    unit: "Component rendering with mock WebSocket"
    integration: "Full dashboard with mock server"
    e2e: "Real WebSocket connection in staging"
    
  open_questions_for_architect:
    - "Should we cache dashboard state between page reloads?"
    - "What's the failover if WebSocket drops for >5 seconds?"
```

**Verification:** Frontend Specialist output includes component props interface, testing strategy, and performance metrics.

---

### Route 2: Architecture → Backend

**Trigger:** "Service needs to handle 10K requests per second. Architect suggests PostgreSQL with Redis caching."

**Information Passed:**

```yaml
# From Software Architect (Tier 0)
system_context:
  current_load: "1K req/sec, 100ms p99 latency"
  target_load: "10K req/sec, <50ms p99 latency"
  
technology_decision:
  database: "PostgreSQL with read replicas"
  caching_layer: "Redis (distributed cache)"
  async_work: "Kafka for event streaming"
  
constraints:
  consistency_model: "Strong consistency for user data, eventual for analytics"
  availability_requirement: "99.99% uptime"
  data_retention: "Hot data: 30 days, Archive: 7 years"
  
scaling_phases:
  phase_1: "Scale to 5K req/sec with replicas"
  phase_2: "Sharding if needed at 10K req/sec"
  phase_3: "Multi-region if needed at 50K+ req/sec"
```

**Backend Specialist (Tier 1) Receives:**
- Load requirements
- Technology choices
- Consistency guarantees
- Scaling roadmap

**Backend Specialist (Tier 1) Decides:**
- API endpoint design
- Request validation rules
- Error handling patterns
- Database schema design (routes to Database Specialist if complex)

**Handoff Return:**

```yaml
api_design:
  endpoints: |
    GET /api/v1/metrics - fetch paginated metrics
    POST /api/v1/metrics - create new metric
    DELETE /api/v1/metrics/{id} - soft delete
    
  request_validation: "zod schema for all inputs"
  error_handling: "Typed error codes, retry-safe responses"
  
database_plan:
  schema: "Normalized, 3NF, audit trail tables included"
  indexes: "On (user_id, created_at) and (metric_id, value)"
  caching_keys: "metric:${id}, user_metrics:${user_id}:${page}"
  
performance_targets:
  p50: "20ms"
  p95: "40ms"
  p99: "50ms"
  
testing_strategy:
  load_test: "k6 script simulating 10K req/sec"
  chaos_test: "Database failover scenarios"
```

---

### Route 3: Architecture → DevOps

**Trigger:** "Multi-region with disaster recovery. Architect suggests Kubernetes + managed database."

**Information Passed:**

```yaml
# From Software Architect (Tier 0)
deployment_architecture:
  runtime: "Kubernetes (self-managed or managed service)"
  regions: "us-east-1, eu-west-1, ap-southeast-1"
  failover_strategy: "Active-active read replicas"
  disaster_recovery:
    rto: "15 minutes"
    rpo: "5 minutes of data"
    
infrastructure_decisions:
  database: "RDS PostgreSQL with automated failover"
  cache: "ElastiCache Redis with cluster mode"
  storage: "S3 with cross-region replication"
  
scaling_requirements:
  auto_scaling_metric: "CPU > 70% → scale up"
  min_replicas: 3
  max_replicas: 100
  
monitoring_requirements:
  slos:
    - "99.99% availability"
    - "< 100ms p99 latency"
  key_metrics: "Request rate, error rate, latency, database connection pool"
```

**DevOps Specialist (Tier 1) Receives:**
- Infrastructure topology
- Failover requirements
- SLO targets
- Scaling bounds

**DevOps Specialist (Tier 1) Decides:**
- Container orchestration specifics
- CI/CD pipeline design
- Observability setup
- Security hardening

---

## Tier 1 → Tier 2 Routing Paths

### When to Route: Domain Specialist → Technology Expert

When a Tier 1 specialist needs specific technology expertise.

---

### Route 1: Frontend Specialist → React Expert

**Trigger:** Frontend Specialist says: "Build a high-performance data table with 10K rows, real-time updates, sorting, filtering."

**Information Passed:**

```yaml
# From Frontend Specialist (Tier 1)
requirements:
  component_type: "data table"
  dataset_size: "10K rows, growing to 100K"
  operations: ["sort", "filter", "search", "real-time updates"]
  
performance_targets:
  render_time: "< 16ms per frame (60fps)"
  initial_load: "LCP < 2.5s"
  interaction_delay: "< 100ms"
  
accessibility_requirements:
  wcag_level: "AA"
  keyboard_navigation: true
  screen_reader_support: true
  
state_management:
    strategy: "Unknown - need React expert"
    data_source: "API with WebSocket updates"
```

**React Expert (Tier 2) Receives:**
- Functional requirements
- Performance constraints
- Accessibility needs
- Data source characteristics

**React Expert (Tier 2) Decides:**
- Virtualization library (react-window vs. react-virtualized)
- State management approach (Zustand vs. Redux vs. TanStack Query)
- Memoization strategy
- Testing approach

**Handoff Return:**

```yaml
implementation:
  component_structure: |
    DataTable (memoized)
    ├── TableHeader (memoized)
    ├── TableBody (virtualized with react-window)
    │  └── TableRow (memoized, keyed by id)
    └── TableFooter (pagination)
    
  state_management:
    library: "TanStack Query (for server state) + Zustand (for UI state)"
    rationale: "Separates concerns: Query handles caching/sync, Zustand handles sort/filter UI state"
    
  performance_optimizations:
    - Virtualization: Only render 20 visible rows at a time
    - Memoization: TableRow only re-renders if data changed
    - Pagination: Load 500 rows at a time, cache previous pages
    
  testing:
    unit: "TableRow component with mock data"
    integration: "DataTable with mock API"
    e2e: "Full table with real API in staging"
    performance: "Lighthouse audit for Web Vitals"
```

---

### Route 2: Backend Specialist → Node.js Expert

**Trigger:** Backend Specialist says: "Build REST API with async job processing and real-time notifications."

**Information Passed:**

```yaml
# From Backend Specialist (Tier 1)
requirements:
  api_style: "REST with WebSocket for real-time"
  operations: ["CRUD", "async jobs", "notifications"]
  
performance_targets:
  response_time: "p99 < 50ms"
  concurrent_connections: "10K"
  job_throughput: "1K jobs/sec"
  
scaling:
  estimated_load: "10K req/sec"
  deployment_target: "Kubernetes"
  
technology_decisions:
  runtime: "Node.js"
  database: "PostgreSQL"
  async_queue: "Bull/RabbitMQ"
  real_time: "Socket.io"
```

**Node.js Expert (Tier 2) Receives:**
- API specification
- Performance targets
- Load characteristics
- Technology stack decisions

**Node.js Expert (Tier 2) Decides:**
- Framework choice (Express, Fastify, Hono)
- Middleware stack
- Error handling patterns
- Async job implementation details

---

### Route 3: Database Specialist → PostgreSQL Expert

**Trigger:** Backend Specialist says: "Design schema for e-commerce: users, products, orders, with complex reporting queries."

**Information Passed:**

```yaml
# From Backend Specialist (Tier 1)
requirements:
  entities: ["user", "product", "order", "inventory"]
  queries: ["user history", "product search", "order analytics"]
  reporting: "Real-time dashboard with aggregations"
  
scale:
  total_records: "100M rows (mostly order history)"
  write_throughput: "10K writes/sec"
  read_throughput: "100K reads/sec"
  
constraints:
  consistency: "Strong for transactions, eventual for analytics"
  retention: "Hot: 1 year, Archive: 7 years"
  backup_rpo: "5 minutes"
```

**PostgreSQL Expert (Tier 2) Receives:**
- Entity relationships
- Query patterns
- Scale targets
- Consistency requirements

**PostgreSQL Expert (Tier 2) Decides:**
- Normalization level (3NF vs. denormalization for reporting)
- Partitioning strategy
- Index design
- Replication setup

---

## Tier 1 → Tier 0 Escalation Paths

### When Domain Specialist Needs Architectural Guidance

**Scenario 1:** Frontend Specialist says "The data table needs to show 100K rows with full-text search. Performance budget is tight."

**Escalation Question:** "Is 100K rows on a single page the right architecture, or should we paginate/virtualize? That's an architectural decision."

**Escalation to Architect:**

```yaml
question: "Architectural trade-off needed"
problem_statement: |
  Current approach: Virtual scrolling + client-side filtering on 100K rows
  Trade-off:
  - Pro: No pagination, searchable everywhere
  - Con: Huge client bundle, network payload massive
  - Alternative: Server-side search with pagination (multiple round trips, better UX)
  
ask_architect: |
  Should we optimize for:
  1. Single request complexity (load all data once)
  2. Multiple small requests (better perceived performance)
  3. A hybrid approach (load first 1K, lazy-load as user scrolls)
```

**Architect's Response:**

```yaml
decision: "Hybrid approach"
reasoning: |
  - Load first 1K rows immediately (small bundle, fast LCP)
  - Search on server (100ms query, returned instantly)
  - Lazy-load more rows as user scrolls (virtualization)
  
implementation_plan:
  api_endpoints:
    - GET /search?q=text&limit=50&offset=0 → First 50 results
    - GET /search/count?q=text → Total matches (for pagination UI)
  
  frontend:
    - Initial render: First 50 items
    - As user scrolls: Fetch next 50
    - Search input: Debounce 300ms, fetch new results
```

---

## Cross-Tier 1 Routing (Lateral Coordination)

### When Frontend, Backend, and DevOps Collaborate

**Workflow Example: "Let's build real-time notifications"**

```
┌─────────────────────────────────────────────────────────────┐
│ Software Architect (Tier 0)                                 │
│ Decision: Real-time notifications via WebSocket + message   │
│ queue for reliability                                        │
└────────────┬────────────────────────────────────┬───────────┘
             │                                    │
             ▼                                    ▼
    ┌──────────────────────┐           ┌──────────────────────┐
    │ Frontend Specialist  │           │ Backend Specialist   │
    │ (Tier 1)             │           │ (Tier 1)             │
    │                      │           │                      │
    │ Decision:            │           │ Decision:            │
    │ - WebSocket client   │           │ - Kafka for queuing  │
    │ - Notification UI    │           │ - Event publisher    │
    │ - Offline queue      │           │ - Retry logic        │
    └──────────┬───────────┘           └──────────┬───────────┘
               │ needs React →                    │ needs Node.js →
               │ specific patterns                │ specific patterns
               ▼                                  ▼
    ┌──────────────────────┐           ┌──────────────────────┐
    │ React Expert         │           │ Node.js Expert       │
    │ (Tier 2)             │           │ (Tier 2)             │
    │                      │           │                      │
    │ - useWebSocket hook  │           │ - Express middleware │
    │ - Notification bell  │           │ - Socket.io setup    │
    │ - Message dedup      │           │ - Kafka integration  │
    └──────────────────────┘           └──────────────────────┘
               │                              │
               └──────────────┬───────────────┘
                              ▼
                   ┌──────────────────────┐
                   │ DevOps Specialist    │
                   │ (Tier 1)             │
                   │                      │
                   │ - K8s deployment     │
                   │ - Message queue      │
                   │ - Monitoring alerts  │
                   └──────────────────────┘
```

**Coordination Points:**

```yaml
frontend_backend_contract:
  api_endpoint: "POST /api/v1/subscribe"
  payload: |
    {
      "event_types": ["order_created", "payment_received"],
      "user_id": "user_123",
      "preferred_delivery": "websocket"
    }
  
  response: |
    {
      "subscription_id": "sub_456",
      "websocket_url": "wss://api.example.com/ws/sub_456",
      "reconnect_interval": 5000
    }
  
  websocket_message_format:
    event:
      type: "order_created"
      timestamp: "2026-07-13T21:00:00Z"
      payload:
        order_id: "order_789"
        total: 99.99
    
frontend_devops_contract:
  deployment:
    - React app loads Socket.io client from /socket.io/socket.js
    - Nginx routes /socket.io/* to Node.js backend
    - Sticky sessions: user connections stay on same backend pod
    
backend_devops_contract:
  infrastructure:
    - Kafka cluster for message distribution
    - Redis for in-flight message cache
    - Connection pooling to database
    - Metrics: active connections, message throughput
    
devops_monitoring:
  slos:
    - 99.99% WebSocket availability
    - Message delivery < 100ms
    - Connection establishment < 1s
  
  alerts:
    - If active_connections drops > 50%
    - If message latency > 500ms
    - If Kafka lag > 60 seconds
```

---

## Full Workflow Example: E-Commerce Platform

**Goal:** Build new cart and checkout flow for 100K concurrent users.

---

### Phase 1: Architect (Tier 0)

**High-Level Design:**

```yaml
system_design:
  frontend:
    - React SPA
    - Client-side cart state management
    - Real-time inventory sync
  
  backend:
    - Node.js API servers
    - Redis for cart state cache
    - PostgreSQL for transactions
  
  async_work:
    - Order processing jobs
    - Email notifications
  
  infrastructure:
    - Kubernetes multi-region
    - CDN for static assets
    - Message queue for reliability
  
  performance_targets:
    - Add to cart: < 100ms
    - Checkout page load: < 2.5s LCP
    - Order confirmation: < 5s
```

**Handoff to:** Frontend, Backend, DevOps specialists

---

### Phase 2: Domain Specialists (Tier 1)

#### Frontend Specialist

```yaml
responsibilities:
  - Cart component UI
  - Checkout form state
  - Real-time inventory status
  - Offline support
  
escalations_to_tier_2:
  - React Expert: Complex form state with async validation
  - Performance Engineer: Bundle size optimization
```

#### Backend Specialist

```yaml
responsibilities:
  - Cart API endpoints
  - Inventory API
  - Order creation workflow
  - Payment integration points
  
escalations_to_tier_2:
  - Node.js Expert: Job queue setup
  - Database Expert: Transaction design
```

#### DevOps Specialist

```yaml
responsibilities:
  - Kubernetes deployment
  - Auto-scaling policy
  - CDN setup
  - Monitoring and alerts
  
escalations_to_tier_2:
  - Kubernetes Expert: Complex failover scenarios
```

---

### Phase 3: Technology Experts (Tier 2)

#### React Expert

**Building:** Cart state management, validation, error handling

```yaml
implementation:
  component_architecture:
    Cart (Zustand store)
    ├── CartSummary
    ├── CartItems (memoized rows)
    └── CheckoutForm (form library: React Hook Form)
  
  state_management:
    library: "Zustand + TanStack Query"
    stores:
      - cart: { items, quantities, total }
      - inventory: { sku → available_qty }
      - checkout: { form_state, errors, loading }
  
  api_integration:
    - Query: GET /inventory/sku/{sku}
    - Mutation: POST /cart/items
    - Mutation: POST /orders (checkout)
  
  performance:
    - Debounce inventory checks: 500ms
    - Memoize CartItem to prevent re-renders
    - Code split: CheckoutModal loaded on demand
```

#### Node.js Expert

**Building:** Cart API, inventory sync, order processing

```yaml
implementation:
  api_endpoints:
    - POST /cart/items (add to cart)
    - PATCH /cart/items/{id} (update quantity)
    - DELETE /cart/items/{id} (remove)
    - POST /orders (create order)
    - GET /inventory/check (bulk availability)
  
  middleware:
    - Authentication
    - Input validation (zod)
    - Rate limiting (per user: 100 req/min)
    - Error handler (typed errors)
  
  business_logic:
    - Reserve inventory on checkout
    - Calculate tax and shipping
    - Trigger order processing job
    - Send confirmation email
  
  async_jobs:
    - Order processing (Kafka consumer)
    - Email notifications (Bull queue)
    - Inventory reconciliation (cron)
  
  performance:
    - Redis cache for inventory (TTL: 30s)
    - Database connection pooling (pool_size: 20)
    - Batch inventory checks
```

---

### Phase 4: Delivery

**Deployed features:**
- ✅ Add to cart (100ms)
- ✅ Real-time inventory (WebSocket sync every 5s)
- ✅ Checkout form validation
- ✅ Multi-region redundancy
- ✅ Email confirmations within 2s of order

---

## How to Use This Map

### For Implementers

1. Start with your requirement
2. Find the matching route above
3. Follow the "Information Passed" and "Handoff Return" structures
4. Use the **Collaboration Contract** in each skill's SDS as your input/output template

### For Skill Contributors

Add a routing section to your skill's Component 12 (Collaboration Contract):

```markdown
## Routing Guidance (Component 12 Extension)

**When I route to you, I pass:**
- [List 5-7 key pieces of context]

**When you route back to me, include:**
- [List 5-7 key deliverables]

**When I escalate to Tier 0, ask about:**
- [List 2-3 architectural trade-offs]

**When I coordinate laterally (same tier), sync on:**
- [List 2-3 handoff points]
```

### For Architecture Review

Use this map to verify skills are routing correctly:

- ✓ No skill tries to do another skill's job
- ✓ Handoff contracts match the defined paths
- ✓ Tier 0 focuses on trade-offs, not implementation
- ✓ Tier 1 focuses on domain patterns, not technology details
- ✓ Tier 2 focuses on technology, not business logic

---

## Extending This Map

As new skills are added:

1. **Tier 0 additions** → update "Tier 0 → Tier 1" section
2. **Tier 1 additions** → add new Tier 1 → Tier 2 routes
3. **Tier 2 additions** → expand existing Tier 1 → Tier 2 routes
4. **Cross-cuts** (e.g., Security) → add new routing sections

Each addition must include:
- When to route (trigger)
- Information passed (input contract)
- Information returned (output contract)
- A real-world example

---

## Design Principles

✅ **Explicit is better than implicit.** Every handoff is named and documented.

✅ **Contracts not chaos.** Each route defines what information flows in and out.

✅ **Verify by reading.** This document should be readable by a new contributor without asking questions.

✅ **Scale by copy.** Adding a new skill means copying a template, filling in domain details, not rewriting.

✅ **Audit by inspection.** Reviewers can check: "Does this skill follow its routing contract?"

---

## Related Documents

- `SKILL-DEFINITION-STANDARD.md` — Component 12 (Collaboration Contract) details
- `SKILL-CREATOR.md` — Phase 7 (Routing) for generating new skills
- `CONTRIBUTING.md` — Checklist for new skill submissions (must define routing)
- `../registry/` — Real skills showing this routing in action

---

*CROSS-TIER-ROUTING-MAP.md · SkillOS · Phase 1 Refinement · MIT License · Owned by the world*
