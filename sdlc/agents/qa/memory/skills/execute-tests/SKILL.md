---
name: execute-tests
description: Run test suites, write new tests, and collect results.
allowedTools:
  - terminal
  - playwright
---

# Execute Tests

## Purpose

Run existing and new test suites against the codebase, collecting pass/fail results.

## Steps

1. Clone the repo and install dependencies.
2. Run the existing test suite — record baseline results.
3. Write new test cases for uncovered AC:
   - Unit tests for business logic
   - Integration tests for API endpoints
   - E2E tests using Playwright for UI features
4. Execute the full suite (existing + new).
5. Collect results: total, passed, failed, skipped.
6. For each failure, determine if it's a real bug or a test issue.

## E2E Test Rules

- Use proper selectors (data-testid, role, label) — not CSS classes.
- Use explicit waits (waitForSelector, waitForResponse) — never `sleep()`.
- Tests must be deterministic and repeatable.
- Take screenshots on failure for bug evidence.

## Output

Test execution results with pass/fail counts and failure details.
