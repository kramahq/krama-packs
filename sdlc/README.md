# sdlc

Takes one Jira story from analysis to tested pull requests.

**Team.** `lead` (orchestrator, Claude) plans the work and calls: `analyst`, `architect`, `developer`, `reviewer`, `qa`. The `reviewer` can ask `code-reviewer` for a second, read-only opinion; that agent is the wrapper's own `a2a-claude/agents/read-only-reviewer`, taken from [`a2a-wrapper`](https://github.com/shashikanth-gs/a2a-wrapper) at a pinned commit (see `krama-pack.yaml`; update the pin on purpose).

**How a run goes.** The lead sets a plan (refinement, design, development, review, testing). A person approves the requirements and the design before development starts. A review that asks for changes, or QA finding bugs, loops back to the developer; the platform caps the loops. The lead keeps the Jira story's status and comments up to date.

**Needs.** Jira and Bitbucket MCP servers (see the repository README) and the `a2a-copilot` and `a2a-claude` backends.

**Differences from the original Software Factory.** The phases, gates and loop rules that the engine used to hold are now the lead's prompt. The devops, documenter and clarifier agents are not included yet. The specialists no longer use a `store_artifact` tool (they return their deliverable and the lead keeps it) and the memory and terminal MCP servers are dropped: the backends have their own file and shell tools in the workspace.

**Inputs.** The request text: a Jira story key and any instructions.
