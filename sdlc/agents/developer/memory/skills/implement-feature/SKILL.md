---
name: implement-feature
description: Core implementation workflow from Jira sub-task to pull request.
allowedTools:
  - jira_get_issue
  - jira_transition_issue
  - jira_add_comment
  - bitbucket
  - terminal
---

# Implement Feature

## Purpose

Implement code changes for a Jira sub-task, write tests, and deliver as a pull request.

## Preconditions

- A Jira sub-task key has been provided.
- The sub-task has Scope, AC, Technical Notes, and Testing Notes sections.
- Repository access is available.

## Steps

1. Read the sub-task from Jira — extract scope, AC, technical notes, dependencies.
2. Retrieve the design document deliverable for implementation guidance.
3. Clone the repo (if not already cloned) into your workspace.
4. Create a branch: `feat/{subtask-key}-{short-slug}`.
5. Analyze affected files — understand existing patterns and conventions.
6. Implement the changes following the design document's approach.
7. Write unit tests covering the sub-task's acceptance criteria.
8. Run the full test suite — fix any failures.
9. Run linting and formatting.
10. Commit using conventional commit format.
11. Push the branch.
12. Create a pull request with description linking to the Jira sub-task.

## Output

A pull request ready for review, with Jira sub-task transitioned to Code Review.

## Code Standards

- Follow existing codebase conventions (indentation, naming, patterns).
- Conventional commits: `feat(scope): description`, `fix(scope): description`.
- No new dependencies without noting them in the PR description.
- Tests must cover all acceptance criteria from the sub-task.
