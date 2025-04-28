## 📘 Personal GitHub Guide 

---

## 1. Introduction

### Brief History and Philosophy

GitHub was launched in 2008 by Tom Preston-Werner, Chris Wanstrath, and PJ Hyett as a web-based hosting service for Git repositories. Git, the underlying version control system, was created by Linus Torvalds in 2005 to manage the development of the Linux kernel. GitHub combines Git's powerful version control capabilities with a user-friendly interface, facilitating collaboration and code sharing among developers.

### Core Philosophy

- **Collaboration**: Encouraging open-source contributions and teamwork.
- **Transparency**: Maintaining a clear history of changes and discussions.
- **Efficiency**: Streamlining development workflows through integrations and automation.

---

## 2. GitHub Basics

### Creating a Repository

```bash
# Initialize a new Git repository
git init

# Add a remote repository
git remote add origin https://github.com/username/repository.git
```

### Cloning a Repository

```bash
# Clone an existing repository
git clone https://github.com/username/repository.git
```

### Making Changes

```bash
# Check the status of your working directory
git status

# Add changes to the staging area
git add filename

# Commit changes with a message
git commit -m "Your commit message"
```

### Pushing Changes

```bash
# Push changes to the remote repository
git push origin main
```

### Deleting a Branch

```bash
# Delete a local branch
git branch -d branch_name

# Force delete a local branch
git branch -D branch_name

# Delete a remote branch
git push origin --delete branch_name
```

### Renaming a Branch

```bash
# Rename the current branch
git branch -m new-branch-name

# Rename a different branch
git branch -m old-branch-name new-branch-name

# Push the renamed branch to remote
git push origin new-branch-name

# Delete the old branch from remote
git push origin --delete old-branch-name
```


---

## 3. Branching and Merging

### Creating and Switching Branches

```bash
# Create a new branch
git branch feature-branch

# Switch to the new branch
git checkout feature-branch

# Or create and switch in one command
git checkout -b feature-branch
```

### Merging Branches

```bash
# Switch to the branch you want to merge into
git checkout main

# Merge the feature branch into main
git merge feature-branch
```

### Resolving Merge Conflicts

```bash
# After a conflict, edit the files to resolve issues
# Then add the resolved files
git add resolved-file

# Commit the merge
git commit
```

### Stashing Changes

```bash
# Save your local modifications temporarily
git stash

# Apply the latest stash
git stash apply

# List all stashed changes
git stash list

# Drop a specific stash
git stash drop stash@{0}
```

### Rebasing

```bash
# Rebase your current branch onto main
git checkout feature-branch
git rebase main

# Abort a rebase if something goes wrong
git rebase --abort
```

Rebasing replays commits from one branch onto another, creating a cleaner history.

---

## 4. Pull Requests

### Creating a Pull Request

1. Push your feature branch to GitHub.
2. Navigate to the repository on GitHub.
3. Click on "Compare & pull request".
4. Add a title and description.
5. Click "Create pull request".

### Reviewing and Merging Pull Requests

- **Review**: Comment on specific lines, approve, or request changes.
- **Merge**: Choose between merge commit, squash and merge, or rebase and merge.

---

## 5. Issues and Project Management

### Creating an Issue

1. Navigate to the "Issues" tab.
2. Click "New issue".
3. Provide a title and description.
4. Submit the issue.

### Labels and Milestones

- **Labels**: Categorize issues (e.g., bug, enhancement).
- **Milestones**: Group issues for a specific release or goal.

### Projects

Use GitHub Projects to organize tasks using Kanban-style boards.

---

## 6. GitHub Actions

### Overview

GitHub Actions enables automation of workflows directly in your repository.

### Creating a Workflow

```yaml
# .github/workflows/ci.yml
name: CI

on:
  push:
    branches: [ main ]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Set up Node.js
        uses: actions/setup-node@v2
        with:
          node-version: '14'
      - run: npm install
      - run: npm test
```

### Common Use Cases

- **CI/CD Pipelines**: Automate builds, tests, and deployments.
- **Code Linting**: Run code formatters or linters on every push.
- **Dependency Updates**: Use Dependabot integration.
- **Notifications**: Send Slack or email notifications on certain events.

### Advanced Concepts

- **Matrix Builds**: Test across multiple environments.
- **Reusable Workflows**: Share workflows across repositories.
- **Secrets Management**: Store sensitive data securely for use in workflows.

---

## 7. Security Features

### Dependabot

Automatically scans dependencies for vulnerabilities and opens pull requests to update them.

### Secret Scanning

Detects accidentally committed secrets like API keys and tokens.

### Code Scanning

Analyzes code for security vulnerabilities using tools like CodeQL.

---

## 8. Advanced Features

### Git Log & History Navigation

```bash
# View commit history
git log

# Show a specific commit
git show commit_hash

# Compare changes between commits
git diff commit1 commit2

# Annotate each line with commit info
git blame filename
```

### Tags and Releases

```bash
# Create a lightweight tag
git tag v1.0

# Create an annotated tag
git tag -a v1.0 -m "Version 1.0"

# Push tags to the remote repository
git push origin v1.0
```

On GitHub, releases can be created via the UI based on tags for distributing software packages.

### Forking and Upstream Sync

```bash
# Add upstream repository
git remote add upstream https://github.com/original-owner/repo.git

# Fetch updates from upstream
git fetch upstream

# Merge upstream changes into local branch
git merge upstream/main
```

### Submodules

```bash
# Add a submodule
git submodule add https://github.com/username/repo.git path/to/submodule

# Initialize and update submodules
git submodule update --init --recursive
```

### Git Hooks

Hooks allow you to automate tasks at specific points in Git workflows.

```bash
# Example: pre-commit hook
# Place script in .git/hooks/pre-commit

#!/bin/sh
npm run lint
```

### Cherry-pick Commits

```bash
# Apply a specific commit from another branch
git cherry-pick commit_hash
```

### Squashing Commits

```bash
# Interactively squash commits
git rebase -i HEAD~3
```

### Git Configurations

```bash
# View global config
git config --global --list

# Set user name and email
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

### Reverting and Resetting

```bash
# Revert a specific commit (safe)
git revert commit_hash

# Reset to a previous commit (destructive)
git reset --hard commit_hash
```

### GitHub Pages

Host static websites directly from your repository.

### Wikis

Create comprehensive documentation within your repository.

### GitHub CLI

Interact with GitHub from the command line.

```bash
# Install GitHub CLI
gh auth login

# Create a new issue
gh issue create

# View pull requests
gh pr list
```

---

## 9. Practical Examples

### Hello World Repository

1. Create a new repository on GitHub.
2. Clone it locally:

```bash
git clone https://github.com/username/hello-world.git
```

3. Navigate into the directory and create a README:

```bash
cd hello-world
echo "# Hello World" > README.md
```

4. Commit and push the changes:

```bash
git add README.md
git commit -m "Add README"
git push origin main
```

### Simple GitHub Action for Linting

```yaml
# .github/workflows/lint.yml
name: Lint Code Base

on: [push, pull_request]

jobs:
  lint:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v2
      - name: Run ESLint
        run: |
          npm install
          npm run lint
```

---

## 10. Common Errors and Best Practices

### Common Errors and Troubleshooting

1. **Permission Denied (Publickey)**
   - Cause: SSH key not configured properly.
   - Solution:

   ```bash
   ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
   ssh-add ~/.ssh/id_rsa
   # Add the public key (~/.ssh/id_rsa.pub) to your GitHub account.
   ```

2. **Merge Conflicts**
   - Cause: Concurrent changes in the same part of a file.
   - Solution:

   ```bash
   # Edit conflicted files manually, then:
   git add conflicted-file
   git commit
   ```

3. **Detached HEAD State**
   - Cause: Checking out a specific commit instead of a branch.
   - Solution:

   ```bash
   git checkout branch_name
   ```

4. **Rebase Conflicts**
   - Cause: Changes between branches conflict during rebase.
   - Solution:

   ```bash
   # Resolve conflicts, then continue rebase
   git rebase --continue
   # Or abort rebase
   git rebase --abort
   ```

5. **Push Rejected (Non-Fast-Forward)**
   - Cause: Remote branch has new commits.
   - Solution:

   ```bash
   git pull --rebase origin branch_name
   git push origin branch_name
   ```

---

### Good Practices and Recommendations

1. **Commit Messages**
   - Use clear, concise messages:
   
   ```
   feat: add new authentication flow
   fix: resolve issue with user login
   docs: update README with setup instructions
   ```

2. **Branch Naming Conventions**
   - Use descriptive names:
   
   ```
   feature/add-login
   bugfix/fix-header-alignment
   hotfix/critical-security-patch
   ```

3. **Use Pull Requests for All Changes**
   - Ensure code reviews, even for small updates.

4. **Keep Branches Short-Lived**
   - Frequently merge back to main branches to avoid large conflicts.

5. **Enable Required Reviews and CI Checks**
   - Configure branch protection rules in GitHub settings.

6. **Avoid Force Push on Shared Branches**
   - Only force push to local or isolated branches.

7. **Tag Releases Consistently**
   - Use semantic versioning:
   
   ```
   v1.0.0, v1.1.0, v2.0.0
   ```

8. **Keep Dependencies Updated**
   - Use Dependabot or similar tools for automated updates.

9. **Automate Workflows**
   - Use GitHub Actions for CI/CD, linting, testing, and deployments.

10. **Backup Important Branches**
    - Regularly push to remote repositories.
