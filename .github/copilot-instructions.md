# GitHub Copilot Workspace Instructions

## Operational Modes
- **Standard (Default):** Follow all 5 phases with mandatory approval gates.
- **`[quick]` Tag:** For trivial single-file fixes or typos, combine Phase 1 & 2 into one proposal.
- **`[auto]` Tag:** Run through Phase 1 to Phase 3 autonomously; stop only at Gate 3 (Diff Review & Pre-Commit).

---

## Agent Behavior: Strict 5-Phase Pipeline

When handling non-trivial coding tasks, follow this structured, gated workflow:

### 1. Scope & Requirement Alignment (Gate 1)
- Examine existing files and `MEMORY.md` in read-only mode first.
- Clarify functional objectives, affected files, assumptions, and edge cases.
- **Stop & Confirm:** Request user approval before drafting implementation code or modifying files.

### 2. Plan & Versioning Strategy (Gate 2)
- Outline exact file modifications, architectural logic changes, and test strategies.
- Specify the SemVer bump target (`patch`, `minor`, `major`) in project manifests.
- Specify documentation updates (`CHANGELOG.md` and `[REF-ID]-[feature-name].md` or `[vVersion]-[feature-name].md`).
- **Stop & Confirm:** Request user approval for the implementation plan and documentation strategy.

### 3. Execution & Verification Circuit Breaker
- Implement changes following the approved plan.
- Execute test suites and linters.
- **Circuit Breaker:** Stop immediately if tests fail 3 consecutive times to prevent circular edits.
- Never edit unrelated files to bypass failing pre-existing tests.

### 4. Review Gate (Gate 3)
- Present a concise diff summary, version update, and verification outcome.
- **Stop & Confirm:** Ask for explicit approval before any git staging or commit operations.

### 5. Memory & Git Boundaries
- Record lasting architectural gotchas in `MEMORY.md`.
- **Mandatory Feature Branch:** In all Git projects, always create and commit into a dedicated feature branch (`feat/<name>`). Never commit directly to `main`/`master` unless user specifically and explicitly commands a deviation.
- Ensure no secrets, `.env` files, or unintended files are staged.
- Never execute `git push` unless explicitly commanded.
