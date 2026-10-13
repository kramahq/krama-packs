# deck

Turns source files and a brief into a presentation.

**Team.** `lead` (orchestrator, Claude) calls `researcher` (reads the attached files and writes a briefing with the evidence), `writer` (the outline, then the slides and speaker notes) and `designer` (a single self-contained HTML deck with keyboard navigation, print styles and inline SVG charts).

**How a run goes.** Research, then an outline. A person approves the outline before the deck is built. The lead checks every number on a slide against the briefing and sends work back if it does not match.

**Output.** `deck/deck.html` in the run's workspace, with the briefing, outline and slide text beside it.

**Inputs.** The request text and attached files (documents, spreadsheets, data), and optionally `audience`, `slides` (about how many) and `tone`.

**Needs.** The `a2a-claude` backend. No MCP servers.
