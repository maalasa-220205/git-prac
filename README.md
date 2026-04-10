# Git Practice Repository

A comprehensive guide and practice resource for mastering Git commands at an industry level. This repository covers everything from basic configuration to advanced operations, providing practical examples and commands for daily development workflows.

## 📋 Table of Contents

1. [Git Configuration and Environment Setup](#git-configuration-and-environment-setup)
2. [Repository Creation and Inspection](#repository-creation-and-inspection)
3. [File Tracking and Staging](#file-tracking-and-staging)
4. [Commit Management and History Navigation](#commit-management-and-history-navigation)
5. [Branching and Branch Management](#branching-and-branch-management)
6. [Merging and Conflict Resolution](#merging-and-conflict-resolution)
7. [Remote Repository Operations](#remote-repository-operations)
8. [Stashing and Workspace Management](#stashing-and-workspace-management)
9. [Resetting, Undoing, and Recovering Changes](#resetting-undoing-and-recovering-changes)
10. [Rebasing and History Rewriting](#rebasing-and-history-rewriting)
11. [Cherry-picking and Patch Management](#cherry-picking-and-patch-management)
12. [Tagging and Release Management](#tagging-and-release-management)
13. [Submodule Integration](#submodule-integration)
14. [Debugging and Troubleshooting with Git](#debugging-and-troubleshooting-with-git)

---

## Git Configuration and Environment Setup

### Setting Up Your Git Identity

```bash
# Set your global username
git config --global user.name "Your Name"

# Set your global email
git config --global user.email "your.email@example.com"

# Set local repository username (overrides global)
git config user.name "Local Name"

# Set local repository email (overrides global)
git config user.email "local.email@example.com"
```

### Viewing Git Configuration

```bash
# View all global configurations
git config --global --list

# View all local configurations
git config --local --list

# View a specific configuration value
git config user.name
```

### Useful Git Configuration Aliases

```bash
# Create command shortcuts
git config --global alias.st status
git config --global alias.co checkout
git config --global alias.br branch
git config --global alias.cm commit
git config --global alias.log-graph "log --graph --oneline --all"
```

### Setting Default Editor and Tools

```bash
# Set default text editor
git config --global core.editor "vim"

# Set merge tool
git config --global merge.tool "vimdiff"

# Enable color output
git config --global color.ui true
```

---

## Repository Creation and Inspection

### Creating a New Repository

```bash
# Initialize a new Git repository
git init

# Create a new repository with a specific branch name
git init --initial-branch=main

# Clone an existing repository
git clone <repository-url>

# Clone into a specific directory
git clone <repository-url> <directory-name>

# Clone a specific branch
git clone --branch <branch-name> <repository-url>
```

### Inspecting Repository Information

```bash
# View repository status
git status

# Show short status format
git status -s

# Display repository configuration
git config --list

# Show remote repository information
git remote -v

# Get information about a specific remote
git remote show origin

# View repository statistics
git rev-parse --show-toplevel  # Show repository root
git rev-parse HEAD              # Show current commit hash
git rev-list --count HEAD       # Count total commits
```

---

## File Tracking and Staging

### Tracking Files

```bash
# Add a specific file to staging area
git add <filename>

# Add all changes to staging area
git add .

# Add all changes interactively
git add -i

# Stage untracked files only
git add -u

# Add changes by patch (choose specific hunks)
git add -p

# Add changes with force
git add -f
```

### Viewing File Changes

```bash
# Show unstaged changes
git diff

# Show staged changes
git diff --staged

# Show changes in a specific file
git diff <filename>

# Show differences between branches
git diff <branch1> <branch2>

# Show word-level changes
git diff --word-diff
```

### Removing and Moving Files

```bash
# Remove a file from working directory and staging
git rm <filename>

# Remove a file only from staging
git rm --cached <filename>

# Rename or move a file
git mv <old-path> <new-path>

# Rename with force overwrite
git mv -f <old-path> <new-path>
```

---

## Commit Management and History Navigation

### Creating Commits

```bash
# Commit staged changes
git commit -m "Commit message"

# Commit with detailed message
git commit -m "Title" -m "Description"

# Commit all changes (tracked files only)
git commit -am "Commit message"

# Commit allowing empty message
git commit --allow-empty-message

# Amend the last commit
git commit --amend

# Amend without editing the message
git commit --amend --no-edit
```

### Viewing Commit History

```bash
# View commit history
git log

# View commit history in one line
git log --oneline

# View commit history with graph visualization
git log --graph --oneline --all

# View commits by specific author
git log --author="Author Name"

# View commits in a date range
git log --since="2 weeks ago" --until="1 week ago"

# View commits that changed a specific file
git log -p <filename>

# Show commit statistics
git log --stat

# View commits with diffs
git log -p

# Limit number of commits shown
git log -n 5  # Last 5 commits
```

### Navigating History

```bash
# Show a specific commit
git show <commit-hash>

# Show files changed in a commit
git show --name-only <commit-hash>

# Show commits not yet pushed
git log origin/main..HEAD

# Show commits in current branch not in another
git log <other-branch>..HEAD
```

---

## Branching and Branch Management

### Creating and Switching Branches

```bash
# Create a new branch
git branch <branch-name>

# Create and switch to a new branch
git checkout -b <branch-name>

# Create and switch using switch command
git switch -c <branch-name>

# Create a branch from a specific commit
git branch <branch-name> <commit-hash>

# Create a tracking branch
git branch --track <branch-name> origin/<branch-name>
```

### Viewing Branches

```bash
# List local branches
git branch

# List all branches (local and remote)
git branch -a

# List branches with their upstream tracking
git branch -vv

# List remote branches
git branch -r

# Show branches that contain a commit
git branch --contains <commit-hash>
```

### Renaming and Deleting Branches

```bash
# Rename current branch
git branch -m <new-name>

# Rename a specific branch
git branch -m <old-name> <new-name>

# Delete a branch (local)
git branch -d <branch-name>

# Force delete a branch
git branch -D <branch-name>

# Delete a remote branch
git push origin --delete <branch-name>

# Delete multiple branches
git branch -d branch1 branch2 branch3
```

### Switching Branches

```bash
# Switch to an existing branch
git checkout <branch-name>

# Switch using switch command (newer syntax)
git switch <branch-name>

# Switch to previous branch
git checkout -

# Switch with a specific tracking branch
git checkout --track origin/<branch-name>
```

---

## Merging and Conflict Resolution

### Merging Branches

```bash
# Merge a branch into current branch
git merge <branch-name>

# Merge without fast-forward (always creates merge commit)
git merge --no-ff <branch-name>

# Merge squashing commits
git merge --squash <branch-name>

# Merge specific commit
git merge <commit-hash>

# Abort a merge in progress
git merge --abort
```

### Handling Merge Conflicts

```bash
# View conflicted files
git status

# View conflicts in a file
git diff

# Resolve conflict and add file
git add <filename>

# Use local version of file
git checkout --ours <filename>

# Use remote version of file
git checkout --theirs <filename>

# Continue merge after resolving conflicts
git commit -m "Merge message"

# Abort entire merge process
git merge --abort

# View merge conflicts in visual format
git diff --ours
git diff --theirs
git diff --base
```

### Merge Strategies

```bash
# Use recursive merge strategy (default)
git merge -s recursive <branch-name>

# Use resolve strategy
git merge -s resolve <branch-name>

# Use ours strategy (always take parent branch)
git merge -s ours <branch-name>

# Use subtree strategy
git merge -s subtree <branch-name>
```

---

## Remote Repository Operations

### Managing Remotes

```bash
# List all remotes
git remote

# List remotes with URLs
git remote -v

# Add a new remote
git remote add <remote-name> <repository-url>

# Remove a remote
git remote remove <remote-name>

# Rename a remote
git remote rename <old-name> <new-name>

# Change remote URL
git remote set-url <remote-name> <new-url>

# Show remote details
git remote show <remote-name>
```

### Pushing Changes

```bash
# Push to default remote and branch
git push

# Push to specific remote and branch
git push <remote-name> <branch-name>

# Push all branches
git push <remote-name> --all

# Push all tags
git push <remote-name> --tags

# Force push (use with caution)
git push -f

# Push with specific policy
git push --force-with-lease

# Delete remote branch
git push <remote-name> --delete <branch-name>

# Push and set upstream
git push -u <remote-name> <branch-name>
```

### Pulling and Fetching

```bash
# Fetch updates from remote
git fetch

# Fetch from specific remote
git fetch <remote-name>

# Fetch all remotes
git fetch --all

# Pull (fetch + merge)
git pull

# Pull with rebase instead of merge
git pull --rebase

# Pull from specific remote and branch
git pull <remote-name> <branch-name>

# Fetch without pulling
git fetch --dry-run
```

### Syncing with Remote

```bash
# Update remote tracking branches
git fetch origin

# Sync local branch with remote
git pull --rebase origin <branch-name>

# View remote history
git log origin/<branch-name>

# Compare local and remote
git log HEAD..origin/<branch-name>
```

---

## Stashing and Workspace Management

### Stashing Changes

```bash
# Stash current changes
git stash

# Stash with descriptive message
git stash save "Work in progress"

# Stash including untracked files
git stash -u

# Stash specific files
git stash push <file1> <file2>

# Stash staged changes only
git stash --staged
```

### Managing Stashes

```bash
# List all stashes
git stash list

# Show specific stash
git stash show stash@{0}

# Show stash with changes
git stash show -p stash@{0}

# Apply stash (keeping it)
git stash apply stash@{0}

# Pop stash (apply and remove)
git stash pop stash@{0}

# Delete a stash
git stash drop stash@{0}

# Delete all stashes
git stash clear

# Create branch from stash
git stash branch <branch-name> stash@{0}
```

---

## Resetting, Undoing, and Recovering Changes

### Undoing Changes

```bash
# Discard changes in working directory
git checkout -- <filename>

# Restore file (newer syntax)
git restore <filename>

# Restore from specific commit
git restore --source=<commit-hash> <filename>

# Undo uncommitted changes (all files)
git checkout -- .

# Clean untracked files
git clean -f

# Clean untracked files and directories
git clean -fd

# Preview clean operations
git clean -fd --dry-run
```

### Resetting Commits

```bash
# Soft reset (keep changes staged)
git reset --soft HEAD~1

# Mixed reset (keep changes unstaged)
git reset --mixed HEAD~1

# Hard reset (discard all changes)
git reset --hard HEAD~1

# Reset to a specific commit
git reset --hard <commit-hash>

# Reset a specific file
git reset <filename>

# Undo reset (use reflog)
git reflog
git reset --hard HEAD@{n}
```

### Recovering Lost Changes

```bash
# View reference logs
git reflog

# Recover deleted branch
git reflog show <branch-name>
git checkout -b <branch-name> <commit-hash>

# Find lost commits
git fsck --lost-found

# Recover uncommitted changes
git reflog
git cherry-pick <commit-hash>
```

---

## Rebasing and History Rewriting

### Basic Rebasing

```bash
# Rebase current branch onto another
git rebase <base-branch>

# Interactive rebase
git rebase -i HEAD~3

# Rebase with specific strategy
git rebase -s recursive <base-branch>

# Continue rebase after conflict resolution
git rebase --continue

# Skip commit during rebase
git rebase --skip

# Abort rebase
git rebase --abort
```

### Interactive Rebase Operations

```bash
# Interactive rebase on last 3 commits
git rebase -i HEAD~3

# Commands available in interactive rebase:
# pick (p) - use commit
# reword (r) - use commit, but edit message
# squash (s) - use commit, but meld into previous
# fixup (f) - like squash, but discard log message
# exec (e) - run shell command
# drop (d) - remove commit
```

### Rebase Best Practices

```bash
# Rebase before pushing
git fetch origin
git rebase origin/main
git push

# Autostash during rebase
git rebase --autostash

# Preserve merge commits during rebase
git rebase --preserve-merges

# Rebase with sign-off
git rebase --signoff
```

---

## Cherry-picking and Patch Management

### Cherry-picking Commits

```bash
# Apply specific commit to current branch
git cherry-pick <commit-hash>

# Apply multiple commits
git cherry-pick <commit1> <commit2> <commit3>

# Cherry-pick range of commits
git cherry-pick <start-commit>..<end-commit>

# Cherry-pick with editing
git cherry-pick -e <commit-hash>

# Cherry-pick without committing
git cherry-pick -n <commit-hash>

# Continue cherry-pick after conflict
git cherry-pick --continue

# Abort cherry-pick
git cherry-pick --abort
```

### Creating and Applying Patches

```bash
# Create patch from commits
git format-patch -1 <commit-hash>

# Create patch from range
git format-patch <start-commit>.<end-commit>

# Create patch between branches
git format-patch <branch1>..<branch2>

# Apply patch
git am <patch-file>

# Apply patch without committing
git apply <patch-file>

# Check if patch applies
git apply --check <patch-file>

# Continue applying patch after conflict
git am --continue

# Abort patch application
git am --abort
```

### Comparing Commits

```bash
# Compare different versions
git diff <commit1> <commit2>

# Show changes between branches
git diff <branch1> <branch2>

# Create diff file
git diff > changes.patch

# Cherry-pick specific hunks
git cherry-pick -n <commit-hash>
git reset
git add -p
```

---

## Tagging and Release Management

### Creating Tags

```bash
# Create lightweight tag
git tag <tag-name>

# Create annotated tag
git tag -a <tag-name> -m "Tag message"

# Create tag for specific commit
git tag <tag-name> <commit-hash>

# Create tag with annotation and sign
git tag -a <tag-name> -m "Message" -s

# Create tag based on pattern
git tag -l v1.*
```

### Managing Tags

```bash
# List all tags
git tag

# List tags matching pattern
git tag -l "v1.*"

# Show tag information
git show <tag-name>

# Delete local tag
git tag -d <tag-name>

# Delete remote tag
git push origin --delete <tag-name>

# Rename tag (delete and recreate)
git tag <new-name> <old-name>
git tag -d <old-name>
git push origin <new-name> --delete <old-name>
```

### Pushing Tags

```bash
# Push specific tag
git push origin <tag-name>

# Push all tags
git push origin --tags

# Push tags and branches
git push origin --all --tags

# Fetch tags from remote
git fetch --tags
```

---

## Submodule Integration

### Adding and Initializing Submodules

```bash
# Add a submodule
git submodule add <repository-url> <path>

# Add submodule at specific branch
git submodule add -b <branch-name> <repository-url> <path>

# Initialize submodules
git submodule init

# Clone repository with submodules
git clone --recurse-submodules <repository-url>

# Clone without initializing submodules
git clone <repository-url>
git submodule update --init --recursive
```

### Managing Submodules

```bash
# Update all submodules
git submodule update

# Update specific submodule
git submodule update <submodule-path>

# Update with pulling latest changes
git submodule update --remote

# Status of all submodules
git submodule status

# Execute command in all submodules
git submodule foreach <command>

# Update submodule branch
git submodule set-branch -b <branch-name> <submodule-path>
```

### Removing Submodules

```bash
# Remove submodule
git submodule deinit <submodule-path>
git rm <submodule-path>

# Clean up submodule configuration
git rm -f <submodule-path>
git config --remove-section submodule.<submodule-path>
```

---

## Debugging and Troubleshooting with Git

### Finding Issues with Git Blame

```bash
# Show who changed each line
git blame <filename>

# Show blame for specific line range
git blame -L <start>,<end> <filename>

# Show blame with email
git blame -e <filename>

# Show blame with date
git blame --date=short <filename>

# Show blame ignoring whitespace changes
git blame -w <filename>
```

### Bisecting to Find Issues

```bash
# Start bisect session
git bisect start

# Mark current commit as bad
git bisect bad

# Mark a known good commit
git bisect good <commit-hash>

# Continue bisecting
git bisect good  # or git bisect bad

# End bisect session
git bisect reset

# Automated bisect with script
git bisect run <script-path>
```

### Debugging with Git Log

```bash
# Find commits that introduced a string
git log -S "string_to_find"

# Find commits by commit message pattern
git log --grep="pattern"

# Find commits by author
git log --author="author name"

# Show changes that added/removed lines
git log -p --all -S "function_name"

# View only merge commits
git log --merges

# Show commits in topological order
git log --topo-order
```

### Checking Repository Integrity

```bash
# Verify repository integrity
git fsck

# Check for corruption
git fsck --full

# Show lost objects
git fsck --lost-found

# Verify all objects
git verify-pack -v .git/objects/pack/*.idx

# Check git consistency
git gc  # Garbage collection
```

### Troubleshooting Common Issues

```bash
# Recover from detached HEAD
git reflog
git checkout -b <new-branch> <commit-hash>

# Undo pushed commits
git revert <commit-hash>

# Check if commit is reachable
git merge-base --is-ancestor <commit> HEAD

# List commits not on any branch
git reflog expire --expire=now --all
git gc --prune=now

# View all references
git show-ref

# Check branch tracking
git branch -vv

# Update remote tracking branches
git remote update
```

---

## Best Practices and Tips

### Workflow Tips

- **Commit Often**: Make small, logical commits with clear messages
- **Pull Before Push**: Always sync with remote before pushing
- **Use Branches**: Create feature branches for new work
- **Write Clear Messages**: Use descriptive commit messages
- **Review Before Commit**: Use `git diff` to review changes
- **Keep History Clean**: Use rebase for local branches, merge for shared branches

### Security Practices

- Sign commits: `git config --global commit.gpgSign true`
- Verify commits: `git log --show-signature`
- Use SSH keys for authentication
- Rotate credentials regularly

### Performance Optimization

```bash
# Enable git maintenance
git maintenance start

# Repack repository
git repack -d

# Clean up unreachable objects
git gc --aggressive

# Use shallow clones for large repos
git clone --depth=1 <repository-url>
```

---

## Resources

- [Official Git Documentation](https://git-scm.com/doc)
- [Git Pro Book](https://git-scm.com/book)
- [GitHub Guides](https://guides.github.com/)
- [Atlassian Git Tutorials](https://www.atlassian.com/git/tutorials)

---

## Contributing

This repository is for learning and practice purposes. Feel free to create branches, experiment with commands, and contribute improvements.

---

**Last Updated**: April 2026
**Status**: Comprehensive Git Practice Guide
