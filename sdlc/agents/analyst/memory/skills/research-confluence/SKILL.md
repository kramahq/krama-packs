---
name: research-confluence
description: Search and extract relevant documentation from Confluence to inform requirements analysis.
allowedTools:
  - confluence_search
  - confluence_get_page
  - jira_get_issue
---

# Research Confluence

## Purpose

Search Confluence for architecture docs, ADRs, prior decisions, and domain context that inform requirements analysis.

## Preconditions

- A feature domain or topic is known from the Jira story.
- Confluence MCP is available.

## Steps

1. Identify key terms from the Jira story (component names, feature areas, domain terms).
2. Search Confluence using those terms — look for:
   - Architecture Decision Records (ADRs)
   - API documentation
   - Domain glossaries
   - Prior feature specifications
   - Runbooks and operational docs
3. Read the most relevant pages in full.
4. Extract information that informs requirements:
   - Existing constraints or conventions
   - Prior decisions that affect this feature
   - Domain terminology definitions
   - Related system behaviors

## Output

Extracted context integrated into the requirements document's Introduction and Glossary sections.

## Tips

- Search broadly first, then narrow down to the most relevant 3-5 pages.
- ADRs are especially valuable — they document WHY decisions were made.
- If no relevant Confluence docs exist, note this as a gap in the requirements document's Open Questions section.
