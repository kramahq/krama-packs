# krama-packs

First-party packs for [Krama](https://github.com/kramahq/krama): versioned agent teams, installed from git. A pack is a directory with a `krama-pack.yaml` that names one orchestrator and the agents it can call. The method (how the team works) is the orchestrator's prompt; nothing about phases or gates is built into Krama.

> **Status:** early development (`0.1.0` packs). They validate against Krama's real backends and install from git; they have not been run end to end against live agents yet.

| Pack | What it does | Agents |
|---|---|---|
| [`sdlc`](sdlc) | Takes a Jira story through analysis, design, development, review and testing. A person approves the requirements and the design. | analyst, architect, developer, reviewer, qa, and a read-only second reviewer taken from the a2a-wrapper repository |
| [`tech-debt`](tech-debt) | Fixes a security or dependency finding with the smallest safe change. A person approves the plan before any code changes. | security-architect, patch-developer, reviewer, qa |
| [`ai-dlc`](ai-dlc) | The AI-Driven Development Life Cycle (Ideation, Inception, Construction, Operation) with a person validating at each gate. | 11 domain agents and 2 reviewers |
| [`deck`](deck) | Turns source files and a brief into a presentation: a briefing, an outline you approve, then a self-contained HTML deck. | researcher, writer, designer |

## Installing

In Krama, install by source: `https://github.com/kramahq/krama-packs.git`, a ref (a tag, or a commit to pin) and the pack's directory as the path, for example `sdlc`. Krama shows what the pack asks for (network, MCP servers, secrets) before anything is installed, and installs only what you consented to. Agents a pack takes from another repository are pinned to a commit in the pack file.

## What the packs need

- **Backends.** The orchestrators use `a2a-claude`. `sdlc` and `tech-debt` run their specialists on `a2a-copilot`, as the originals did; `ai-dlc` and `deck` use `a2a-claude` throughout. A backend must be installed and allowed by policy.
- **The MCP gateway (`sdlc`, `tech-debt`).** The specialists reach Jira, Bitbucket and, for `tech-debt`, SonarQube, Black Duck and Artifactory through MCP servers at the addresses the original Software Factory used: `127.0.0.1:4300/servers/<name>/sse` for the gateway and `localhost:4104/mcp` for Bitbucket. Those addresses are shown as network permissions when you install. Edit the pack (or fork it) if your servers are elsewhere. No credential is stored in a pack.
- **Credentials.** Packs hold no secrets. The backends read theirs from the environment or from the bindings you give at install.

## Layout

```
<pack>/
  krama-pack.yaml          the pack: orchestrator, agents, who may call whom
  agents/<agent>/...       the instructions and skills an agent's config points at
  README.md
```

Licensed under [Apache-2.0](LICENSE).
