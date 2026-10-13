# QA — Execution Playbook

## Tools

1. **mcp-atlassian** — Search for sub-tasks (`jira_search`), read stories and sub-tasks (`jira_get_issue`), create bug sub-tasks (`jira_create_issue` with `parent` field), post test comments (`jira_add_comment`).
2. **bitbucket** — Read PRs, browse repo code, understand what changed.
3. **Your file tools** — Read/write test files in your workspace, read memory files.
4. **terminal** — Clone repos, install dependencies, run test suites, execute commands.
5. **playwright** — Run E2E browser tests, interact with UIs, take screenshots for bug evidence.
6. **Earlier results** — the orchestrator includes what you need from earlier phases in your task; ask it if something is missing.

## Jira as Source of Truth

### Reading from Jira

1. **Read all completed sub-tasks** — Use `jira_search` with JQL `parent = {storyKey}` to retrieve all sub-tasks. Read each completed sub-task's description, AC, technical notes, and testing notes.
2. **Read the parent story** — Full feature context, overall AC, cross-cutting concerns.
3. **Read prior agent artifacts** — Developer hand-off comments for PR links, Reviewer comments for flagged concerns.
4. **Read sub-task testing notes** — Each sub-task has a `## Testing Notes` section — use as starting point.

### Writing to Jira

1. **Progress comments** — Post with `[QA]` prefix:
   - `[QA] Beginning test cycle. Reading completed sub-tasks and acceptance criteria.`
   - `[QA] Test plan created. {count} test cases covering {count} sub-tasks.`
   - `[QA] Test execution in progress. {passed}/{total} passing so far.`
2. **Bug sub-task creation** — Use `jira_create_issue` with `parent` field and `[Bug]` prefix summary. Include:
   - Reproduction Steps (numbered)
   - Expected Behavior
   - Actual Behavior
   - Affected Sub-Task reference
   - Severity (Critical, Major, Minor, Trivial)
3. **Test result comments** — Summarize pass/fail counts and link to bug sub-tasks.

## Spec-Driven Workflow

| Direction | Artifacts |
|-----------|-----------|
| **Consumes** | Requirements document (deliverable from Analyst), Design document (deliverable from Architect) |
| **Produces** | Test results (pass/fail summary, bug sub-tasks) |

## Workflow Steps

1. **Read all sub-tasks** — Use `jira_search` with JQL `parent = {storyKey}`. Filter for completed sub-tasks.
2. **Post start comment** — `[QA] Beginning test cycle. Reading completed sub-tasks and acceptance criteria.`
3. **Read spec documents** — Use your final answer to retrieve requirements and design documents.
4. **Build test plan** — Map each sub-task's AC to test cases. Use the **write-test-plan** skill.
5. **Clone and set up** — Clone the repo, install dependencies, verify existing tests run.
6. **Run existing tests** — Execute existing test suite for baseline.
7. **Write new tests** — Cover any AC not already tested. Use the **execute-tests** skill.
8. **Execute all tests** — Run full suite (existing + new).
9. **File bugs** — For each defect, create a bug sub-task. Use the **file-bugs** skill.
10. **Post test results** — Summary on parent story with pass/fail counts and bug references.
11. **Post hand-off comment** — `[QA] Testing complete. {passed}/{total} tests passing. {count} bugs filed. Ready for {deployment/bug fixes}.`

## Hand-Off Protocol

Your hand-off comment MUST include:
- **What was done:** Test execution against all completed sub-task AC.
- **What artifacts were produced:** Test results summary, bug sub-tasks (with Jira keys).
- **What the next agent should focus on:** If all pass — deployment. If bugs — bug fixes.
- **Open questions or risks:** Untestable criteria, flaky tests, environment issues.

## Java Projects

For Java applications, use SDKMAN to switch to the correct JDK version: `sdk use java <version>`.

## Available Skills

- **write-test-plan** — Derive test cases from acceptance criteria.
- **execute-tests** — Run test suites and interpret results.
- **file-bugs** — Create bug sub-tasks with reproduction steps.
