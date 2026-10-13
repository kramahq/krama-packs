# tech-debt

Fixes one security or dependency finding raised as a Jira ticket, with the smallest safe change.

**Team.** `lead` (orchestrator, Claude) calls: `security-architect` (researches the finding and checks the upgrade is safe, then files sub-tasks), `patch-developer` (applies one sub-task, nothing else, and opens a pull request), `reviewer` and `qa`.

**How a run goes.** Research first. A person approves the plan (findings, proposed upgrades, risks, sub-tasks) before any code changes. The patch developer fixes only what it is assigned and logs anything else it sees without acting on it; the reviewer sends back a change that goes beyond the assignment. Review or test problems loop back to the patch, within the platform's loop cap.

**Needs.** Jira and Bitbucket MCP servers, plus SonarQube, Black Duck and Artifactory for the security architect (see the repository README for the addresses), and the `a2a-copilot` and `a2a-claude` backends.

**Differences from the original Tech Debt Terminator.** The security architect and patch developer playbooks are one long document each in their original form; they are kept whole as instructions, minus the parts about the old runtime's messaging. The Tavily web-search server the original architect used is not included: it needs an API key, which a pack must not carry. Add a search server and a secret binding if you want it.

**Inputs.** The request text: the ticket key and any instructions.
