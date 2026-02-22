# Multi-Agent Product Organization (Cursor-Native)

This repository defines a role-based engineering organization built with Cursor subagents and Cursor skills only (no custom orchestration scripts).

## Operating Model

- Role subagents live in `.cursor/agents/`
- Reusable capabilities live in `.cursor/skills/`
- Always-on enforcement rules live in `.cursor/rules/`
- SDLC uses explicit handoffs, artifacts, and approval gates
- VP Engineering is a human-in-the-loop decision role, not a subagent
- Git is the source of truth for planning, implementation, verification, and release records
- Detailed SDLC reference: `docs/SDLC.md`

## Role Subagents

- `product-manager`: market opportunities, value proposition, initiative/epic framing
- `designer`: design discovery, UX/UI specifications, and experience validation
- `program-manager`: program/project breakdown, sequencing, dependencies, risk tracking
- `engineering-manager`: estimation, staffing, execution planning, quality accountability
- `developer`: implementation, tests, refactoring, defect fixes
- `qa`: test strategy, acceptance validation, regression confidence
- `devops`: CI/CD, environment reliability, release safety
- `architect-security`: architecture direction, security validation, NFR governance
- `manager`: orchestrates subagents, enforces SDLC phase progression, and handles gate pauses

## Human Governance Role

The VP Engineering role is performed by the human operator. Agents must pause and request explicit sign-off when a gate is triggered.

Mandatory VP gates are fixed at transitions 1->2, 3->4, and pre-live 5->6. Outside these gates, VP sign-off is only required for escalations.

## Canonical Role-to-Skill Matrix

- `product-manager` (required): `product-discovery`, `roadmap-prioritization`; (optional): `design-discovery-spec`, `delivery-planning`, `cost-and-budgeting`
- `designer` (required): `design-discovery-spec`; (optional): `product-discovery`, `architecture-security-review`
- `program-manager` (required): `delivery-planning`, `vp-signoff-gates`; (optional): `roadmap-prioritization`, `cost-and-budgeting`, `org-governance-enforcement`
- `engineering-manager` (required): `engineering-execution`, `vp-signoff-gates`; (optional): `code-quality-review`, `delivery-planning`, `org-governance-enforcement`
- `developer` (required): `engineering-execution`, `code-quality-review`; (optional): `qa-test-strategy`, `architecture-security-review`, `security-continuous-validation`
- `qa` (required): `qa-test-strategy`; (optional): `code-quality-review`, `devops-release`, `security-continuous-validation`
- `devops` (required): `devops-release`; (optional): `cost-and-budgeting`, `architecture-security-review`, `security-continuous-validation`, `vp-signoff-gates`
- `architect-security` (required): `architecture-security-review`, `security-continuous-validation`; (optional): `engineering-execution`, `code-quality-review`, `cost-and-budgeting`
- `manager` (required): `delivery-planning`, `org-governance-enforcement`, `vp-signoff-gates`; (optional): `security-continuous-validation`

## SDLC Workflow and Minimum Artifacts

1. **Opportunity and Discovery** (Product Manager)
   - Required artifacts: PRD with functional requirements, non-functional requirements, metrics, and initial cost envelope
2. **Initiative Shaping** (Product + Designer + Architect/Security)
   - Required artifacts: design discovery outputs, UX/UI design spec, architecture document, threat model, scope boundaries, initial epic map
3. **Planning and Estimation** (Program + Engineering Manager + Developer + QA)
   - Required artifacts: work breakdown, estimate baseline, dependency map, milestone plan, QA test plan, user stories
   - User story fields: description, acceptance criteria, story points in ideal days, criticality (must/should/could/wont)
4. **Build and Verify** (Developer + QA + DevOps)
   - Required artifacts: PR set, automated test evidence mapped to test plan, defect log, quality summary
5. **Release Readiness** (DevOps + QA + Architect/Security)
   - Required artifacts: release checklist, security validation report, rollout/rollback plan
6. **Release and Observe** (DevOps + Program + Product)
   - Required artifacts: deployment record, KPI snapshot, budget variance report, follow-up actions

## Halt and Notify Workflow (Long-Running Agent Control)

Manager enforces assembly-line halts at mandatory stage gates and escalation triggers. When a halt occurs, agents must produce a VP decision brief using `vp-signoff-gates`:

- include trigger reason, options, recommendation, reversible/irreversible impact
- include cost impact (delivery/runtime/agent usage), confidence, and risk level
- stop before irreversible actions (production release, scope expansion, risk acceptance)

No gate decision means no continuation beyond the blocking step.

## VP Sign-Off Policy

Mandatory stage-gate approvals:

- Gate 1: between Stage 1 and Stage 2
- Gate 2: between Stage 3 and Stage 4 (must include detailed delivery cost estimate)
- Gate 3: before live release (between Stage 5 and Stage 6)

Escalation approvals (any phase):

- budget variance exceeds 15% versus approved baseline
- scope increase exceeds 20% effort versus approved scope
- architecture/security risk is rated high or critical and cannot be fully mitigated in-cycle
- release risk is high (rollback uncertainty, major customer impact, or critical unresolved defects)

## Continuous Security Validation

Security checks are mandatory at shaping, build, and release phases:

- threat/risk review during initiative shaping
- code-level and dependency/security validation during build
- release-time security readiness check with explicit residual risk statement

Use `security-continuous-validation` and `architecture-security-review` together for high-risk changes.

## Test Quality Policy

- QA owns the test plan at Stage 3.
- Stage 4 evidence must trace to test-plan items.
- Automated testing follows the test pyramid: static analysis, unit, integration, then minimal end-to-end.
- Manual testing is exploratory support, not the primary validation path.

## Git-Based Workflow

- one initiative branch per approved scope (`initiative/<name>`)
- one delivery PR per scoped increment (`feature/<name>` or `fix/<name>`)
- required PR checks:
  - test execution and quality gates
  - QA validation summary
  - architecture/security review for sensitive changes
  - release-readiness checklist for deployment PRs
- keep decision records in PR descriptions/comments

## Governance Enforcement Loop

Use `org-governance-enforcement` as a periodic and pre-release audit to verify:

- SDLC artifact completeness for current phase
- role definition quality and role-skill alignment
- skill documentation quality and output discipline
- gate escalation correctness and VP handoff readiness

## How To Use

- invoke role subagents directly (example: `/manager`, `/product-manager`, `/designer`, `/developer`, `/qa`)
- request parallel workstreams in one prompt when appropriate
- keep prompts outcome-focused (inputs, constraints, outputs, deadline)
- when a gate triggers, review the VP brief and provide decision before agents continue