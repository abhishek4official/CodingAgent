# Project Long-Term Memory

This file preserves architectural patterns, gotchas, framework quirks, and team preferences across AI agent sessions. Agents must inspect this file in Phase 1 and record new insights in Phase 5.

---

## 1. Architecture Patterns & Design Decisions
<!-- Record key architectural designs, patterns, and structure choices here. -->
- Cursor dual-rule strategy: Modern `.cursor/rules/*.mdc` (supporting `globs: *` and `alwaysApply: true`) paired with root `.cursorrules` for complete backwards compatibility.
- GitHub Copilot multi-tier structure: Repository instructions (`.github/copilot-instructions.md`), path instructions (`.github/instructions/*.instructions.md`), prompt templates (`.github/prompts/*.prompt.md`), custom agent specialist profiles (`.github/agents/*.agent.md`), and universal root manifests (`AGENTS.md`, `AGENT.md`).
- Canonical pipeline rules are standardized in `codingPlanAndExecute.md` and projected across Antigravity, Claude Code, GitHub Copilot, Cursor, and Windsurf.

---

## 2. Gotchas, Quirks & Known Issues
<!-- Record edge cases, unexpected runtime behaviors, package bugs, or OS-specific workarounds. -->
- Windows PowerShell 5.1 does not support the `&&` statement separator in commands; use `;` instead.
- Pre-staging git safety checks require testing that `.gitignore` patterns match sensitive files.

---

## 3. Project Conventions & Standards
<!-- Record testing preferences, doc locations, manifest conventions, or lint rules. -->
- Documentation specs follow: `[REF-ID]-[feature-name].md` or `[vVersion]-[feature-name].md`.
- Versions are tracked via SemVer in manifest (`package.json`) and synced to `CHANGELOG.md`.
- Remote repository URL: `https://github.com/abhishek4official/CodingAgent.git`.
- Featured in Portfolio / Resume: `https://github.com/abhishek4official/abhishek4official.github.io` (live at `https://abhishek4official.github.io/`).

---

## 4. User & Workflow Preferences
<!-- Record explicit developer preferences, CLI tool choices, or style mandates. -->
- Strict 5-Phase gated workflow enforced for non-trivial features.
- Mandatory Feature Branch Policy: Always create and commit to a feature branch (`feat/<name>`) for any Git project where working; never commit directly to `main`/`master` unless explicitly commanded by the user.
- Never push to git remote without explicit user command.
