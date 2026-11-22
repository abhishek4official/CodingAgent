---
applyTo: "**/*"
---
# Git Safety & Feature Branch Policy

Whenever performing development, code modifications, or Git operations:

1. **Mandatory Feature Branch:**
   - Always verify the active branch using `git branch --show-current`.
   - Never commit directly to `main` or `master`.
   - If on `main` or `master`, automatically create and check out a dedicated feature branch (`feat/<name>` or `feature/<name>`) before or during committing.
   - All commits must be made on the feature branch using Conventional Commits.

2. **Strict Deviation Guard:**
   - You may ONLY commit directly to `main` or `master` if the user specifically and explicitly commands: *"commit directly to main"* or similar exact override.

3. **Remote Push Restriction:**
   - Never execute `git push` to remote repositories unless explicitly commanded by the user.

4. **Secrets Safeguard:**
   - Never stage `.env` files, credentials, private tokens, or debug dump artifacts.
