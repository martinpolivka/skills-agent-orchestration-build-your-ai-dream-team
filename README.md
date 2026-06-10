# Agent Orchestration: Build Your AI Dream Team

_Use custom agents in GitHub Copilot CLI to plan, design, build, and validate a small dashboard._

## Welcome

GitHub Copilot CLI brings an agentic coding assistant directly into your terminal. In this exercise, you will use prebuilt custom agents in a local VS Code workspace to orchestrate planning, design, coding, and validation for Mona's Project Pulse dashboard.

- **Who is this for**: Developers who have basic GitHub and GitHub Copilot familiarity and want to learn how to coordinate specialist agents from the terminal.
- **What you'll learn**: How to use GitHub Copilot CLI locally to inspect custom agents, ask an Orchestrator to involve specialist agents, plan implementation phases, build a small dashboard, and validate the final result.
- **What you'll build**: A runnable Project Pulse dashboard with `app/index.html`, `app/styles.css`, `app/project-data.json`, and `.vscode/launch.json`, plus planning and handoff notes in `docs/`.
- **How long**: This exercise takes less than one hour to complete.

### Local prerequisites

Before you start, make sure your computer has:

- [Git](https://git-scm.com/) and a GitHub.com account that can fork this public repository.
- [Visual Studio Code](https://code.visualstudio.com/) with an integrated terminal.
- GitHub Copilot access for your GitHub account.
- [GitHub CLI](https://cli.github.com/) installed and authenticated with `gh auth login`.
- GitHub Copilot CLI installed, or permission to install it during Step 1:
  - Windows: `winget install GitHub.Copilot`
  - macOS and Linux with Homebrew: `brew install copilot-cli`
  - macOS and Linux with the official install script: `curl -fsSL https://gh.io/copilot-install | bash`
- Python 3.13 or later for previewing the static dashboard with `python3 -m http.server`.
- Network access to GitHub and the Copilot service.

In this exercise, you will:

1. Start GitHub Copilot CLI in a local VS Code terminal.
1. Inspect the Orchestrator, Planner, Coder, and Designer files under `.github/agents/`.
1. Use the Orchestrator and Planner to create a Project Pulse implementation plan.
1. Use the Orchestrator to delegate dashboard design and coding work.
1. Build the dashboard files, create a VS Code launch configuration, run the dashboard, and validate the result.
1. Summarize the final coordinated handoff.

### How to start this exercise

Before making any changes, fork this repository to your own GitHub account. Do not create branches or commit directly in the original repository. Create your participant branch in your fork. Use a branch name that identifies you, for example `participant/<your-name>`.

Continue with [Step 1](.github/steps/1-step.md).

Further steps:

- [Step 2](.github/steps/2-step.md)
- [Step 3](.github/steps/3-step.md)
- [Step 4](.github/steps/4-step.md)
- [Review](.github/steps/x-review.md)

---

&copy; 2026 GitHub &bull; [Code of Conduct](https://www.contributor-covenant.org/version/2/1/code_of_conduct/code_of_conduct.md) &bull; [MIT License](https://gh.io/mit)
