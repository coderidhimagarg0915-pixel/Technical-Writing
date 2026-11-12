# Git Command Quick Reference

Commands below are based on the TW Git lecture.

| Purpose | Command |
|---|---|
| Check version | `git --version` |
| Set author name | `git config --global user.name "Ridhima Garg"` |
| Set author email | `git config --global user.email "coderidhimagarg0915@gmail.com"` |
| View configuration | `git config --global --list` |
| Initialize repository | `git init` |
| Check status | `git status` |
| Stage one file | `git add filename` |
| Stage all changes | `git add .` |
| Commit staged changes | `git commit -m "message"` |
| Full history | `git log` |
| Compact history | `git log --oneline` |
| Unstaged diff | `git diff` |
| Staged diff | `git diff --staged` |
| Changes from HEAD | `git diff HEAD` |
| List indexed files | `git ls-files` |
| Rename/move | `git mv old.py new.py` |
| Remove tracked file | `git rm filename` |
| Unstage but preserve edits | `git restore --staged filename` |
| Discard unstaged edits | `git restore filename` |
| Revert a commit | `git revert COMMIT_ID` |
| Add remote | `git remote add origin REPOSITORY_URL` |
| List remotes | `git remote -v` |
| Rename current branch | `git branch -M main` |
| Push and set upstream | `git push -u origin main` |
| Clone | `git clone REPOSITORY_URL` |
| Fetch | `git fetch origin` |
| Pull | `git pull` |
| List branches | `git branch` |
| Create branch | `git branch feature-login` |
| Switch branch | `git switch feature-login` |
| Create and switch | `git switch -c feature-login` |
| Merge branch into current branch | `git merge feature-login` |
| List tags | `git tag` |
| Create annotated tag | `git tag -a v1.0.0 -m "Version 1.0.0"` |
| Show tag | `git show v1.0.0` |
| Push tag | `git push origin v1.0.0` |
| Rebase feature on main | `git switch feature` then `git rebase main` |

## Safety notes

- `git restore filename` discards unstaged changes. Practise only on disposable changes.
- `git revert COMMIT_ID` creates a new commit; it does not erase the old commit.
- `git rebase` rewrites commit identities. Avoid rebasing shared commits without agreement.
- Never commit passwords, API keys or private tokens.
