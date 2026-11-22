# Strict Agentic Coding Pipeline & Multi-Agent Setup

[![GitHub Repository](https://img.shields.io/badge/GitHub-CodingAgent-blue?logo=github)](https://github.com/abhishek4official/CodingAgent)
[![Version](https://img.shields.io/badge/version-1.2.0-green.svg)](package.json)
[![Architecture Guide](https://img.shields.io/badge/Architecture_Guide-abhishek4official.github.io%2Fai--agents-0ea5e9?style=flat-square&logo=googlechrome&logoColor=white)](https://abhishek4official.github.io/ai-agents/)
[![llms.txt](https://img.shields.io/badge/llms.txt-Documented-emerald?style=flat-square)](https://abhishek4official.github.io/llms.txt)

A universal, deterministic 5-phase software development pipeline with safety gates, test circuit-breakers, version synchronization, and long-term memory for AI coding agents (**Antigravity**, **Claude Code**, **GitHub Copilot**, **Cursor**, and **Windsurf**).

---

## 📖 Architecture & Design Documentation
For an in-depth technical breakdown of the 5-phase deterministic engineering protocol, automated test circuit breakers, and cross-harness parity across Antigravity, Claude Code, Cursor, Copilot, and Windsurf, visit the official architecture hub:

👉 **[https://abhishek4official.github.io/ai-agents/](https://abhishek4official.github.io/ai-agents/)**

### Related AI Architecture Hubs
* **[Model Context Protocol (MCP) Developer Guide](https://abhishek4official.github.io/mcp/)** — Open standard for connecting AI agents to external tools, databases, and prompts.
* **[Agent Frameworks Evaluation](https://abhishek4official.github.io/agent-frameworks/)** — Comparing Microsoft Agent Framework (Semantic Kernel + AutoGen) vs LangGraph vs DAG orchestrators.
* **[Local AI & Private Systems](https://abhishek4official.github.io/local-ai/)** — Running local multi-agent systems via Ollama without cloud subscriptions.

---

## Repository
- **Official GitHub Repository:** [https://github.com/abhishek4official/CodingAgent](https://github.com/abhishek4official/CodingAgent)
- **Live Architecture & Portfolio:** [https://abhishek4official.github.io/](https://abhishek4official.github.io/)

---

## Folder & Configuration Structure

```
.
├── .claude/
│   ├── CLAUDE.md                    # Claude Code configuration & pipeline instructions
│   └── settings.json                # Claude Code permissions & safety settings
├── .cursor/
│   └── rules/
│       └── strict-pipeline.mdc      # Modern Cursor IDE rule definition (v0.40+)
├── .gemini/
│   └── rules.md                     # Antigravity workspace rules
├── .github/
│   ├── agents/                      # Custom Copilot agent profiles
│   │   └── pipeline.agent.md        # @pipeline custom agent specialist
│   ├── copilot-instructions.md      # GitHub Copilot workspace instructions
│   ├── instructions/                # Modular path-specific instructions
│   │   └── git-safety.instructions.md
│   └── prompts/                     # Executable prompt templates for Copilot
│       └── strict-pipeline.prompt.md
├── .cursorrules                     # Cursor AI IDE configuration (legacy fallback)
├── .gitignore                       # Safeguard against secrets & temp files
├── .windsurfrules                   # Windsurf IDE Cascade configuration
├── AGENT.md                         # Universal agent protocol (singular alias)
├── AGENTS.md                        # Universal agent persona and pipeline protocol
├── CHANGELOG.md                     # Project release changelog & version history
├── MEMORY.md                        # Persistent cross-session project memory
├── package.json                     # Metadata manifest & SemVer version tracker
├── README.md                        # Installation, setup, and usage guide
└── codingPlanAndExecute.md          # Canonical pipeline specification
```

---

## Tool-by-Tool Installation & Setup Guide

### 1. Claude (Claude Code CLI)

Claude Code detects configuration files in `.claude/CLAUDE.md`.

#### **Installation**
Ensure you have Node.js (v18+) installed, then install the Claude Code CLI globally:

```powershell
npm install -g @anthropic-ai/claude-code
```

#### **Authentication & Launch**
Navigate to this repository root and launch Claude:

```bash
cd path/to/CodingAgent
claude
```
- On first launch, follow the browser login prompt to authenticate with Anthropic.
- Claude Code will automatically read [`.claude/CLAUDE.md`](.claude/CLAUDE.md).

---

### 2. Google Antigravity

Antigravity auto-discovers workspace rules in `.gemini/rules.md`.

#### **Setup**
1. Open this repository in the Antigravity IDE / workspace.
2. Antigravity will automatically load:
   - Rules: [`.gemini/rules.md`](.gemini/rules.md)
3. No manual installation is needed; the pipeline is active by default.

---

### 3. GitHub Copilot

GitHub Copilot Agent supports a multi-tiered architecture for instructions, prompt templates, and path-specific rules:

#### **Setup**
1. Install the **GitHub Copilot** and **GitHub Copilot Chat** extensions in VS Code or JetBrains.
2. Sign in to your GitHub account and open this folder.
3. Copilot automatically loads:
   - **Custom Specialist Agent:** [`.github/agents/pipeline.agent.md`](.github/agents/pipeline.agent.md) (`@pipeline` in chat)
   - **Workspace Instructions:** [`.github/copilot-instructions.md`](.github/copilot-instructions.md)
   - **Path Instructions:** [`.github/instructions/git-safety.instructions.md`](.github/instructions/git-safety.instructions.md)
   - **Prompt Template:** Select or invoke prompt templates from [`.github/prompts/strict-pipeline.prompt.md`](.github/prompts/strict-pipeline.prompt.md)
   - **Universal Agent Manifest:** [`AGENTS.md`](AGENTS.md) / [`AGENT.md`](AGENT.md) at root

---

### 4. Cursor

Cursor automatically reads `.cursorrules` and `.cursor/rules/*.mdc` for its Agent / Composer mode.

#### **Setup**
1. Open this workspace in Cursor (`cursor .`).
2. When chatting in **Composer** (Ctrl+I / Cmd+I) or **Agent mode**, Cursor automatically incorporates `.cursor/rules/strict-pipeline.mdc` and [`.cursorrules`](.cursorrules).

---

### 5. Windsurf

Windsurf Cascade auto-detects `.windsurfrules` in the workspace root.

#### **Setup**
1. Open this project in Windsurf.
2. Cascade will automatically adopt the instructions defined in [`.windsurfrules`](.windsurfrules).

---

## How to Use the Pipeline

When asking any agent to work on a task, simply state your goal. The agent will execute through 5 distinct phases:

```
[Phase 1: Spec] ──> (GATE 1: Stop for approval)
       │
[Phase 2: Plan & Docs] ──> (GATE 2: Stop for approval)
       │
[Phase 3: Code & Test] ──> (Circuit Breaker: Stop after 3 failures)
       │
[Phase 4: Diff Review] ──> (GATE 3: Stop for commit approval)
       │
[Phase 5: Memory & Git Commit] ──> (Local commit only; never auto-pushes)
```

### Operational Tags / Shortcuts

You can prefix your prompts to adjust the strictness of the gates:

| Prompt Tag | Behavior | Best Used For |
| :--- | :--- | :--- |
| *(None / Default)* | Strictly stops at Gate 1, Gate 2, and Gate 3. | Features, refactors, architectural tasks. |
| `[quick] <prompt>` | Merges Phase 1 & 2 into a single confirmation. | Typos, 1-line fixes, small config adjustments. |
| `[auto] <prompt>` | Runs Phases 1–3 autonomously; stops only at Gate 3 (Diff review). | Fast prototyping when you only want to review final diffs before commit. |

---

## Automated Installation Prompts (For AI Agents)

You can copy and paste the meta-prompts below directly into **any AI coding assistant** (Google Antigravity, Claude Code, GitHub Copilot, Cursor, Windsurf, or Aider) to have the agent autonomously install and configure this pipeline for you:

### 1. Project-Specific Installation (Single Repository)
Use this prompt inside an existing or new project to have your agent pull and configure the full pipeline:

```text
Please install and configure the 5-phase strict agentic coding pipeline from https://github.com/abhishek4official/CodingAgent.git into this current project:
1. Detect and configure rules for all coding agents supported in this workspace:
   - Google Antigravity: .gemini/rules.md
   - Claude Code: .claude/CLAUDE.md & .claude/settings.json
   - Cursor: .cursorrules & .cursor/rules/strict-pipeline.mdc
   - GitHub Copilot: .github/copilot-instructions.md, .github/instructions/git-safety.instructions.md, .github/prompts/strict-pipeline.prompt.md, and .github/agents/pipeline.agent.md
   - Windsurf: .windsurfrules
2. Copy root AGENTS.md, AGENT.md, and canonical codingPlanAndExecute.md.
3. Initialize MEMORY.md if it doesn't already exist.
4. Enforce the Mandatory Feature Branch Policy: ensure agents always create a feature branch (feat/<name>) for any work and never commit directly to main/master unless explicitly requested.
```

### 2. Global Machine-Level Installation (All Workspaces)
Use this prompt to instruct your agent to configure the pipeline globally across your entire development environment:

```text
Please configure the strict 5-phase agentic coding pipeline from https://github.com/abhishek4official/CodingAgent.git globally on this machine:
1. Claude Code: Set up the global pipeline instructions in ~/.claude/CLAUDE.md.
2. Google Antigravity: Install the pipeline as a global custom rule or plugin in ~/.gemini/.
3. GitHub Copilot: Configure global chat custom instructions in user-level VS Code settings.
4. Cursor / Windsurf: Add the 5-phase pipeline to global user rules.
5. Guarantee that the Mandatory Feature Branching Policy (always creating feat/<name> and never committing directly to main/master) is activated across all projects.
```

---

## Documentation & Memory Rules

1. **Feature Spec Naming Convention:**
   - If reference ticket exists: `[REF-ID]-[feature-name].md` (e.g. `PROJ-142-jwt-auth.md`).
   - If no reference ticket exists: `[vVersion]-[feature-name].md` (e.g. `v1.3.0-jwt-auth.md`).
2. **Project Memory (`MEMORY.md`):**
   - The agent inspects [`MEMORY.md`](MEMORY.md) during Phase 1 to remember past quirks and preferences.
   - The agent appends newly discovered patterns and gotchas during Phase 5.
3. **Git Branch & Commit Safety:**
   - **Mandatory Feature Branch:** For all Git projects, agents automatically create and switch to a dedicated feature branch (`feat/<name>`) and commit to it. Committing directly to `main`/`master` is forbidden unless the user specifically and explicitly commands a deviation.
   - **No Auto-Push:** The agent will never execute `git push` to remote repositories unless explicitly commanded by you.
