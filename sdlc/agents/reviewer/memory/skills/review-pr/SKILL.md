---
name: review-pr
description: Review a pull request for correctness, security, performance, and code quality.
allowedTools:
  - bitbucket
  - jira_get_issue
  - jira_transition_issue
  - jira_add_comment
  - terminal
  - sonar
---

# Review Pull Request

## Purpose

Evaluate a pull request against the sub-task's acceptance criteria and design document, producing a clear approve/reject decision.

## Preconditions

- PR link or reference is available (from Developer's hand-off or task message).
- Sub-task AC and design document are accessible.

## Review Checklist

### Correctness
- [ ] Each acceptance criterion is satisfied by the code changes
- [ ] Implementation matches the design document's approach
- [ ] Edge cases from the sub-task's Testing Notes are handled

### Security (OWASP Top 10)
- [ ] No injection vulnerabilities (SQL, XSS, command injection)
- [ ] No authentication/authorization bypass
- [ ] No sensitive data exposure (logs, responses, error messages)
- [ ] Input validation on all external inputs
- [ ] No hardcoded secrets or credentials

### Performance
- [ ] No N+1 queries
- [ ] No unbounded loops or collections
- [ ] Pagination for list endpoints
- [ ] No excessive memory allocation

### Test Coverage
- [ ] Tests exist for new logic
- [ ] Edge cases covered per Testing Notes
- [ ] Tests are deterministic (no timing-based assertions)

### Code Style
- [ ] Consistent with existing codebase conventions
- [ ] Meaningful variable/function names
- [ ] No dead code or commented-out blocks

### Architecture
- [ ] Aligned with design document and ADRs
- [ ] No unnecessary new patterns introduced
- [ ] Proper separation of concerns

## Output

Review decision (approve or changes requested) with specific, actionable findings referencing file names and line numbers.
