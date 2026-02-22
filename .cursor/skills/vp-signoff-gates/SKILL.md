---
name: vp-signoff-gates
description: Applies executive decision gates for high-impact scope, budget, risk, and release decisions. Use when determining whether VP Engineering approval is required.
---

# VP Sign-Off Gates

## Instructions

1. Check whether this checkpoint is one of the mandatory stage gates in `docs/SDLC.md`.
2. Check whether any escalation threshold is crossed.
3. If either condition is true, halt execution before irreversible steps.
4. Summarize options, costs, risks, and recommendation.
5. Identify what is reversible versus irreversible.
6. Provide an explicit ask for VP Engineering (human) decision.
7. Record decision conditions and next checkpoint.

## Mandatory Stage Gates

- Gate 1: between Stage 1 and Stage 2
- Gate 2: between Stage 3 and Stage 4 (include detailed delivery cost estimate)
- Gate 3: before live release (between Stage 5 and Stage 6)

## Default Escalation Thresholds

- Budget variance > 15% versus approved baseline
- Scope increase > 20% effort versus approved scope
- High or critical unresolved architecture/security risk
- High release risk (rollback uncertainty, major customer impact, or critical unresolved defects)

## Escalation Categories

- Budget variance beyond threshold
- Significant scope change
- Material architecture/security risk acceptance
- High business-impact release decision

## Output Template

- Trigger type (mandatory stage gate and/or escalation)
- Gate trigger(s)
- Decision options
- Recommendation
- Required VP Engineering (human) decision
- Post-decision conditions
