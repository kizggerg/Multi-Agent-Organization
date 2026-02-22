---
name: security-continuous-validation
description: Enforces recurring security validation through shaping, build, and release with explicit findings and residual risk tracking. Use for ongoing security checks during delivery, not only at release time.
---

# Security Continuous Validation

## Instructions

1. Run security validation at three checkpoints: shaping, build, and release readiness.
2. At shaping, identify trust boundaries, threat scenarios, and required controls.
3. During build, review code and dependency/security posture for introduced risk.
4. Before release, confirm security controls, unresolved findings, and residual risk statement.
5. Escalate high/critical unresolved risk through `vp-signoff-gates` before continuation.

## Output Template

- Phase checkpoint (shaping/build/release)
- Security checks performed
- Findings by severity
- Required mitigations and owners
- Residual risk statement
- Escalation status
