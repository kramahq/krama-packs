---
name: refine-story
description: Read a Jira story, research docs, and write structured requirements with Given/When/Then acceptance criteria.
allowedTools:
  - jira_get_issue
  - jira_search
  - jira_add_comment
  - confluence_search
---

# Refine Story

## Purpose

Transform a raw Jira story into a well-defined requirements document with numbered acceptance criteria in Given/When/Then format.

## Preconditions

- A Jira story key has been provided in the task message.
- The story exists in Jira and has a description.

## Steps

1. Read the Jira story using `jira_get_issue` — extract description, comments, linked issues.
2. Search Confluence for related architecture docs, ADRs, and domain context.
3. Read linked issues to understand dependencies and broader context.
4. Draft the requirements document following the structure:
   - Introduction
   - Glossary
   - Numbered Requirements (REQ-1, REQ-2, ...) with Given/When/Then AC
   - Non-Functional Requirements
   - Edge Cases
   - Out of Scope
   - Open Questions
5. Ensure every AC is testable by a QA agent.
6. Include security criteria if the feature involves auth, data, or APIs.
7. Include rollback criteria if the story references a migration.
8. Return the document as your final answer; the orchestrator keeps it for the next agent.

## Output

A structured requirements document stored as a deliverable, with a summary comment posted to the Jira story.

## Quality Checklist

- [ ] All AC are in Given/When/Then format
- [ ] At least one NFR identified
- [ ] Edge cases documented
- [ ] Out of scope explicitly stated
- [ ] No assumptions — everything grounded in Jira/Confluence data
