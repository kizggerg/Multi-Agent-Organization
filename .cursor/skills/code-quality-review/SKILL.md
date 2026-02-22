---
name: code-quality-review
description: Reviews code for correctness, maintainability, and regressions with practical risk-based feedback. Use when evaluating pull requests or implementation quality.
---

# Code Quality Review

## Instructions

1. Check behavior correctness and edge cases.
2. Check readability, cohesion, and complexity.
3. Check test coverage for changed behavior.
4. Flag regressions, risky assumptions, and missing safeguards.
5. Prioritize findings by severity and impact.

## Severity Bands

- Critical: must fix before merge
- High: should fix in this change
- Medium: fix soon or track explicitly
- Low: optional improvement

## Output Template

- Scope reviewed
- Findings by severity (critical/high/medium/low)
- Evidence for each finding (file/path and behavior impact)
- Required fixes before merge
- Deferred items with owner and due date
