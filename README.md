# Multi-Agent Product Organization (Cursor-Native)

This repository defines a role-based engineering organization built with Cursor subagents and Cursor skills only (no custom orchestration scripts).

## Operating Model

- Role subagents live in `.cursor/agents/`
- Reusable capabilities live in `.cursor/skills/`
- SDLC uses explicit handoffs, artifacts, and approval gates
- VP Engineering is a human-in-the-loop decision role, not a subagent
- Git is the source of truth for planning, implementation, verification, and release records

## Role Subagents

- `product-manager`: market opportunities, value proposition, initiative/epic framing
- `program-manager`: program/project breakdown, sequencing, dependencies, risk tracking
- `engineering-manager`: estimation, staffing, execution planning, quality accountability
- `developer`: implementation, tests, refactoring, defect fixes
- `qa`: test strategy, acceptance validation, regression confidence
- `devops`: CI/CD, environment reliability, release safety
- `architect-security`: architecture direction, security validation, NFR governance

## Human Governance Role

The VP Engineering role is performed by the human operator. Agents must pause and request explicit sign-off when a gate is triggered.

## Canonical Role-to-Skill Matrix

- `product-manager` (required): `product-discovery`, `roadmap-prioritization`; (optional): `delivery-planning`, `cost-and-budgeting`
- `program-manager` (required): `delivery-planning`, `vp-signoff-gates`; (optional): `roadmap-prioritization`, `cost-and-budgeting`, `org-governance-enforcement`
- `engineering-manager` (required): `engineering-execution`, `vp-signoff-gates`; (optional): `code-quality-review`, `delivery-planning`, `org-governance-enforcement`
- `developer` (required): `engineering-execution`, `code-quality-review`; (optional): `qa-test-strategy`, `architecture-security-review`, `security-continuous-validation`
- `qa` (required): `qa-test-strategy`; (optional): `code-quality-review`, `devops-release`, `security-continuous-validation`
- `devops` (required): `devops-release`; (optional): `cost-and-budgeting`, `architecture-security-review`, `security-continuous-validation`, `vp-signoff-gates`
- `architect-security` (required): `architecture-security-review`, `security-continuous-validation`; (optional): `engineering-execution`, `code-quality-review`, `cost-and-budgeting`

## SDLC Workflow and Minimum Artifacts

1. **Opportunity and Discovery** (Product Manager)
   - Required artifacts: problem statement, value hypothesis, target metrics, initial cost envelope
2. **Initiative Shaping** (Product + Program + Architect/Security)
   - Required artifacts: epic map, constraints, initial architecture notes, risk register
3. **Planning and Estimation** (Program + Engineering Manager + Developer)
   - Required artifacts: work breakdown, estimate baseline, dependency map, milestone plan
4. **Build and Verify** (Developer + QA)
   - Required artifacts: PR set, test evidence, defect log, quality summary
5. **Release Readiness** (DevOps + QA + Architect/Security)
   - Required artifacts: release checklist, security validation report, rollout/rollback plan
6. **Release and Observe** (DevOps + Program + Product)
   - Required artifacts: deployment record, KPI snapshot, budget variance report, follow-up actions

## Halt and Notify Workflow (Long-Running Agent Control)

When any gate below triggers, agents must halt execution and produce a VP decision brief using `vp-signoff-gates`:

- include trigger reason, options, recommendation, reversible/irreversible impact
- include cost impact (delivery/runtime/agent usage), confidence, and risk level
- stop before irreversible actions (production release, scope expansion, risk acceptance)

No gate decision means no continuation beyond the blocking step.

## VP Sign-Off Thresholds (Default Policy)

VP approval is required when any condition is true:

- budget variance exceeds 15% versus approved baseline
- scope increase exceeds 20% effort versus approved scope
- architecture/security risk is rated high or critical and cannot be fully mitigated in-cycle
- release risk is high (rollback uncertainty, major customer impact, or critical unresolved defects)
- initiative starts above medium cost envelope or cross-team staffing impact

## Continuous Security Validation

Security checks are mandatory at shaping, build, and release phases:

- threat/risk review during initiative shaping
- code-level and dependency/security validation during build
- release-time security readiness check with explicit residual risk statement

Use `security-continuous-validation` and `architecture-security-review` together for high-risk changes.

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

- invoke role subagents directly (example: `/product-manager`, `/developer`, `/qa`)
- request parallel workstreams in one prompt when appropriate
- keep prompts outcome-focused (inputs, constraints, outputs, deadline)
- when a gate triggers, review the VP brief and provide decision before agents continue