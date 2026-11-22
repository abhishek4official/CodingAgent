# Antigravity Workspace Rules: Gated Coding Pipeline

Follow this 5-phase engineering protocol for non-trivial development tasks.

## Operational Modes
- **Default:** Execute all 5 phases with strict user approval gates.
- **`[quick]` Tag:** For simple bugfixes or single-line modifications, merge Phases 1 & 2 into a single confirmation.
- **`[auto]` Tag:** Execute Phases 1 through 3 autonomously; pause only at Gate 3 for diff review and pre-commit approval.

---

## Phase 1: Requirement Alignment & Scope (GATE 1)
- Explore files in read-only mode; consult `MEMORY.md`.
- Formulate a precise technical specification:
  - Functional objective & acceptance criteria.
  - Affected components and files.
  - Assumptions, constraints, and edge cases.
  - Reference / Ticket ID (if available).
- **GATE 1 (STOP):** Present the specification and ask:
  *"Do you approve this specification, or would you like to adjust scope/assumptions?"*
  *(Do not proceed with detailed implementation planning or code edits until approved).*

---

## Phase 2: Implementation Plan & Documentation Strategy (GATE 2)
- Formulate step-by-step implementation plan:
  - Exact files to create, edit, or delete.
  - Architectural / logic flow changes.
  - Dependencies or environment variables to add.
  - **Version Bump Strategy:** SemVer update target (`patch`, `minor`, `major`) in manifest files.
  - **Documentation Strategy:**
    - Manifests and `CHANGELOG.md` updates.
    - Spec naming rule: `[REF-ID]-[feature-name].md` or `[vVersion]-[feature-name].md`.
  - Verification & test plan.
- **GATE 2 (STOP):** Present the plan and ask:
  *"Do you approve this implementation plan and documentation strategy?"*
  *(Do not touch filesystem, create files, or install dependencies until approved).*

---

## Phase 3: Implementation, Documentation & Verification
- If working within a Git repository, check `git branch --show-current`. If on `main`/`master`, create and checkout a feature branch (`feat/<name>`). Always commit to feature branch; only deviate if user specifically requests.
- Follow approved plan strictly. If an architectural deviation is needed, stop and return to Phase 2.
- Bump project version in manifests/lockfiles and update `CHANGELOG.md`.
- Run tests and linters using non-interactive flags (`--yes`, `--no-pager`, `--ci`).
- **Circuit Breaker:** If tests fail after **3 attempts**, STOP immediately, report failure details, and ask for guidance.

---

## Phase 4: Diff Review & Iteration (GATE 3)
- Present concise summary of code diffs, documentation, and verification outputs.
- **GATE 3 (STOP):** Ask:
  *"Are you satisfied with these changes, docs, and version bump, and ready to commit?"*
  *(Do not stage or commit until approved).*

---

## Phase 5: Memory Retention & Safe Git Commit
- Update `MEMORY.md` with new architectural discoveries or gotchas.
- Check `git status` and `git branch --show-current`. Ensure no secrets or `.env` files are included.
- **Mandatory Feature Branch:** Always commit into a feature branch (`feat/<name>`). Never commit directly to `main`/`master` unless the user specifically and explicitly commands a deviation.
- Stage intentional files and commit using Conventional Commits (e.g. `feat(v1.2.0): ...`).
- **NEVER** run `git push` unless explicitly requested by the user.
