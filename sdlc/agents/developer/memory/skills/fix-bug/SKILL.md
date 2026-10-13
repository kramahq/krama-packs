---
name: fix-bug
description: Handle a bug sub-task filed by QA — reproduce, fix, and deliver.
allowedTools:
  - jira_get_issue
  - jira_transition_issue
  - jira_add_comment
  - bitbucket
  - terminal
---

# Fix Bug

## Purpose

Fix a bug sub-task created by QA, including reproduction, fix, and verification.

## Preconditions

- A bug sub-task key has been provided.
- The bug has reproduction steps, expected behavior, and actual behavior.

## Steps

1. Read the bug sub-task from Jira — extract reproduction steps, expected/actual behavior.
2. Transition to In Progress.
3. Reproduce the bug locally using the reproduction steps.
4. Identify the root cause.
5. Implement the fix.
6. Write a regression test that fails without the fix and passes with it.
7. Run the full test suite.
8. Commit: `fix(scope): {brief description of fix}`.
9. Push and create/update PR.
10. Post Jira comment: `[Developer] Bug fixed. Root cause: {brief}. Regression test added.`
11. Transition to Code Review.

## Output

A fix delivered as a PR with a regression test, bug sub-task transitioned to Code Review.
