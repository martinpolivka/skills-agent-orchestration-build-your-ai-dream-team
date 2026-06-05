# Agent team

The following custom agents collaborate to build **Mona's Project Pulse** dashboard.  
Work is orchestrated from **GitHub Copilot CLI running in a Codespace**.

| Agent | Model | Definition | Responsibility |
|-------|-------|-----------|----------------|
| **Orchestrator** | Claude Opus 4.7 | `.github/agents/orchestrator.agent.md` | Coordinates Planner, Coder, and Designer. Breaks requests into phased tasks, delegates with explicit file scopes, and verifies the integrated result. |
| **Planner** | Claude Opus 4.7 | `.github/agents/planner.agent.md` | Researches the codebase and produces implementation plans with ordered steps, file assignments, dependencies, edge cases, and validation expectations. |
| **Coder** | GPT-5.5 | `.github/agents/coder.agent.md` | Implements code-oriented tasks—writes logic, fixes bugs, creates support files (e.g., `.vscode/launch.json`), and validates changes. |
| **Designer** | Gemini 3.1 Pro | `.github/agents/designer.agent.md` | Handles UI/UX, accessibility, information architecture, interaction flow, and visual design including responsive layout and CSS hooks. |

> **Note:** GitHub Copilot CLI in a Codespace acts as the human-in-the-loop orchestration layer, invoking these agents and controlling all git operations.
