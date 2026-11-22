# Agentic Coding Protocol (AGENT.md)

Universal protocol and operating instructions for AI coding agents (GitHub Copilot, Google Antigravity, Claude Code, Cursor, and Windsurf).

> **Note:** This file serves as the singular alias for [AGENTS.md](AGENTS.md) to ensure universal compatibility across agents and tool configurations.

## Operational Modes & Override Tags
- **Standard (Default):** Execute all 5 phases with mandatory approval gates.
- **`[quick]` Tag:** For trivial single-line or typo fixes, merge Phase 1 (Spec) and Phase 2 (Plan) into a single proposal.
- **`[auto]` Tag:** Execute Phase 1 through Phase 3 autonomously; pause only at Gate 3 for diff review and pre-commit approval.

---

## The 5-Phase Gated Pipeline

### Phase 1: Requirement Alignment & Scope (GATE 1)
- Inspect codebase in read-only mode; inspect `MEMORY.md` if available.
- Formulate technical specification:
  - Functional objective & acceptance criteria.
  - Affected components and files.
  - Assumptions, constraints, and edge cases.
  - Reference / Ticket ID (if available).
- **GATE 1 (STOP):** Present the specification and ask:
  *"Do you approve this specification, or would you like to adjust scope/assumptions?"*
  *(Do not design implementation steps or write code until approved).*

---

### Phase 2: Implementation Plan & Documentation Strategy (GATE 2)
- Formulate step-by-step implementation plan:
  - Exact files to create, edit, or delete.
  - Architectural / logic flow changes.
  - Dependencies or environment variables to add.
  - **Version Bump Strategy:** SemVer update target (`patch`, `minor`, `major`) in manifest files (`package.json`, `pyproject.toml`, `Cargo.toml`, etc.).
  - **Documentation Strategy:**
    - Manifests and `CHANGELOG.md` updates.
    - Spec naming rule: `[REF-ID]-[feature-name].md` or `[vVersion]-[feature-name].md`.
  - Verification & test plan.
- **GATE 2 (STOP):** Present the plan and ask:
  *"Do you approve this implementation plan and documentation strategy?"*
  *(Do not touch filesystem, create files, or install dependencies until approved).*

---

### Phase 3: Implementation, Documentation & Verification
- **Branch Verification & Auto-Checkout:**
  - If working within a Git repository, check `git branch --show-current`.
  - If on `main`, `master`, or base branch, **create and check out a dedicated feature branch** (`git checkout -b feat/<name>`).
  - Always commit to the feature branch; only deviate if the user specifically and explicitly requests.
- Adhere strictly to the approved plan. If an architectural deviation is needed, stop and return to Phase 2.
- Bump project version in manifests/lockfiles and update `CHANGELOG.md`.
- Run tests and linters using non-interactive flags (`--yes`, `--no-pager`, `--ci`).
- **Circuit Breaker:** If tests fail after **3 attempts**, STOP immediately, report failure details, and ask for guidance.

---

### Phase 4: Diff Review & Iteration (GATE 3)
- Present concise summary of code diffs, documentation, and verification outputs.
- **GATE 3 (STOP):** Ask:
  *"Are you satisfied with these changes, docs, and version bump, and ready to commit?"*
  *(Do not stage or commit until approved).*

---

### Phase 5: Memory Retention & Safe Git Commit
- Update `MEMORY.md` with new architectural discoveries or gotchas.
- Check `git status` and `git branch --show-current`. Ensure no secrets or `.env` files are included.
- **Mandatory Feature Branch:** Always commit into a feature branch (`feat/<name>`). Never commit directly to `main`/`master` unless the user specifically and explicitly commands a deviation.
- Stage intentional files and commit using Conventional Commits (e.g. `feat(v1.2.0): ...`).
- **NEVER** run `git push` unless explicitly requested by the user.
