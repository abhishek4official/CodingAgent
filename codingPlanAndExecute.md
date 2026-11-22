# Strict Agentic Coding Pipeline

Follow this 5-phase pipeline in exact order for all non-trivial coding tasks. Do NOT proceed past a **GATE** or **STOP** condition without explicit user approval.

## Operational Modes & Override Tags
- **Standard (Default):** Follow all 5 phases with mandatory stop gates.
- **`[quick]` Tag:** For trivial single-file/typo fixes, combine Phases 1 & 2 into a single confirmation step.
- **`[auto]` Tag:** Proceed through Phase 1 to Phase 3 autonomously; pause only at Gate 3 (Diff & Commit Review).

---

## Phase 1: Requirement Alignment & Scope
1. Explore relevant files in read-only mode to understand context and existing patterns.
2. Check for existing project memory (`MEMORY.md` or `.agent/memory.md`) to adhere to known quirks and conventions.
3. Rewrite the user's request into a precise technical specification:
   - Functional objective & expected behavior
   - Likely affected files/components
   - Constraints, assumptions, and edge cases
   - Issue/ticket reference number (if available)
4. If anything is ambiguous, list questions alongside the specification.

**GATE 1:** STOP. Present the specification and ask: 
*"Do you approve this specification, or would you like to adjust scope/assumptions?"*
Do not design detailed implementation steps or write code until approved.

---

## Phase 2: Implementation Plan & Documentation Strategy
1. Detail a concise, step-by-step **Implementation Plan**:
   - Exact files to create, edit, or delete
   - Architectural/logic changes
   - New dependencies, environment variables, or destructive/migration commands required
   - **Version Bump Strategy:** Target version update (SemVer: major/minor/patch) in manifest files (`package.json`, `pyproject.toml`, `Cargo.toml`, etc.)
   - **Documentation & Spec Files:** Target docs to create/update (`CHANGELOG.md`, `README.md`, release/feature specs)
   - Verification plan (unit/integration tests or manual reproduction script)
2. Note any pre-existing issues or breaking changes this could cause.

**GATE 2:** STOP. Ask: 
*"Do you approve this implementation plan and documentation strategy?"* 
Do not create, edit files, or install dependencies until approved.

---

## Phase 3: Implementation, Documentation & Verification
1. **Code Implementation:** Implement changes strictly adhering to the approved plan.
   - If you hit an unexpected blocker that requires deviating from the approved plan, **STOP and return to Phase 2**.
2. **Version Bump & Documentation Sync:**
   - Bump the project version in manifest and lock files.
   - Update `CHANGELOG.md` and relevant technical docs.
   - **Document Naming Rule:** When creating or renaming feature/release documentation or specs:
     - **If a reference number is provided:** Name file as `[REF-ID]-[feature-name].md` (e.g., `PROJ-142-jwt-auth.md`).
     - **If NO reference number is provided:** Name/rename file as `[vVersion]-[feature-name].md` (e.g., `v1.3.0-jwt-auth.md`).
3. **Testing & Checks:**
   - Add or update tests covering the new functionality and edge cases.
   - Run the targeted test suite, linter, and type checks using non-interactive flags (`--yes`, `--no-pager`, `--ci`).
   - **Circuit Breaker:** If target checks still fail after **3 attempts**, **STOP**, report the failure, and ask for guidance.
   - If tests fail due to pre-existing, unrelated codebase issues, report them immediately instead of attempting out-of-scope fixes.

---

## Phase 4: Diff Review & Iteration
1. Present a concise review summary:
   - Summary of code changes and updated version
   - Documentation created/renamed and updated
   - Verification results (test commands run and pass/fail outputs)
2. Ask the user for feedback. If requested, apply adjustments, re-verify, and present updated diffs.

**GATE 3:** STOP. Ask: 
*"Are you satisfied with these changes, docs, and version bump, and ready to commit?"* 
Do not stage or commit until explicitly approved.

---

## Phase 5: Memory Retention & Safe Git Commit
1. **Memory Retention:**
   - Record any new architectural discoveries, gotchas, framework quirks, or user preferences into `MEMORY.md` so context is preserved across future sessions.
2. **Pre-Staging Safety Check:**
   - Check `git branch --show-current`, `git status`, and `git diff --stat`.
   - Ensure only intentional files (code, tests, docs, version manifests, memory) are staged; leave pre-existing unrelated modified files untouched.
   - Verify no secrets, `.env` files, credentials, or temporary debug artifacts are included.
   - If currently on a protected branch (e.g., `main`/`master`), **STOP and ask whether to commit directly or create a new branch first**.
3. **Commit Execution:**
   - Verify local author info (`git config user.name`, `git config user.email`). Do NOT inject AI attributions or custom trailers unless requested.
   - Stage changes and craft a conventional commit message referencing the new version (e.g., `feat(v1.3.0): add JWT auth and update docs`).
   - **Do NOT push to remote unless explicitly asked.**
4. Output the commit hash, branch name, and commit summary.
