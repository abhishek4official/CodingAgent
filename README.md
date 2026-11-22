# Strict Agentic Coding Pipeline & Multi-Agent Setup

[![GitHub Repository](https://img.shields.io/badge/GitHub-CodingAgent-blue?logo=github)](https://github.com/abhishek4official/CodingAgent)
[![Version](https://img.shields.io/badge/version-1.2.0-green.svg)](package.json)

A universal, deterministic 5-phase software development pipeline with safety gates, test circuit-breakers, version synchronization, and long-term memory for AI coding agents (**Antigravity**, **Claude Code**, **GitHub Copilot**, **Cursor**, and **Windsurf**).

---

## Repository
- **Official GitHub Repository:** [https://github.com/abhishek4official/CodingAgent](https://github.com/abhishek4official/CodingAgent)

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

```powershell
cd c:\Users\abhis\Documents\CodeingAgentAndPypeline
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
