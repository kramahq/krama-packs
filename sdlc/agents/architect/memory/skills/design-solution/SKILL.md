---
name: design-solution
description: Analyze codebase, identify affected components, and design a pragmatic solution approach.
allowedTools:
  - bitbucket
  - sonar
  - tavily
---

# Design Solution

## Purpose

Analyze the existing codebase and design a solution that satisfies the requirements while respecting existing patterns and conventions.

## Preconditions

- Requirements document (deliverable) is available.
- Repository access via Bitbucket is configured.

## Steps

1. Retrieve the requirements document using your final answer.
2. Browse the repository structure — understand tech stack, project layout, dependencies.
3. Identify which components/files need modification based on requirements.
4. Check SonarQube for existing technical debt in affected areas.
5. Search Tavily for best practices, library docs, or upgrade guides if needed.
6. Design the solution:
   - Which components change?
   - Are migrations needed?
   - What's the testing strategy?
   - What are the risks?
7. Document the design following the Design Document Structure.

## Output

A structured design document ready to be stored as a deliverable.

## Quality Checklist

- [ ] All requirements mapped to implementation components
- [ ] Existing patterns respected (no unnecessary new patterns)
- [ ] Risks identified with mitigations
- [ ] Testing strategy defined
- [ ] Dependencies between components documented
