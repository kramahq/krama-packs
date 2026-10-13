---
name: write-adr
description: Write an Architecture Decision Record to Confluence for significant design decisions.
allowedTools:
  - confluence_create_page
  - confluence_search
---

# Write ADR

## Purpose

Document significant architectural decisions in Confluence as Architecture Decision Records (ADRs) for future reference.

## Preconditions

- A significant architectural decision has been made during design.
- Confluence access is available.

## When to Use

Write an ADR when:
- Choosing between multiple viable approaches
- Introducing a new technology or pattern
- Making a decision that affects multiple components
- Deviating from established conventions

Do NOT write an ADR for:
- Trivial implementation choices
- Following existing patterns without deviation

## ADR Structure

```markdown
# ADR-{number}: {Title}

## Status
Accepted

## Context
{What is the issue that we're seeing that is motivating this decision?}

## Decision
{What is the change that we're proposing and/or doing?}

## Consequences
{What becomes easier or more difficult to do because of this change?}

## Alternatives Considered
{What other options were evaluated and why they were rejected?}
```

## Output

A Confluence page containing the ADR, with the URL included in the design summary comment on Jira.
