---
name: write-test-plan
description: Derive test cases from acceptance criteria and sub-task testing notes.
allowedTools:
  - jira_get_issue
  - jira_search
---

# Write Test Plan

## Purpose

Create a comprehensive test plan mapping each acceptance criterion to one or more test cases.

## Steps

1. Read all completed sub-tasks and their AC.
2. Retrieve the requirements document for NFRs and edge cases.
3. For each AC, create test cases covering:
   - Happy path (positive test)
   - Error/failure path (negative test)
   - Edge cases and boundary conditions
4. Include E2E test cases for user-facing features.
5. Note which tests already exist vs. need to be written.

## Output

A test plan document with test case IDs mapped to requirement IDs and sub-task AC.
