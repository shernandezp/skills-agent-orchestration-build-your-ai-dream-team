# Agent Team

This document describes the custom agent team orchestrated via **GitHub Copilot CLI in a Codespace** to build Mona's Project Pulse dashboard.

## Agents

### Orchestrator
- **Model:** Claude Opus 5.5 (copilot)
- **Definition:** `.github/agents/orchestrator.agent.md`
- **Responsibility:** Coordinates Planner, Coder, and Designer agents. Breaks down complex requests into phases, delegates to specialists, manages parallel and sequential task execution, and verifies integration.

### Planner
- **Model:** Claude Opus 5.5 (copilot)
- **Definition:** `.github/agents/planner.agent.md`
- **Responsibility:** Creates implementation plans through codebase research, documentation review, and dependency analysis. Produces ordered steps, file assignments, parallelization opportunities, and edge case identification without writing code.

### Coder
- **Model:** GPT-5.5 (copilot)
- **Definition:** `.github/agents/coder.agent.md`
- **Responsibility:** Implements code-oriented tasks with explicit error handling and testable behavior. Writes application logic, support configuration, and validates changes within assigned file scope. For Project Pulse, creates `.vscode/launch.json` and ensures the dashboard is runnable.

### Designer
- **Model:** Gemini 3.7 Flash (copilot)
- **Definition:** `.github/agents/designer.agent.md`
- **Responsibility:** Handles UI/UX, accessibility, information architecture, and visual design. Creates a polished dashboard with project cards, status badges, responsive layout, and deterministic CSS hooks—ensuring the first view clearly looks like a Project Pulse dashboard.

## Orchestration

The Orchestrator receives the user request, coordinates the team through phases, manages file ownership to prevent conflicts, and ensures the integrated result meets all requirements. Planner, Coder, and Designer work sequentially or in parallel based on file scope and data dependencies, all orchestrated through the **GitHub Copilot CLI** running in a **Codespace** environment.
