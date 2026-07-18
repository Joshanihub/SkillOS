# SkillOS — Industry Verticals
## How current skills serve specific industries, and what premium skills each vertical needs

This document maps the base registry skills to industry verticals and identifies
the highest-value domain-specific skills for each industry. These industry-specific
skills represent the premium tier of the marketplace (v5.0) — specialized expertise
that general skills cannot provide.

The base skills (Software Architect, Frontend Specialist, React Expert, Backend
Specialist, Database Specialist, DevOps Specialist) apply to all software-building
industries. This document covers what those industries need **beyond** the base set.

---

## How to Read This Document

Each vertical section contains:

**Base skills that apply** — which current registry skills serve this industry
**Critical compliance context** — regulatory requirements that affect all skills used in this vertical
**Domain-specific skills needed** — skills the base registry cannot cover
**Priority** — how urgently each domain skill is needed (HIGH/MEDIUM/LOW)
**Estimated complexity** — how hard the skill would be to generate and validate

---

## Software Engineering (General)

*The core vertical. All base skills serve this vertical directly.*

**Base skills that apply:** All of them.

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Security Principles (Tier 0) | HIGH | Every software project needs this — currently missing from registry |
| Systems Thinking (Tier 0) | HIGH | Complexity management, trade-off analysis at scale |
| TypeScript Specialist (Tier 2) | HIGH | Most modern JavaScript projects use TypeScript |
| Next.js Expert (Tier 2) | HIGH | Most popular React framework |
| Node.js Expert (Tier 2) | HIGH | Dominant backend for JavaScript teams |
| PostgreSQL Specialist (Tier 2) | MEDIUM | Most common open-source database |
| Auth Specialist (Tier 3) | MEDIUM | OAuth2, OIDC, FIDO2 patterns needed by all projects |
| Testing Specialist (Tier 3) | MEDIUM | Currently only Tier 2 has testing guidance |
| CI/CD Specialist (Tier 3) | MEDIUM | GitHub Actions, deployment pipelines |
| Observability Specialist (Tier 3) | MEDIUM | Metrics, logging, alerting patterns |

---

## Healthcare

**Critical compliance context:**
- HIPAA (US): PHI handling, Business Associate Agreements, audit logs, breach notification
- NHS DSP Toolkit (UK): data security and protection standards
- Kenya Health Informatics standards
- HL7 FHIR: standard for health data interoperability
- Every skill used in healthcare MUST apply Conservative temperature mode

**Base skills that apply with modifications:**
- Software Architect — must flag HIPAA PHI classification for every data field
- Database Specialist — must recommend field-level encryption for PHI
- DevOps Specialist — must include HIPAA-compliant logging (no PHI in logs)

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| HIPAA Compliance Specialist | HIGH | PHI handling rules affect every architectural decision |
| Clinical Documentation Specialist | HIGH | Medical record structure, ICD codes, SNOMED CT |
| HL7 FHIR Specialist | HIGH | Interoperability standard for all health data exchange |
| Medical Terminology Specialist | MEDIUM | Correct terminology in AI-generated clinical content |
| Patient Safety Auditor | MEDIUM | Risk classification for health software (FDA, CE marking) |
| Telemedicine UX Specialist | MEDIUM | Accessibility for elderly and disabled patients |

**Premium tier potential:** HIGH. HIPAA compliance alone justifies enterprise pricing.

---

## Finance and Fintech

**Critical compliance context:**
- PCI DSS: payment card data handling
- SOX (US public companies): financial reporting controls
- GDPR Article 22: automated decision-making restrictions (affects AI credit scoring)
- Nigeria CBN Open Banking Framework
- Kenya Central Bank digital finance regulations
- MiFID II (EU): financial instrument reporting
- DORA (EU): digital operational resilience
- All financial systems: Conservative temperature mode mandatory

**Base skills that apply with modifications:**
- Backend Specialist — must include idempotency patterns for financial transactions
- Database Specialist — must recommend immutable audit logs for all financial records
- Security Principles — must include fraud detection patterns

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Financial Compliance Specialist | HIGH | PCI DSS, SOX, MiFID II — varies by jurisdiction |
| Payment Integration Specialist | HIGH | Stripe, M-Pesa, Paystack, Flutterwave integration patterns |
| Risk and Fraud Detection Specialist | HIGH | ML-based fraud patterns, rule engines |
| Open Banking Specialist | MEDIUM | API standards for financial data sharing |
| Algorithmic Trading Specialist | MEDIUM | High-frequency, low-latency system patterns |
| Financial Reporting Specialist | MEDIUM | Accounting standards, regulatory reporting |

**Premium tier potential:** VERY HIGH. Financial compliance is expensive to get wrong.
African market: M-Pesa integration specialist would be unique and valuable.

---

## Legal

**Critical compliance context:**
- Legal Professional Privilege: AI-assisted legal work must preserve privilege
- Bar Association rules vary by jurisdiction (AI disclosure requirements differ)
- GDPR: legal documents frequently contain special category data
- Evidence standards differ by jurisdiction
- Conservative temperature mode: mistakes in legal documents have serious consequences

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Contract Review Specialist | HIGH | Clause analysis, risk flagging, redlining patterns |
| Legal Research Specialist | HIGH | Case law synthesis, jurisdiction-aware research |
| Legal Document Drafter | HIGH | Jurisdiction-specific document structures and language |
| Compliance Monitoring Specialist | MEDIUM | Regulatory change tracking, policy gap analysis |
| IP and Patent Specialist | MEDIUM | Patent claim structure, prior art analysis |
| Litigation Support Specialist | MEDIUM | Discovery, deposition prep, evidence organization |

**Premium tier potential:** HIGH. Legal errors are costly. Bill-by-hour model means
efficiency tools have clear ROI.

---

## Education

**Critical compliance context:**
- FERPA (US): student educational records privacy
- COPPA (US): children under 13 online privacy
- GDPR Article 8: children's consent (under 16 in most EU states)
- Accessibility: educational tools must meet WCAG 2.2 AA — often WCAG AAA
- Academic integrity: AI assistance disclosure requirements vary by institution

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Curriculum Design Specialist | HIGH | Learning objectives, assessment alignment, sequencing |
| Accessibility Learning Specialist | HIGH | Universal Design for Learning (UDL) principles |
| Assessment Design Specialist | MEDIUM | Formative, summative, rubric design |
| Learning Path Optimizer | MEDIUM | Adaptive learning sequences, prerequisite mapping |
| Academic Writing Specialist | MEDIUM | Citation formats, academic register, integrity guidelines |

**Premium tier potential:** MEDIUM. EdTech is a large market but pricing pressure is high.

---

## Government and Public Sector

**Critical compliance context:**
- WCAG 2.2 AA minimum (often AAA required by law for government sites)
- Open Government Data standards
- Procurement regulations vary by country — detailed audit trails required
- Accessibility Law varies: Section 508 (US), EN 301 549 (EU), equivalent in other jurisdictions
- Security clearance implications for some work
- Public records requirements

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Government Accessibility Specialist | HIGH | Legal requirements stricter than private sector |
| Policy Analysis Specialist | HIGH | Policy drafting, impact assessment, stakeholder mapping |
| Public Procurement Specialist | MEDIUM | Tender documents, evaluation criteria, compliance |
| Open Data Specialist | MEDIUM | Data publishing standards, linked data, metadata |
| Regulatory Drafting Specialist | MEDIUM | Legal language, cross-reference management |

**Premium tier potential:** MEDIUM-HIGH. Government contracts are large but slow.

---

## Cybersecurity

**Critical compliance context:**
- NIST Cybersecurity Framework
- ISO 27001 / 27002
- SOC 2 Type II
- GDPR breach notification (72 hours)
- NIS2 Directive (EU): critical infrastructure security
- Ethical hacking: strict authorized-use-only requirements

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Threat Intelligence Specialist | HIGH | Threat actor profiles, TTPs, IOC analysis |
| Penetration Testing Specialist | HIGH | REQUIRES explicit authorized-use-only constraint |
| SOC Analyst Specialist | HIGH | Alert triage, incident classification, playbooks |
| Security Architecture Reviewer | HIGH | Cloud security architecture, zero-trust design |
| Incident Response Specialist | MEDIUM | IR playbooks, communication templates, forensics |
| Compliance Auditor (ISO/SOC/NIST) | MEDIUM | Gap analysis, control mapping, audit prep |

**Premium tier potential:** VERY HIGH. Security breaches are expensive. Clear ROI.
Note: Penetration Testing skill requires the strongest ethical constraints
in the entire registry — explicit authorized context mandatory.

---

## Manufacturing and Industrial

**Critical compliance context:**
- ISO 9001: quality management systems
- ISO 45001: occupational health and safety
- IEC 61511: functional safety for process industries
- Industry 4.0 standards for connected manufacturing
- Supply chain traceability requirements

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Industrial IoT Specialist | MEDIUM | Sensor integration, SCADA, edge computing |
| Quality Management Specialist | MEDIUM | ISO 9001, defect analysis, SPC |
| Supply Chain Specialist | MEDIUM | Traceability, ERP integration, demand forecasting |
| Safety Engineering Specialist | LOW | Functional safety, hazard analysis |

**Premium tier potential:** MEDIUM. Market exists but is less developer-centric.

---

## Research and Science

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Research Methodology Specialist | HIGH | Experimental design, statistical validity |
| Literature Review Specialist | HIGH | Systematic review, meta-analysis, citation management |
| Statistical Analysis Specialist | HIGH | R/Python statistical methods, interpretation |
| Scientific Writing Specialist | MEDIUM | Paper structure, journal requirements, abstracts |
| Data Visualization Specialist | MEDIUM | Scientific charts, reproducible figures |

**Premium tier potential:** MEDIUM. Research institutions have limited budgets.

---

## Media, Marketing, and Content

**Critical compliance context:**
- ASA (UK), FTC (US), and regional advertising standards
- GDPR consent for data-driven personalization
- Platform-specific content policies (Google, Meta, TikTok)
- Disclosure requirements for AI-generated content (EU AI Act)

**Domain-specific skills needed:**

| Skill | Priority | Notes |
|---|---|---|
| Copywriting Specialist | HIGH | Persuasion WITHOUT dark patterns — strong ethical constraint |
| SEO Specialist | HIGH | Technical SEO, content strategy, Core Web Vitals |
| Marketing Strategy Specialist | MEDIUM | Campaign planning, funnel design, attribution |
| Social Media Specialist | MEDIUM | Platform-specific formats, algorithm awareness |
| Brand Voice Specialist | MEDIUM | Brand guidelines, tone consistency |

**Premium tier potential:** HIGH. Marketing teams are large and pay well.
Note: Copywriting Specialist has the most important ethical constraint outside
of security/medical — no dark patterns, no manufactured urgency, ever.

---

## Priority Order for Community Skill Development

Based on this vertical analysis, the recommended order for the next skills:

**Immediate (needed for announcement at 10 skills):**
1. Security Principles (Tier 0) — universal dependency
2. Backend Specialist (Tier 1) — completes core product team
3. Database Specialist (Tier 1) — already in routing map, highly referenced
4. DevOps Specialist (Tier 1) — deployment is universal
5. Systems Thinking (Tier 0) — foundational for all complex decisions
6. ML/AI Specialist (Tier 1) — high demand given SkillOS context
7. TypeScript Specialist (Tier 2) — near-universal in modern JS projects

**Near-term (v2.0 registry growth, 11-20 skills):**
8. Next.js Expert (Tier 2)
9. Node.js Expert (Tier 2)
10. PostgreSQL Specialist (Tier 2)
11. Python Specialist (Tier 2)
12. Auth Specialist (Tier 3)
13. Testing Specialist (Tier 3)
14. CI/CD Specialist (Tier 3)
15. Mobile Specialist (Tier 1)

**Premium vertical skills (v5.0 marketplace):**
Payment Integration Specialist (Fintech — Africa focus: M-Pesa/Paystack)
HIPAA Compliance Specialist (Healthcare)
Financial Compliance Specialist (Finance)
Copywriting Specialist (Marketing — with strong ethical constraints)
Contract Review Specialist (Legal)

---

*INDUSTRY-VERTICALS.md · SkillOS docs/ · MIT License*
