---
name: org-governance-enforcement
description: Audits repository execution discipline by checking SDLC adherence, role clarity, role-to-skill mapping, and governance escalation readiness. Use as a periodic control or before major approvals/releases.
---

# Org Governance Enforcement

## Purpose

Act as the organizational compliance "hammer": verify that each role and workflow is executing as defined, and force explicit remediation when gaps are found.

## Audit Scope

1. SDLC adherence
   - Confirm current phase deliverables exist and are complete.
   - Verify upstream/downstream handoff artifacts are present.
2. Role specification quality
   - Ensure each subagent has clear responsibilities, collaborations, and outputs.
   - Flag role overlap or responsibility gaps.
3. Role-to-skill mapping integrity
   - Check that assigned skills support the role's responsibilities.
   - Flag missing core skills or contradictory skill usage.
4. Skill documentation quality
   - Ensure each skill has concise instructions and a clear output format.
   - Flag vague language or missing decision criteria.
5. Governance and escalation readiness
   - Verify gate criteria are defined for scope, risk, budget, and release.
   - Verify issues crossing thresholds are explicitly escalated to VP Engineering (human).
6. Halt/notify discipline
   - Verify long-running workflows halt at gate checkpoints.
   - Verify VP decision briefs are produced before irreversible actions.

## Enforcement Rules

- No silent failures: every failed check needs an owner and due date.
- No ambiguous status: each finding is pass/fail/partial.
- No gate bypass: high-risk findings require explicit VP decision.
- No auto-approval: VP decisions are human-only and must be acknowledged before continuation.

## Output Template

- Audit scope and timestamp
- Overall status (green/yellow/red)
- Findings:
  - `Critical`: must fix before next gate
  - `High`: fix in current cycle
  - `Medium`: track with owner and due date
  - `Low`: improvement opportunity
- Required escalations
- Remediation plan (owner, action, due date)
- Re-audit trigger
