Status: DRAFT

Context:
- The user asked to publish the current repository to a new private GitHub repository under https://github.com/lyraqin named `my-claude-code`.
- The repo already has `origin` pointing to `https://github.com/lyraqin/Claude.git`, so publishing requires creating the new remote, retargeting push settings, and ensuring no tracked files violate repository rules before pushing.

Approach:
1. Verify the working tree is clean (`git status`) and no untracked files need to be committed before pushing; collect any special instructions scanned so far (e.g., plan-first policies and `papers/` immutability) to avoid accidental changes.
2. Use `gh repo create lyraqin/my-claude-code --private --source=. --remote=origin` (or create the repo via the web if gh is unavailable) to provision the target GitHub repository and configure it as the new `origin`. Authenticate via `gh auth login` if necessary.
3. Update the `origin` remote URL (or replace the remote) so it points to the newly created repository; ensure `.git/config` reflects the change but do not edit tracked files directly.
4. Push the local branches/tags (`git push origin HEAD`, `git push --tags`) so the new GitHub repo mirrors the current main branch.
5. Confirm the push succeeded through `git remote -v`, `git fetch origin`, and `gh repo view lyraqin/my-claude-code` (or via web) to check the commit history.

Files to modify:
- `.git/config` (via `git remote set-url`) to point `origin` at `https://github.com/lyraqin/my-claude-code.git`. No tracked source files should be edited for this task.

Verification:
- Run `git status` to ensure clean working tree.
- Run `git remote -v` and `gh repo view lyraqin/my-claude-code` to confirm `origin` is correctly set and the repo exists as private.
- After pushing, check the GitHub repo page to verify the commit history and files match the local tree.
