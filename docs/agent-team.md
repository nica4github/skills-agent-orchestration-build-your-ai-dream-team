# Agent team

This repository defines a small custom agent team in `.github/agents` to build Mona's Project Pulse dashboard. The Orchestrator delegates scoped work to three specialists; none of the agents stage, commit, or push changes — the learner controls git through Copilot CLI prompts.

- Orchestrator
  - Model: Claude Opus 4.7 (copilot)
  - Role: Breaks the dashboard request into phases, assigns explicit file scopes, manages dependencies, and verifies the integrated result.
  - Def: `.github/agents/orchestrator.agent.md`

- Planner
  - Model: Claude Opus 4.7 (copilot)
  - Role: Researches the codebase, enumerates steps, edge cases, file ownership, and produces an actionable plan the Orchestrator can use.
  - Def: `.github/agents/planner.agent.md`

- Coder
  - Model: GPT-5.5 (copilot)
  - Role: Implements code within the Orchestrator-assigned scope. For Project Pulse the Coder will create runnable support (e.g., `.vscode/launch.json` with cwd set to `app` and open `index.html`) and validate changes.
  - Def: `.github/agents/coder.agent.md`

- Designer
  - Model: Gemini 3.1 Pro (copilot)
  - Role: Produces dashboard UX, responsive layout, CSS hooks (e.g. `.dashboard`, `.project-card`), accessible styling, and visual polish for Project Pulse.
  - Def: `.github/agents/designer.agent.md`

See each `.agent.md` under `.github/agents/` for the full execution rules, tools, and delegation behaviors used during development.
