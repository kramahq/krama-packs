---
name: file-bugs
description: Create bug sub-tasks in Jira with full reproduction details.
allowedTools:
  - jira_create_issue
  - jira_add_comment
---

# File Bugs

## Purpose

Create well-structured bug sub-tasks in Jira for each defect found during testing.

## Bug Sub-Task Template

```
Summary: [Bug] {short description}

## Reproduction Steps
1. {Step 1}
2. {Step 2}
3. {Step 3}

## Expected Behavior
{What should happen according to the AC}

## Actual Behavior
{What actually happens, including error messages}

## Affected Sub-Task
{JIRA-KEY} — {which AC is violated}

## Severity
{Critical | Major | Minor | Trivial}

## Environment
Branch: {branch}
OS: {os}
Runtime: {version}

Labels: [bug]
Priority: {based on severity}
```

## Severity Guide

- **Critical** — System crash, data loss, security vulnerability, complete feature broken.
- **Major** — Core functionality broken, no workaround, AC clearly violated.
- **Minor** — Feature works but with issues, workaround exists.
- **Trivial** — Cosmetic issue, typo, minor UI glitch.

## Rules

- Always use `jira_create_issue` with `parent` field — never just a comment.
- Always include reproduction steps — "it doesn't work" is not acceptable.
- Always reference the specific AC that is violated.
- Include screenshots or error logs when available.
