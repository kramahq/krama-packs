---
name: fix-review-feedback
description: Address code review comments, push fixes, and update the PR.
allowedTools:
  - jira_get_issue
  - jira_add_comment
  - bitbucket
  - terminal
---

# Fix Review Feedback

## Purpose

Address reviewer's feedback on a pull request, push fixes, and prepare for re-review.

## Preconditions

- A re-dispatch message from the Orchestrator with review feedback.
- The PR branch still exists and is accessible.

## Steps

1. Read the review feedback from the task message.
2. Read the PR comments in Bitbucket for specific file/line references.
3. Check out the existing branch.
4. Address each review comment:
   - Fix code issues
   - Add missing tests
   - Resolve security concerns
5. Run the test suite — ensure all tests pass.
6. Commit with message: `fix(scope): address review feedback`.
7. Push the updated branch.
8. Post a Jira comment: `[Developer] Review feedback addressed. PR updated.`

## Output

Updated PR ready for re-review. Jira sub-task remains in Code Review state.
