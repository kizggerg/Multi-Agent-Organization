---
name: qa-test-strategy
description: Defines risk-based validation plans across functional and regression testing. Use when creating acceptance coverage or release confidence assessments.
---

# QA Test Strategy

## Instructions

1. Build and own a test plan during planning and estimation.
2. Map test-plan items to user stories and acceptance criteria.
3. Prioritize automated coverage using the test pyramid:
   - static analysis and fast checks
   - unit tests
   - integration tests
   - minimal end-to-end tests
4. Use manual testing mainly for exploratory validation and unknown risk areas.
5. During build and verify, trace test evidence back to test-plan items.
6. Capture defects with reproducible steps and impact.
7. Produce go/no-go recommendation with confidence level.

## Output Template

- Test plan summary (owner, scope, version)
- Coverage matrix (flow -> tests)
- Story/acceptance mapping
- Pyramid distribution summary (static/unit/integration/e2e)
- Pass/fail status
- Defect summary by severity
- Residual risks
- Release recommendation
