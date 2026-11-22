# Project Guidelines & Strict Agentic Pipeline (Claude Code)

## Operational Modes
- **Standard (Default):** Follow all 5 phases with mandatory approval gates.
- **`[quick]` Tag:** For trivial single-file fixes or typos, combine Phase 1 & 2 into one proposal.
- **`[auto]` Tag:** Run through Phase 1 to Phase 3 autonomously; stop only at Gate 3 (Diff Review & Pre-Commit).

---

## 5-Phase Gated Execution Pipeline

### Phase 1: Requirement Alignment & Scope
1. Inspect files in read-only mode; read `MEMORY.md` for known patterns.
2. Produce a technical specification: Objective, Affected Files, Assumptions/Edge Cases, and Reference ID.
3. **GATE 1 (STOP):** Ask: *"Do you approve this specification, or would you like to adjust scope/assumptions?"*

### Phase 2: Implementation Plan & Documentation Strategy
1. Present detailed plan:
   - Files to create/edit/delete.
   - Version bump target (SemVer in manifests: `package.json`, `pyproject.toml`, `Cargo.toml`, etc.).
   - Documentation updates (`CHANGELOG.md` and `[REF-ID]-[feature-name].md` or `[vVersion]-[feature-name].md`).
   - Verification commands and test scope.
2. **GATE 2 (STOP):** Ask: *"Do you approve this implementation plan and documentation strategy?"*

### Phase 3: Implementation & Verification
1. Adhere strictly to the approved plan. If unexpected blockers occur, halt and return to Phase 2.
2. Run linters and tests with non-interactive flags (`--yes`, `--no-pager`, `--ci`).
3. **Circuit Breaker:** If tests or checks fail after **3 attempts**, STOP, report failures, and await user direction.

### Phase 4: Diff Review & Iteration
1. Present diff summary, docs updated, and test pass/fail results.
2. **GATE 3 (STOP):** Ask: *"Are you satisfied with these changes, docs, and version bump, and ready to commit?"*

### Phase 5: Memory Retention & Safe Git Commit
1. Append any new architectural insights or quirks into `MEMORY.md`.
2. Inspect `git status`. Verify no secrets, credentials, or `.env` files are staged.
3. If on a protected branch (`main`/`master`), ask before committing.
4. Create a conventional commit referencing version (e.g., `feat(v1.2.0): ...`). Never push to remote without explicit request.
