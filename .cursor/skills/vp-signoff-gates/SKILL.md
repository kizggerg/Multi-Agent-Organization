---
name: vp-signoff-gates
description: Applies executive decision gates for high-impact scope, budget, risk, and release decisions. Use when determining whether VP Engineering approval is required.
---

# VP Sign-Off Gates

## Instructions

1. Check if the decision crosses any escalation threshold.
2. If a threshold is crossed, halt execution before irreversible steps.
3. Summarize options, costs, risks, and recommendation.
4. Identify what is reversible versus irreversible.
5. Provide an explicit ask for VP Engineering (human) decision.
6. Record decision conditions and next checkpoint.

## Default Escalation Thresholds

- Budget variance > 15% versus approved baseline
- Scope increase > 20% effort versus approved scope
- High or critical unresolved architecture/security risk
- High release risk (rollback uncertainty, major customer impact, or critical unresolved defects)
- Initiative start with medium-or-higher cost envelope and cross-team staffing impact

## Escalation Categories

- Budget variance beyond threshold
- Significant scope change
- Material architecture/security risk acceptance
- High business-impact release decision

## Output Template

- Gate trigger(s)
- Decision options
- Recommendation
- Required VP Engineering (human) decision
- Post-decision conditions
