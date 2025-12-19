# git_commands
Common git commands that are difficult to remember

## Remote Commands

```bash
# My own (Giddy-Up224) preference for adding remote

# If you accidentally pushed to the wrong remote 🫤
git remote remove origin

# Connect local repo to remote repo
git remote add origin https://github.com/<account>/<repo>

# Push local to remote
git push -u origin main
```

```bash
# List all remotes and their URLs
git remote -v

# Show remote branch details
git ls-remote <remote_name> <branch_name>

# Extract remote URL from Git config
git config --get remote.origin.url
# Alternative: grep "url =" .git/config

# Update remote URL
git remote set-url origin <new_url>

# Add new remote
git remote add <remote_name> <remote_url>

# Remove remote
git remote remove <remote_name>

# Rename remote
git remote rename <old_name> <new_name>

# Prune deleted remote branches
git remote prune <remote_name>

# Fetch from remote
git fetch <remote_name>

# Fetch specific branch from remote
git fetch <remote_name> <branch_name>

# Fetch all remote branches and tags
git fetch --all --tags

# Pull from remote (fetch + merge)
git pull <remote_name> <branch_name>

# Push to remote
git push <remote_name> <branch_name>

# Push to specific remote and branch
git push <remote_name> <local_branch>:<remote_branch>

# Force push (use with caution!)
git push --force-with-lease  # Safer alternative to --force
                             # Acts as a safety mechanism by checking if the remote
                             # branch has been modified since your last fetch.
                             # This helps prevent accidentally overwriting team
                             # members' work, which can happen with a regular
                             # --force push.

# Check remote tracking branches
git branch -vv

# Remove stale remote-tracking branches
git remote prune origin --dry-run  # Preview what will be pruned
git remote prune origin            # Actually prune
git fetch --prune                  # Fetch and prune in one command

# Mirror a repository (including all refs)
git clone --mirror <repository_url>

# Verify remote connections
git remote verify <remote_name>

# Sync fork with upstream
git fetch upstream
git checkout main
git merge upstream/main
```

## Terminology

```md
# Repository Concepts
repository  - A directory containing your project and its version history
local       - Your copy of the repository on your machine
remote      - A repository hosted on the internet or network (GitHub, GitLab, etc.)
fork        - A copy of someone else's repository under your account
clone       - A local copy of a remote repository

# Common Remote Names
origin      - The default name Git gives to the primary remote repository you cloned from
upstream    - Commonly used name for the original repository you forked from

# Branches and References
main/master - The default primary branch name (main is the new standard, master was historical)
HEAD        - A pointer to the current branch/commit you're working on
tracking branch - A local branch that tracks a remote branch (e.g., main tracks origin/main)

# Data Transfer Operations
fetch       - Download changes from remote without integrating them
pull        - Download changes from remote and integrate them (fetch + merge)
push        - Upload your local changes to a remote repository

# Merging and Integration
merge       - Combine changes from one branch into another
fast-forward - A merge where no new commit is created (target branch just moves forward)
merge commit - A new commit created when combining changes from two branches
conflict    - When changes in two branches modify the same code and cannot auto-merge
rebase      - Alternative to merge: replays your changes on top of target branch
cherry-pick - Apply a specific commit from one branch to another
```

## Repository Structure Example

```md
Your Local Repo (local)
    │
    ├── origin (your fork on GitHub)
    │     └── main branch
    │
    └── upstream (original repository)
          └── main branch

Example:
- upstream: https://github.com/original-author/project
- origin: https://github.com/your-username/project
- local: /home/your-username/project
```

## Remote Setups Example

```md
Simple Setup (Direct):
local ↔ origin (primary remote repository)

Fork Setup (Contributing to others):
local ↔ origin (your fork) ↔ upstream (original repository)

Multiple Remotes:
local ↔ origin (primary)
     ↔ staging (testing server)
     ↔ production (live server)
```

## Credits

[Jeremy Stretch](https://dev.to/j3zz3r/git-remote-cheatsheet-168n)
