# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

## [1.2.0] - 2026-11-22

### Added
- Mandatory Feature Branch Policy across all agent frameworks: agents must always create and switch to a dedicated feature branch (`feat/<name>` or `feature/<name>`) for any Git repository where work occurs, and always commit directly to that feature branch.
- Explicit deviation boundary: agents are strictly forbidden from committing directly to `main`/`master` unless the user specifically and explicitly commands a deviation.
- GitHub Copilot Agent structure enhancements:
  - Added `.github/agents/pipeline.agent.md` custom Copilot agent profile (`@pipeline`).
  - Added `.github/prompts/strict-pipeline.prompt.md` prompt file for executable Copilot Agent workflows.
  - Added `.github/instructions/git-safety.instructions.md` modular instruction applying Git safety across all workspaces.
  - Added `AGENT.md` & `AGENTS.md` universal protocol files for GitHub Copilot, Claude, Cursor, and Windsurf agent alignment.
- Formal feature specification document `v1.2.0-mandatory-feature-branching.md`.

### Changed
- Updated canonical specification in `codingPlanAndExecute.md` (Phase 3 & Phase 5) with feature branch auto-checkout and commit enforcement.
- Synchronized Google Antigravity workspace rules (`.gemini/rules.md`) and global plugin rules (`AGENTS.md` & `SKILL.md`).
- Synchronized Claude Code (`.claude/CLAUDE.md`), GitHub Copilot (`.github/copilot-instructions.md`), Cursor (`.cursorrules`, `.cursor/rules/strict-pipeline.mdc`), and Windsurf (`.windsurfrules`).
- Updated `MEMORY.md` to persist the mandatory feature branch preference across sessions.
- Updated `README.md` to highlight the feature branch safety policy.

## [1.1.0] - 2026-11-22

### Added
- Feature parity for GitHub Copilot in `.github/copilot-instructions.md` with `[quick]` and `[auto]` operational tag guidance.
- Modern Cursor IDE rule definition `.cursor/rules/strict-pipeline.mdc` supporting glob matchers and `alwaysApply: true`.
- `.gitignore` file safeguarding environment secrets, OS artifacts, and temporary debug files.
- `package.json` manifest specifying project metadata and SemVer version tracking.
- Git repository initialization and remote origin binding to `https://github.com/abhishek4official/CodingAgent.git`.

### Changed
- Renamed canonical specification file from `codeingPlanAndExecure.md` to `codingPlanAndExecute.md` fixing typo.
- Updated `README.md` with official repository link and corrected file references.

## [1.0.0] - 2026-11-22

### Added
- Initial release of the 5-phase strict gated coding pipeline.
- Cross-agent configurations for Google Antigravity (`.gemini/rules.md`), Claude Code (`.claude/CLAUDE.md`, `.claude/settings.json`), GitHub Copilot (`.github/copilot-instructions.md`), Cursor (`.cursorrules`), and Windsurf (`.windsurfrules`).
- Long-term memory tracking template in `MEMORY.md`.
- Canonical pipeline definition in `codingPlanAndExecute.md`.
