# Changelog

All notable changes to this project will be documented in this file.

The format is based on [Keep a Changelog](https://keepachangelog.com/en/1.1.0/),
and this project adheres to [Semantic Versioning](https://semver.org/spec/v2.0.0.html).

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
