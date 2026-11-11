# Git and GitHub — Documentation

## 1. Version control

Version control records changes to files over time so earlier versions can be inspected, compared and recovered. It helps track modifications, identify who made changes and when, restore earlier versions, and support collaboration.

### Types of version control systems

1. **Local VCS:** versions are managed on one computer.
2. **Centralized VCS:** a central server stores project history. Example: SVN.
3. **Distributed VCS:** each clone contains repository history. Example: Git.

## 2. Git vs GitHub

- **Git** is a distributed version control system. It tracks changes and maintains project history through commits.
- **GitHub** is an online hosting and collaboration platform for Git repositories. It provides features such as pull requests, Issues and code review.

Git can be used locally without a network. GitHub's online features require connectivity.

## 3. Installation and configuration

Download Git for Windows, macOS or Linux from https://git-scm.com/downloads.

Check installation:

```bash
git --version
```

Configure the author identity used in commits:

```bash
git config --global user.name "Your Name"
git config --global user.email "your-email@example.com"
git config --global --list
```

These values identify the commit author; they do not authenticate you to GitHub.

## 4. Repository basics

A Git repository stores project history and tracking metadata. Git stores this metadata in the hidden `.git` directory.

Create a directory and initialize it:

```bash
mkdir my-project
cd my-project
git init
```

The three main areas are:

1. **Working directory:** files being edited.
2. **Staging area:** selected changes prepared for the next commit.
3. **Repository:** committed project history.

## 5. Basic Git workflow

```bash
git status
git add filename
git commit -m "Describe the change"
git log
```

- `git status` displays the state of the working directory and staging area.
- `git add` stages the current contents of a file.
- `git commit` records staged changes in the local repository.
- `git log` displays commit history.

Stage all changes in the current directory:

```bash
git add .
```

Stage selected files:

```bash
git add file1.py file2.py
git add *.py
```

Changes made after staging must be staged again.

## 6. Inspecting changes and history

```bash
git log
git log --oneline
git diff
git diff --staged
git diff HEAD
git ls-files
```

- `git diff`: unstaged changes to tracked files.
- `git diff --staged`: staged changes.
- `git diff HEAD`: tracked changes relative to the current commit.
- `git ls-files`: files known to Git's index; untracked files are normally not listed.

## 7. Ignoring files

Create a `.gitignore` file to specify intentionally untracked files and directories.

Example:

```gitignore
__pycache__/
*.pyc
.env
*.log
data/
```

Common uses include temporary files, caches, local environment configuration, logs and generated outputs. Adding a file to `.gitignore` does not remove it from history if it was already committed.

## 8. Renaming and deleting files

```bash
git mv old.py new.py
git rm old.py
```

- `git mv` stages a move or rename.
- `git rm` removes a tracked file from the working directory and stages its removal.

Git detects renames by comparing file contents; rename is not a separate fundamental object type.

## 9. Undoing changes

### Unstage a file while preserving working-directory edits

```bash
git restore --staged filename
```

### Discard unstaged modifications to a tracked file

```bash
git restore filename
```

**Warning:** the second command discards unstaged modifications and they may be difficult or impossible to recover. Inspect with `git diff` first.

### Revert a commit safely

```bash
git log --oneline
git revert COMMIT_ID
```

`git revert` creates a new commit that reverses the changes introduced by an earlier commit. It preserves existing history and is often suitable for undoing published changes.

## 10. GitHub and remote repositories

Create a repository on GitHub. A remote connects a local repository to a hosted repository.

```bash
git remote add origin REPOSITORY_URL
git remote -v
```

Replace `REPOSITORY_URL` with the actual repository URL.

Rename the current branch to `main` and push:

```bash
git branch -M main
git push -u origin main
```

`-u` sets the upstream tracking relationship.

Clone a remote repository:

```bash
git clone REPOSITORY_URL
```

Fetch and pull:

```bash
git fetch origin
git pull
```

- `git fetch` downloads remote updates without integrating them into the current branch.
- `git pull` fetches and integrates updates into the current branch, typically by merging or rebasing according to configuration.

## 11. Branches

A branch is an independent line of development. It allows work to happen without directly modifying another branch.

```bash
git branch
git branch feature-login
git switch feature-login
git switch main
git switch -c feature-login
```

- `git branch` lists local branches.
- `git branch feature-login` creates a branch but does not switch to it.
- `git switch` changes the current branch.
- `git switch -c` creates and switches to a branch.

The current branch is marked with an asterisk when running `git branch`.

## 12. Merging and merge conflicts

Merge a feature branch into `main`:

```bash
git switch main
git merge feature-login
```

The branch currently checked out is the target branch.

A merge conflict occurs when Git cannot automatically combine competing changes. Open the conflicted file, decide which changes to keep or combine, remove conflict markers, then stage the resolved file and complete the merge.

Example conflict markers:

```text
<<<<<<< HEAD
result = 10
=======
result = 20
>>>>>>> feature-login
```

After editing the file to the intended final content:

```bash
git add filename
git status
git commit
```

If Git has already prepared a merge commit, `git commit` completes it. Follow Git's prompt if it specifies another action.

## 13. Pull requests, forks and code review

A **pull request (PR)** proposes changes for review and integration into another branch on a hosting platform.

Typical process:

1. Push a feature branch to GitHub.
2. Open a pull request against the target branch.
3. Explain the changes.
4. Request reviews and run checks.
5. Address feedback and merge when approved.

A pull request is not the same as the local `git pull` command.

A **fork** is a separate hosted copy of a repository under another account or namespace. A **clone** creates a local copy of a repository, including its Git history.

Code review checks correctness, identifies bugs, suggests improvements and verifies tests and readability.

## 14. Tags and releases

A tag identifies a point in repository history, often to mark a software version.

```bash
git tag
git tag -a v1.0.0 -m "Version 1.0.0"
git show v1.0.0
git push origin v1.0.0
```

Semantic versioning commonly follows `MAJOR.MINOR.PATCH`. GitHub Releases can attach notes and downloadable files to a version tag.

## 15. Merge vs rebase

Example commands:

```bash
git switch main
git merge feature
```

```bash
git switch feature
git rebase main
```

- **Merge** combines branch histories, may create a merge commit, and preserves existing commits.
- **Rebase** replays commits on a new base, rewrites commit identities and can produce a linear history.

Avoid rebasing shared commits unless the team understands the consequences of rewriting history.

## 16. GitHub Issues and Projects

- **Issues** track bugs, features, questions and tasks.
- **Projects** organize work and track progress using views such as tables or boards.

## 17. Authentication and security

GitHub connections can use HTTPS or SSH. Never commit passwords, API keys or private tokens. Review repository visibility and access permissions. A `.gitignore` entry does not erase a secret that has already entered Git history.

## 18. Best practices

1. Commit changes frequently and logically.
2. Write clear commit messages.
3. Use descriptive branch names.
4. Review changes before committing.
5. Pull or fetch updates regularly.
6. Test changes before merging.
7. Keep credentials and unnecessary generated files out of the repository.
8. Maintain a useful README.

## 19. Practical command checklist

Use this checklist to practise the commands from the lecture:

- [ ] `git --version`
- [ ] `git config --global user.name "Your Name"`
- [ ] `git config --global user.email "you@example.com"`
- [ ] `git config --global --list`
- [ ] `git init`
- [ ] `git status`
- [ ] `git add filename`
- [ ] `git add .`
- [ ] `git commit -m "message"`
- [ ] `git log`
- [ ] `git log --oneline`
- [ ] `git diff`
- [ ] `git diff --staged`
- [ ] `git diff HEAD`
- [ ] `git ls-files`
- [ ] `git mv old.py new.py`
- [ ] `git rm filename`
- [ ] `git restore --staged filename`
- [ ] `git restore filename` (only on a disposable test change)
- [ ] `git revert COMMIT_ID` (practise in a test repository)
- [ ] `git remote add origin REPOSITORY_URL`
- [ ] `git remote -v`
- [ ] `git branch -M main`
- [ ] `git push -u origin main`
- [ ] `git clone REPOSITORY_URL`
- [ ] `git fetch origin`
- [ ] `git pull`
- [ ] `git branch`
- [ ] `git branch feature-login`
- [ ] `git switch feature-login`
- [ ] `git switch main`
- [ ] `git switch -c feature-login`
- [ ] `git merge feature-login`
- [ ] `git tag`
- [ ] `git tag -a v1.0.0 -m "Version 1.0.0"`
- [ ] `git show v1.0.0`
- [ ] `git push origin v1.0.0`
- [ ] `git rebase main`

## 20. Mini-project: version-controlled calculator

The lecture's mini-project asks students to create a calculator, initialize Git, commit the first version, publish it on GitHub, implement a feature on a branch, and submit that feature through a pull request.

### Initialize

```bash
mkdir calculator
cd calculator
git init
```

Create `main.py`:

```python
print("Calculator")
a = 10
b = 5
print("Sum:", a + b)
```

### Record the first version

```bash
git status
git add main.py
git status
git commit -m "Add initial calculator"
git log --oneline
```

### Publish on GitHub

Create an empty GitHub repository named `calculator` for this exercise, then:

```bash
git branch -M main
git remote add origin REPOSITORY_URL
git push -u origin main
```

### Add subtraction on a feature branch

```bash
git switch -c feature-subtraction
```

Add this line to `main.py`:

```python
print("Difference:", a - b)
```

Then:

```bash
git add main.py
git commit -m "Add subtraction feature"
git push -u origin feature-subtraction
```

Open a pull request on GitHub with base branch `main` and compare branch `feature-subtraction`. Review and merge it.

Finally, update local `main`:

```bash
git switch main
git pull origin main
```

## References

- Class lecture: *Version Control Tools: Git and GitHub — Concepts, Commands, and Collaborative Development*, Prof. Neeta Nain, MNIT Jaipur, 12 October 2026.
- Official Git documentation: https://git-scm.com/docs
- Git downloads: https://git-scm.com/downloads
- GitHub: https://github.com/
