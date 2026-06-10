## Step 1: Meet the agent team

Welcome to **Agent Orchestration: Build Your AI Dream Team**!

Mona's team needs a small **Project Pulse** dashboard. You will use GitHub Copilot CLI to coordinate a prebuilt team of custom agents that can plan, design, code, and validate the dashboard.

### What is the goal?

The goal is not to write every file with one prompt. The goal is to practice orchestration:

- The **Orchestrator** coordinates the request.
- The **Planner** creates implementation phases and file ownership.
- The **Designer** guides the dashboard experience.
- The **Coder** implements the static app files.

The custom agent definitions are already available in `.github/agents/`. Your first task is to inspect that team and document how you will use it.

### :keyboard: Activity: Open the repository and start Copilot CLI

1. Fork this repository to your own GitHub account if you have not already forked it.

   Do not create branches or commit directly in the original repository. All workshop changes should stay in a branch in your fork.

1. Clone your fork to your machine if you have not already cloned it:

   ```bash
   # Clone your fork of this prepared workshop repository and enter its folder.
   git clone https://github.com/<your-github-username>/skills-agent-orchestration-build-your-ai-dream-team.git
   cd skills-agent-orchestration-build-your-ai-dream-team
   ```

1. Open the cloned repository in VS Code.

1. Before making changes, create your own participant branch in your fork:

   ```bash
   # Create a participant branch for your lab work.
   git switch -c participant/<your-name>
   ```

1. Open the integrated terminal and start GitHub Copilot CLI.

> [!NOTE]
> If you are not already in the Copilot CLI interactive mode, run this command.

   ```bash
   copilot --allow-all --enable-all-github-mcp-tools
   ```

1. If prompted, use `/login` to authenticate.

> [!NOTE]
> If multiline input is awkward in your terminal, run `/terminal-setup` inside Copilot CLI.

### :keyboard: Activity: Inspect the custom agents

1. Ask Copilot CLI to inspect the agent definitions:

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Inspect .github/agents/ and summarize the custom agent team I will use to build
   > Mona's Project Pulse dashboard.
   >
   > Update the replace text in `docs/agent-team.md`.
   > ```

1. Update `docs/agent-team.md` with:

   - Orchestrator, Planner, Coder, and Designer.
   - The model assigned to each agent.
   - The responsibility of each agent.
   - The `.github/agents/` file for each agent.
   - How the team will work together to build Project Pulse.

1. Save the file.

1. Ask Copilot CLI to stage, commit, and push your work. Copy and paste this prompt into the Copilot CLI interactive mode:

   > ![Static Badge](https://img.shields.io/badge/-Prompt-text?style=social&logo=github%20copilot)
   >
   > ```prompt
   > Stage docs/agent-team.md.
   >
   > Commit it with the message "Document the Project Pulse agent team".
   >
   > Push the commit to my fork.
   > ```

1. After pushing your commit, continue with the next step.

<details>
<summary>Having trouble? 🤷</summary><br/>

- Make sure you updated `docs/agent-team.md`.
- Make sure the file references `.github/agents/`.
- Make sure the file includes all four agent names.
- Make sure the file uses the updated models: Opus 4.7, GPT-5.5, and Gemini 3.1 Pro.
- Make sure you pushed your commit to your fork.

</details>

---

### Navigation

- Next: [Step 2](2-step.md)
- [Back to README](../../README.md)
