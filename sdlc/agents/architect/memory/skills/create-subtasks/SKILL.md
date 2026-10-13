---
name: create-subtasks
description: Break a design into Jira sub-tasks with the standard template structure.
allowedTools:
  - jira_create_issue
  - jira_add_comment
---

# Create Sub-Tasks

## Purpose

Break the design document into independent, well-specified Jira sub-tasks that developers can immediately work from.

## Preconditions

- Design document is complete.
- Parent story key is known.

## Steps

1. Identify logical units of work from the design document.
2. For each unit, create a sub-task using `jira_create_issue` with `parent` field.
3. Each sub-task MUST include all template sections:
   - Scope (specific files, classes, APIs)
   - Acceptance Criteria (sliced from parent story)
   - Technical Notes (approach, patterns, libraries)
   - Dependencies (blocked by / blocks)
   - Testing Notes (how to verify)
   - Spec Reference (link to deliverables)
   - Labels and Story Points
4. Ensure sub-tasks are independent when possible (parallelizable).
5. Include explicit dependency relationships when work must be sequenced.
6. Store the task breakdown as a deliverable.

## Output

Jira sub-tasks created under the parent story, plus a task breakdown deliverable.

## Rules

- Each sub-task must be completable in isolation.
- Story Points: 1 (small), 3 (medium), 5 (large).
- Labels: one of [backend, frontend, infra, docs, test].
- Do NOT assign sub-tasks — the Orchestrator handles delegation.
