# SkillOS Changelog
## Permanent record of all implemented changes across versions.
## This file IS committed to the repository.
## SkillUpdates.md (gitignored) is the scratch space; this is the truth.

Format: newest entries at the top.

---

## [v2.0.0-beta] — 2026-07-19

### Added — Phase 2.3 Announcement Content (SkillOsUpdates/, gitignored)
- `SkillOsUpdates/LAUNCH-POST.md` — full launch article for dev.to / Hashnode (ready to publish)
- `SkillOsUpdates/LAUNCH-THREAD-X.md` — 12-tweet X/Twitter launch thread (ready to post)
- `SkillOsUpdates/LAUNCH-HN-POST.md` — Show HN post with title, body, and submission timing guidance

### Added — Phase 2.1 New Skills (11-skill milestone — complete Tier 0 + Tier 1)
- `registry/tier-1/mobile-specialist-v1.0.0.md` — compiled via Skill Creator v1.1. Cross-platform (Flutter/React Native) and native iOS/Android. 15 failure modes: insecure token storage, missing certificate pinning, online-only design, low-end device blindness, deep link hijacking, M-Pesa/non-card payment rail assumption. 4 output templates: architecture spec, payment integration, performance debug, store submission checklist.

### Added — Phase 2.1 New Skills (10-skill threshold reached)
- `registry/tier-0/systems-thinking-v1.0.0.md` — compiled via Skill Creator v1.1. Conway's Law, Team Topologies, systemic failure modes (distributed monolith, resume-driven development, Goodhart's Law), 15 domain-specific failure modes, 4 output templates (trade-off analysis, socio-technical map, system dynamics map, root cause analysis).
- `registry/tier-1/ml-ai-specialist-v1.0.0.md` — compiled via Skill Creator v1.1. RAG architectures (chunking, hybrid retrieval, re-ranking), agent topologies, LLMOps evaluation pipelines, 10 domain-specific failure modes (blind top-K, prompt drift, indirect prompt injection, ACL bypass in vector DBs).
- `registry/tier-2/typescript-specialist-v1.0.0.md` — compiled via Skill Creator v1.1. Advanced type theory (discriminated unions, conditional/mapped types), Zod runtime boundary validation, compiler configuration, 10 domain-specific failure modes (the `any` virus, type gymnastics, lying to the compiler with `as Type`).

### Added — Phase 2.2 Community Infrastructure
- `.github/PULL_REQUEST_TEMPLATE.md` — strict SDS enforcement on all contributions: all 13 components, validation model specified, three test results, global defaults checklist, MIT license confirmation
- `.github/ISSUE_TEMPLATE/bug_report.yml` — structured bug reporting with severity classification, model used, reproduction steps, expected vs actual output
- `.github/ISSUE_TEMPLATE/new_skill_proposal.yml` — proposal gate with overlap check, 5 failure mode preview, routing relationships, ethical constraints required before building
- `.github/ISSUE_TEMPLATE/skill_improvement.yml` — SDS component-targeted improvements with regional context field
- `.github/ISSUE_TEMPLATE/config.yml` — disables blank issues, routes general questions to Discussions
- `docs/WORKFLOW-EXAMPLES.md` — three complete multi-skill workflows: Full Stack SaaS (construction fintech context), Financial API (Nigeria CBN + NDPR compliance), Legacy Security Audit
- `docs/INDUSTRY-VERTICALS.md` — 10 industry verticals mapped to base skills + domain-specific skill needs + premium tier opportunities; priority order for next 15 skills

---

## [v1.1.0] — 2026-07-15

### Added
- `docs/ASSUMPTION-TEMPLATE.md` — standardized assumption documentation template
  for all skills when handling 50-79% complete requests. Converts CONDITIONAL
  validation results to PASS by enforcing explicit assumption surfacing.
- `docs/CROSS-TIER-ROUTING-MAP.md` — explicit routing paths between all skills
  across tiers. Defines typed handoff fields for Tier 0→1, Tier 1→2,
  Tier 1↔1, and Tier 1→0 escalation. Foundation for v3.0 Skill Runtime routing.
- `docs/WORKFLOW-EXAMPLES.md` — three complete multi-skill workflow examples
  (SaaS product build, API design, security review).
- `SkillOsTests.md` — structured test scratch file (gitignored).
- `SkillUpdates.md` — update tracking scratch file (gitignored after implementing).
- `CHANGELOG.md` — this file. Permanent version history.
- `MASTER_CONTEXT.md` — complete project context for cross-session continuity.
- `IMPLEMENTATION_ROADMAP.md` — full six-phase roadmap with checklists.
- `SYSTEM_INSTRUCTIONS.md` — enhanced system prompt for Claude Projects.
- `.gitignore` — ignores test and update scratch files.

### Changed
- `README.md` — updated to full eight-layer architecture vision. Added complete
  2026 tool landscape (four categories). Updated roadmap to show v1.0 complete
  and v1.1 active. Added Project Rules, AaaS, IDE Integration to platform description.
- `SKILL-CREATOR.md` — updated to v1.1. Installation now covers all platforms
  (Claude, ChatGPT, Gemini, Codex CLI, OpenCode, Aider, Antigravity, Devin Desktop,
  Nimbalyst). Model table updated to July 2026 frontier.
- `SKILL-DEFINITION-STANDARD.md` — updated to v1.1. Added portability annotations,
  cultural intelligence as named component, full 10-phase Decision Engine,
  Observability added to Constraint Matrix, Skill Temperature Spectrum formalized.
- `CONTRIBUTING.md` — expanded tool guidance (5 terminal agents with example commands).
- `context.md` — updated current status, tool recommendations, validation table.
- `validation/test-harness.md` — added cross-model validation methodology table.
  Clarified that Haiku validation = graceful degradation, not production readiness.
- `registry/tier-0/software-architect-v1.0.1.md` — observability fix applied.
  New Constraint Matrix row, Quality Gate, Mode 1 section, Mode 2 section, FM-18.
  SDS compliance: 12/13 → 13/13.

### Pending (v1.1 in progress)
- Testing strategy formalization for Tier 0 and Tier 1 skills
- Tier 1 cross-model validation on all 3 pilot skills

---

## [v1.0.1] — 2026-07-12 (patch)

### Changed
- `registry/tier-0/software-architect-v1.0.1.md` — observability gap fixed.
  Addresses the one genuine SDS compliance gap found in Phase 2 validation.

---

## [v1.0.0] — 2026-07-12

### Added
- `SKILL-DEFINITION-STANDARD.md` — 13-component SDS governance contract
- `SKILL-CREATOR.md` — 10-phase compiler system prompt
- `registry/tier-0/software-architect-v1.0.0.md` — Tier 0 pilot skill
- `registry/tier-1/frontend-specialist-v1.0.0.md` — Tier 1 pilot skill (3/3 PASS)
- `registry/tier-2/react-expert-v1.0.0.md` — Tier 2 pilot skill
- `README.md` — project front door
- `CONTRIBUTING.md` — contribution guidelines
- `context.md` — AI coding tool session context
- `validation/test-harness.md` — three-test validation standard
- `LICENSE` — MIT
- GitHub Actions SDS compliance validator

### Validation results (v1.0)
- 7/9 PASS · 2/9 CONDITIONAL · 0/9 FAIL
- SDS Compliance: 92% (12/13 — observability gap)
- Model: claude-haiku-4.5 (graceful degradation test)

---

*CHANGELOG.md · SkillOS · MIT License*
