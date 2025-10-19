Git Complete Guide - Everything You Need to Know 🚀
===================================================

English Version
---------------

* * *

What is Git? 🤔
---------------

**Git** is a **distributed version control system** (VCS) that tracks changes in your code over time. It allows multiple developers to work on the same project without overwriting each other's work.

**Created by:** Linus Torvalds (creator of Linux) in 2005

**Key Concepts:**

* 📂 **Repository (Repo)** - A project folder tracked by Git
* 💾 **Commit** - A snapshot of your project at a specific point in time
* 🌿 **Branch** - A parallel version of your code
* 🔄 **Merge** - Combining changes from different branches
* ☁️ **Remote** - A version of your repository hosted online (GitHub, GitLab, etc.)

* * *

Why Use Git? 💡
---------------

### Advantages:

1. **Version Control** 📜
   
   * Track every change in your code
   * Go back to any previous version
   * See who changed what and when

2. **Collaboration** 👥
   
   * Multiple people work on the same project
   * Merge changes without conflicts
   * Review code before merging

3. **Backup** 💾
   
   * Your code is stored locally AND remotely
   * Never lose work
   * Disaster recovery

4. **Experimentation** 🧪
   
   * Try new features in branches
   * If it works → merge
   * If it fails → delete branch

5. **Portfolio** 💼
   
   * Show your work on GitHub
   * Prove your skills to employers
   * Contribute to open source

* * *

Git vs GitHub 🆚
----------------

| Git                            | GitHub                          |
| ------------------------------ | ------------------------------- |
| Version control system         | Website/service                 |
| Works locally on your computer | Stores repos in the cloud       |
| Command-line tool              | Web interface + Git integration |
| Free and open source           | Free for public repos           |
| Created by Linus Torvalds      | Created by Microsoft            |

**Analogy:**

* **Git** = Camera (takes photos/commits)
* **GitHub** = Instagram (stores and shares photos)

**Alternatives to GitHub:**

* GitLab
* Bitbucket
* Gitea

* * *

How Git Works: The Three States 🎭
----------------------------------

Git has three main states where your files can reside:
    Working Directory → Staging Area → Repository
         (Modified)       (Staged)      (Committed)

### 1. **Working Directory** 📁

* Your actual project files
* Where you make changes
* Not tracked by Git yet

### 2. **Staging Area (Index)** 📦

* Prepared files ready to commit
* "Staging" = selecting which changes to save
* Like packing a box before shipping

### 3. **Repository (.git directory)** 💾

* Committed changes
* Permanent history
* Safely stored snapshots

* * *

Basic Git Workflow 🔄
---------------------

    1. Modify files in working directory
             ↓
    2. Stage changes (git add)
             ↓
    3. Commit staged changes (git commit)
             ↓
    4. Push to remote repository (git push)

* * *

Git Installation 📥
-------------------

### Windows:

    # Download from: https://git-scm.com/download/win
    # Or use Winget:
    winget install Git.Git

### macOS:

    # Using Homebrew:
    brew install git
    
    # Or Xcode Command Line Tools:
    xcode-select --install

### Linux:

    # Debian/Ubuntu:
    sudo apt update
    sudo apt install git
    
    # Fedora:
    sudo dnf install git
    
    # Arch:
    sudo pacman -S git

### Verify Installation:

    git --version
    # Output: git version 2.x.x

* * *

Git Configuration ⚙️
--------------------

### First-Time Setup (IMPORTANT!):

    # Set your name (will appear in commits)
    git config --global user.name "Your Name"
    
    # Set your email (must match GitHub email)
    git config --global user.email "your.email@example.com"
    
    # Set default branch name to 'main'
    git config --global init.defaultBranch main
    
    # Set default editor (optional)
    git config --global core.editor "code --wait"  # VS Code
    git config --global core.editor "vim"          # Vim

### View Configuration:

    # View all settings
    git config --list
    
    # View specific setting
    git config user.name
    git config user.email

### Configuration Levels:

    # System-wide (all users)
    git config --system
    
    # User-wide (your account)
    git config --global
    
    # Repository-specific (current repo only)
    git config --local

* * *

Essential Git Commands 📚
-------------------------

### 1. Creating Repositories

#### Initialize a New Repository:

    # Create new repo in current directory
    git init
    
    # Create new repo in specific directory
    git init my-project

**What it does:**

* Creates a hidden `.git` folder
* Starts tracking changes
* Sets up Git infrastructure

#### Clone an Existing Repository:

    # Clone from GitHub
    git clone https://github.com/username/repo-name.git
    
    # Clone with custom name
    git clone https://github.com/username/repo-name.git my-folder
    
    # Clone specific branch
    git clone -b branch-name https://github.com/username/repo-name.git

**What it does:**

* Downloads entire repository
* Creates local copy
* Sets up remote connection

* * *

### 2. Basic Snapshotting

#### Check Status:

    # See current state of working directory
    git status
    
    # Short format
    git status -s

**Output meanings:**

* `??` - Untracked file
* `M` - Modified file
* `A` - Added (staged) file
* `D` - Deleted file

#### Stage Changes:

    # Stage specific file
    git add filename.txt
    
    # Stage multiple files
    git add file1.txt file2.txt
    
    # Stage all changes
    git add .
    
    # Stage all files of a type
    git add *.js
    
    # Stage directory
    git add foldername/
    
    # Interactive staging
    git add -i
    
    # Stage parts of a file
    git add -p

#### Unstage Changes:

    # Unstage specific file
    git reset filename.txt
    
    # Unstage all files
    git reset

#### Commit Changes:

    # Commit with message
    git commit -m "Add new feature"
    
    # Commit with detailed message
    git commit -m "Add login functionality" -m "This adds user authentication with JWT tokens"
    
    # Stage and commit in one step
    git commit -am "Fix bug in header"
    
    # Open editor for commit message
    git commit
    
    # Amend last commit (change message or add files)
    git commit --amend

**Good Commit Messages:**
    ✅ "Add user authentication"
    ✅ "Fix null pointer exception in UserService"
    ✅ "Update README with installation instructions"

    ❌ "fix"
    ❌ "changes"
    ❌ "asdfasdf"

#### Remove Files:

    # Remove file from Git and filesystem
    git rm filename.txt
    
    # Remove from Git but keep in filesystem
    git rm --cached filename.txt
    
    # Remove directory
    git rm -r foldername/

#### Move/Rename Files:

    # Rename file
    git mv oldname.txt newname.txt
    
    # Move file
    git mv file.txt newfolder/file.txt

* * *

### 3. Viewing History

#### View Commit History:

    # View all commits
    git log
    
    # One line per commit
    git log --oneline
    
    # With graph
    git log --oneline --graph --all
    
    # Last N commits
    git log -5
    
    # Show file changes
    git log --stat
    
    # Search commits
    git log --grep="bug fix"
    
    # Commits by author
    git log --author="John"
    
    # Commits in date range
    git log --since="2024-01-01" --until="2024-12-31"
    
    # Pretty format
    git log --pretty=format:"%h - %an, %ar : %s"

#### View Specific Commit:

    # Show commit details
    git show commit-hash
    
    # Show specific file in commit
    git show commit-hash:filename.txt

#### View Changes:

    # Changes in working directory (not staged)
    git diff
    
    # Changes in staging area
    git diff --staged
    # or
    git diff --cached
    
    # Changes between commits
    git diff commit1 commit2
    
    # Changes in specific file
    git diff filename.txt

* * *

### 4. Undoing Changes

#### Discard Changes in Working Directory:

    # Discard changes in specific file
    git checkout -- filename.txt
    
    # Discard all changes
    git checkout -- .
    
    # Modern way (Git 2.23+)
    git restore filename.txt
    git restore .

#### Unstage Files:

    # Unstage specific file
    git reset HEAD filename.txt
    
    # Modern way
    git restore --staged filename.txt

#### Undo Commits:

##### Soft Reset (keep changes):

    # Undo last commit, keep changes staged
    git reset --soft HEAD~1
    
    # Undo last 3 commits
    git reset --soft HEAD~3

##### Mixed Reset (default):

    # Undo last commit, keep changes unstaged
    git reset HEAD~1
    # or
    git reset --mixed HEAD~1

##### Hard Reset (delete changes):

    # ⚠️ DANGEROUS! Undo last commit and delete changes
    git reset --hard HEAD~1
    
    # Reset to specific commit
    git reset --hard commit-hash

##### Revert (safe undo):

    # Create new commit that undoes changes
    git revert commit-hash
    
    # Revert without committing
    git revert --no-commit commit-hash

**Difference:**

* `reset` - Moves branch pointer, rewrites history
* `revert` - Creates new commit, preserves history

* * *

### 5. Branching and Merging

#### View Branches:

    # List local branches
    git branch
    
    # List all branches (local + remote)
    git branch -a
    
    # List remote branches
    git branch -r
    
    # Verbose (shows last commit)
    git branch -v

#### Create Branch:

    # Create new branch
    git branch feature-login
    
    # Create and switch to branch
    git checkout -b feature-login
    
    # Modern way
    git switch -c feature-login

#### Switch Branch:

    # Switch to existing branch
    git checkout branch-name
    
    # Modern way
    git switch branch-name
    
    # Switch to previous branch
    git switch -

#### Delete Branch:

    # Delete merged branch
    git branch -d branch-name
    
    # Force delete (even if not merged)
    git branch -D branch-name
    
    # Delete remote branch
    git push origin --delete branch-name

#### Rename Branch:

    # Rename current branch
    git branch -m new-name
    
    # Rename specific branch
    git branch -m old-name new-name

#### Merge Branches:

    # Merge branch into current branch
    git merge feature-login
    
    # Merge without fast-forward (creates merge commit)
    git merge --no-ff feature-login
    
    # Merge and squash commits
    git merge --squash feature-login

**Merge Types:**

* **Fast-forward** - Simple, moves pointer forward
* **Three-way merge** - Creates merge commit
* **Squash merge** - Combines all commits into one

#### Resolve Merge Conflicts:

    # 1. Git shows conflicts
    git merge feature-login
    # CONFLICT (content): Merge conflict in file.txt
    
    # 2. View conflicted files
    git status
    
    # 3. Open file and resolve conflicts
    # Look for:
    # <<<<<<< HEAD
    # Your changes
    # =======
    # Their changes
    # >>>>>>> feature-login
    
    # 4. After resolving, stage changes
    git add file.txt
    
    # 5. Complete merge
    git commit

* * *

### 6. Remote Repositories

#### View Remotes:

    # List remotes
    git remote
    
    # List remotes with URLs
    git remote -v
    
    # Show remote details
    git remote show origin

#### Add Remote:

    # Add remote repository
    git remote add origin https://github.com/username/repo.git
    
    # Add with SSH
    git remote add origin git@github.com:username/repo.git

#### Change Remote URL:

    # Change remote URL
    git remote set-url origin https://github.com/username/new-repo.git

#### Remove Remote:

    # Remove remote
    git remote remove origin

#### Fetch Changes:

    # Download changes (doesn't merge)
    git fetch
    
    # Fetch from specific remote
    git fetch origin
    
    # Fetch specific branch
    git fetch origin main

#### Pull Changes:

    # Fetch and merge
    git pull
    
    # Pull from specific branch
    git pull origin main
    
    # Pull with rebase
    git pull --rebase

**Difference:**

* `fetch` - Downloads changes only
* `pull` - Downloads AND merges (`fetch` + `merge`)

#### Push Changes:

    # Push to remote
    git push
    
    # Push to specific remote and branch
    git push origin main
    
    # Push all branches
    git push --all
    
    # Push with tags
    git push --tags
    
    # Force push (⚠️ DANGEROUS!)
    git push -f origin main
    
    # Safer force push
    git push --force-with-lease origin main
    
    # Set upstream for future pushes
    git push -u origin main

* * *

### 7. Stashing

#### Save Work Temporarily:

    # Stash changes
    git stash
    
    # Stash with message
    git stash save "Work in progress on login"
    
    # Stash including untracked files
    git stash -u
    
    # Stash everything (including ignored files)
    git stash -a

#### View Stashes:

    # List stashes
    git stash list
    
    # Show stash contents
    git stash show
    
    # Show stash diff
    git stash show -p

#### Apply Stashes:

    # Apply latest stash (keeps stash)
    git stash apply
    
    # Apply specific stash
    git stash apply stash@{2}
    
    # Apply and remove stash
    git stash pop
    
    # Apply specific stash and remove
    git stash pop stash@{1}

#### Delete Stashes:

    # Delete specific stash
    git stash drop stash@{0}
    
    # Delete all stashes
    git stash clear

* * *

### 8. Tagging

#### Create Tags:

    # Lightweight tag
    git tag v1.0.0
    
    # Annotated tag (recommended)
    git tag -a v1.0.0 -m "Version 1.0.0 release"
    
    # Tag specific commit
    git tag -a v1.0.0 commit-hash -m "Release version 1.0.0"

#### View Tags:

    # List tags
    git tag
    
    # List tags with pattern
    git tag -l "v1.*"
    
    # Show tag details
    git show v1.0.0

#### Push Tags:

    # Push specific tag
    git push origin v1.0.0
    
    # Push all tags
    git push --tags

#### Delete Tags:

    # Delete local tag
    git tag -d v1.0.0
    
    # Delete remote tag
    git push origin --delete v1.0.0

* * *

### 9. Advanced Operations

#### Rebase:

    # Rebase current branch onto main
    git rebase main
    
    # Interactive rebase (edit commits)
    git rebase -i HEAD~3
    
    # Continue rebase after resolving conflicts
    git rebase --continue
    
    # Abort rebase
    git rebase --abort

**Interactive Rebase Commands:**

* `pick` - Use commit
* `reword` - Change commit message
* `edit` - Stop for amending
* `squash` - Combine with previous commit
* `fixup` - Like squash but discard message
* `drop` - Remove commit

#### Cherry-pick:

    # Apply specific commit to current branch
    git cherry-pick commit-hash
    
    # Cherry-pick multiple commits
    git cherry-pick commit1 commit2
    
    # Cherry-pick without committing
    git cherry-pick --no-commit commit-hash

#### Reflog:

    # View reference log (all actions)
    git reflog
    
    # Recover deleted commit
    git reflog
    git reset --hard HEAD@{2}

#### Clean:

    # Remove untracked files (dry run)
    git clean -n
    
    # Remove untracked files
    git clean -f
    
    # Remove untracked files and directories
    git clean -fd
    
    # Remove ignored files too
    git clean -fdx

* * *

.gitignore File 🚫
------------------

**Purpose:** Tell Git which files to ignore (not track)

### Create .gitignore:

    # Create file
    touch .gitignore
    
    # Or
    echo "node_modules/" > .gitignore

### Common Patterns:

    # OS files
    .DS_Store
    Thumbs.db
    desktop.ini
    
    # IDE files
    .vscode/
    .idea/
    *.swp
    *.swo
    *~
    
    # Language-specific
    
    # Python
    __pycache__/
    *.py[cod]
    *.pyo
    *.pyd
    .Python
    venv/
    env/
    
    # Node.js
    node_modules/
    npm-debug.log
    yarn-error.log
    
    # Java
    *.class
    *.jar
    *.war
    target/
    
    # C++
    *.o
    *.exe
    *.out
    a.out
    
    # Build directories
    build/
    dist/
    *.egg-info/
    
    # Logs
    *.log
    logs/
    
    # Environment variables
    .env
    .env.local
    
    # Database
    *.db
    *.sqlite
    
    # Temporary files
    *.tmp
    *.temp
    *.bak
    
    # Sensitive data
    config/secrets.yml
    *.key
    *.pem

### Ignore Already Tracked Files:

    # Stop tracking but keep file
    git rm --cached filename
    
    # For directories
    git rm -r --cached foldername/
    
    # Then commit
    git commit -m "Remove tracked files from .gitignore"

* * *

Git Workflows 🔄
----------------

### 1. Feature Branch Workflow

    main branch (production)
        |
        ├── feature-1 (your work)
        ├── feature-2 (teammate's work)
        └── bugfix-login

**Process:**
    # 1. Create feature branch
    git checkout -b feature-login

    # 2. Make changes and commit
    git add .
    git commit -m "Add login form"

    # 3. Push to remote
    git push -u origin feature-login

    # 4. Create Pull Request on GitHub

    # 5. After approval, merge to main
    git checkout main
    git merge feature-login

    # 6. Delete feature branch
    git branch -d feature-login
    git push origin --delete feature-login

* * *

### 2. Gitflow Workflow

    main (production)
        |
    develop (integration)
        |
        ├── feature/login
        ├── feature/profile
        └── hotfix/critical-bug

**Branches:**

* `main` - Production code
* `develop` - Integration branch
* `feature/*` - New features
* `release/*` - Release preparation
* `hotfix/*` - Emergency fixes

* * *

### 3. Forking Workflow

**Used for open source:**

1. Fork repository on GitHub

2. Clone your fork

3. Create feature branch

4. Make changes

5. Push to your fork

6. Create Pull Request to original repo
   
   # 1. Clone your fork
   
    git clone https://github.com/YOUR_USERNAME/repo.git
   
   # 2. Add upstream remote
   
    git remote add upstream https://github.com/ORIGINAL_OWNER/repo.git
   
   # 3. Create feature branch
   
    git checkout -b feature-awesome
   
   # 4. Make changes and commit
   
    git add .
    git commit -m "Add awesome feature"
   
   # 5. Push to your fork
   
    git push origin feature-awesome
   
   # 6. Create Pull Request on GitHub
   
   # 7. Keep fork updated
   
    git fetch upstream
    git checkout main
    git merge upstream/main
    git push origin main

* * *

GitHub Specific Features 🐙
---------------------------

### 1. Pull Requests (PRs)

**What it is:** Request to merge your changes into another branch

**Process:**

1. Push branch to GitHub
2. Click "Compare & pull request"
3. Fill out PR template
4. Request reviewers
5. Address feedback
6. Merge when approved

### 2. Issues

**Track bugs and features:**
    # Bug Report Template

    ## Description
    What's the problem?

    ## Steps to Reproduce
    1. Go to...
    2. Click on...
    3. See error

    ## Expected Behavior
    What should happen?

    ## Actual Behavior
    What actually happens?

    ## Environment
    - OS: Windows 10
    - Browser: Chrome 120
    - Version: 1.2.3

### 3. GitHub Actions (CI/CD)

**Automate workflows:**
    # .github/workflows/test.yml
    name: Run Tests

    on: [push, pull_request]

    jobs:
      test:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2
          - name: Run tests
            run: |
              npm install
              npm test

### 4. SSH Keys

**Setup SSH for GitHub:**
    # 1. Generate SSH key
    ssh-keygen -t ed25519 -C "your.email@example.com"

    # 2. Start SSH agent
    eval "$(ssh-agent -s)"

    # 3. Add key to agent
    ssh-add ~/.ssh/id_ed25519

    # 4. Copy public key
    cat ~/.ssh/id_ed25519.pub

    # 5. Add to GitHub:
    # Settings → SSH and GPG keys → New SSH key

    # 6. Test connection
    ssh -T git@github.com

* * *

Best Practices ✅
----------------

### 1. Commit Often, Push Regularly

    # ✅ Good
    git commit -m "Add login form"
    git commit -m "Add validation"
    git commit -m "Add error handling"
    
    # ❌ Bad
    # Wait 3 days, then one huge commit
    git commit -m "Add entire login system"

### 2. Write Meaningful Commit Messages

    # ✅ Good
    git commit -m "Fix null pointer exception in UserService.login()"
    git commit -m "Add email validation to registration form"
    
    # ❌ Bad
    git commit -m "fix"
    git commit -m "updates"
    git commit -m "asdf"

**Convention:**
    <type>: <subject>

    <body>

    <footer>

**Types:**

* `feat:` - New feature
* `fix:` - Bug fix
* `docs:` - Documentation
* `style:` - Formatting
* `refactor:` - Code restructuring
* `test:` - Adding tests
* `chore:` - Maintenance

**Example:**
    git commit -m "feat: add user authentication

    - Implement JWT tokens
    - Add login/logout endpoints
    - Add password hashing with bcrypt

    Closes #123"

### 3. Keep Commits Atomic

* One commit = one logical change
* Easy to understand
* Easy to revert if needed

### 4. Use Branches

    # ✅ Good - use branches
    git checkout -b feature-payment
    # make changes
    git commit
    git push origin feature-payment
    
    # ❌ Bad - work directly on main
    git checkout main
    # make changes
    git commit

### 5. Pull Before Push

    # Always pull before pushing
    git pull origin main
    git push origin main

### 6. Review Before Committing

    # Check what you're committing
    git diff
    git status
    
    # Then commit
    git add .
    git commit -m "Message"

### 7. Use .gitignore

* Don't commit sensitive data
* Don't commit dependencies
* Don't commit build artifacts

### 8. Don't Force Push to Shared Branches

    # ❌ Dangerous on shared branches
    git push -f origin main
    
    # ✅ Only on your personal branches
    git push -f origin feature-my-work

* * *

Common Mistakes & Solutions 🚨
------------------------------

### 1. Committed to Wrong Branch

    # Solution: Stash, switch branch, apply
    git stash
    git checkout correct-branch
    git stash pop
    git add .
    git commit -m "Message"

### 2. Accidentally Committed Sensitive Data

    # Solution: Remove from history
    git filter-branch --force --index-filter \
      "git rm --cached --ignore-unmatch path/to/file" \
      --prune-empty --tag-name-filter cat -- --all
    
    # Or use BFG Repo-Cleaner (easier)
    bfg --delete-files sensitive.txt

### 3. Merge Conflict

    # 1. Pull latest changes
    git pull origin main
    
    # 2. See conflicts
    git status
    
    # 3. Open files and resolve
    # Remove <<<<<<, ======, >>>>>> markers
    # Keep the code you want
    
    # 4. Stage resolved files
    git add resolved-file.txt
    
    # 5. Complete merge
    git commit

### 4. Accidentally Deleted Branch

    # Find deleted branch in reflog
    git reflog
    
    # Restore it
    git checkout -b branch-name commit-hash

### 5. Pushed Wrong Commit

    # If not pushed yet
    git reset --hard HEAD~1
    
    # If already pushed (and it's your branch)
    git reset --hard HEAD~1
    git push -f origin branch-name
    
    # If it's a shared branch (safer)
    git revert commit-hash
    git push origin branch-name

### 6. Large Files Error

    # GitHub rejects files > 100MB
    
    # Solution: Use Git LFS
    git lfs install
    git lfs track "*.psd"
    git add .gitattributes
    git add large-file.psd
    git commit -m "Add large file with LFS"

* * *

Git Aliases (Shortcuts) ⚡
-------------------------

**Make Git commands shorter:**
    # Setup aliases
    git config --global alias.st status
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.cm commit
    git config --global alias.last 'log -1 HEAD'
    git config --global alias.unstage 'reset HEAD --'
    git config --global alias.visual 'log --oneline --graph --all'

    # Usage
    git st          # instead of git status
    git co main     # instead of git checkout main
    git visual      # pretty git log

**Advanced aliases:**
    # Pretty log
    git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

    # Undo last commit
    git config --global alias.undo 'reset HEAD~1 --mixed'

    # Amend without changing message
    git config --global alias.amend 'commit --amend --no-edit'

* * *

Git Hooks 🪝
------------

**Automate actions on Git events:**

### Common Hooks:

* `pre-commit` - Run before commit
* `commit-msg` - Validate commit message
* `pre-push` - Run before push
* `post-merge` - Run after merge

### Example: Pre-commit Hook

    # .git/hooks/pre-commit
    
    #!/bin/sh
    # Run tests before commit
    
    npm test
    
    if [ $? -ne 0 ]; then
        echo "Tests failed! Commit aborted."
        exit 1
    fi

**Make executable:**
    chmod +x .git/hooks/pre-commit

* * *

Git Internals (How Git Works) 🔬
--------------------------------

### Git Objects:

1. **Blob** - File content
2. **Tree** - Directory structure
3. **Commit** - Snapshot with metadata
4. **Tag** - Named reference to commit

### Inside .git Directory:

    .git/
    ├── HEAD              # Current branch pointer
    ├── config            # Repository configuration
    ├── description       # Repository description
    ├── hooks/            # Git hooks
    ├── index             # Staging area
    ├── objects/          # Git objects (commits, blobs, trees)
    ├── refs/             # Branch and tag references
    │   ├── heads/        # Local branches
    │   ├── remotes/      # Remote branches
    │   └── tags/         # Tags
    └── logs/             # Reference logs

### How Commits Work:

    Commit Object:
    - Tree (snapshot of files)
    - Parent commit(s)
    - Author info
    - Committer info
    - Commit message
    - SHA-1 hash (unique ID)

* * *

Troubleshooting Commands 🔧
---------------------------

    # Check if directory is a Git repo
    git rev-parse --is-inside-work-tree
    
    # Show current branch
    git branch --show-current
    
    # Show remote URL
    git remote get-url origin
    
    # Verify repository
    git fsck
    
    # Clean repository
    git gc
    git prune
    
    # Show config location
    git config --list --show-origin
    
    # Debug command
    GIT_TRACE=1 git status

* * *

Quick Reference Cheatsheet 📋
-----------------------------

### Essential Commands:

    # Setup
    git init                    # Initialize repo
    git clone URL               # Clone repo
    
    # Basic workflow
    git status                  # Check status
    git add .                   # Stage all
    git commit -m "msg"         # Commit
    git push                    # Push to remote
    git pull                    # Pull from remote
    
    # Branching
    git branch                  # List branches
    git branch name             # Create branch
    git checkout name           # Switch branch
    git checkout -b name        # Create and switch
    git merge name              # Merge branch
    
    # Undo
    git reset HEAD~1            # Undo last commit (keep changes)
    git reset --hard HEAD~1     # Undo last commit (delete changes)
    git revert commit-hash      # Safe undo
    
    # History
    git log                     # View commits
    git log --oneline           # Compact view
    git diff                    # View changes
    
    # Remote
    git remote -v               # View remotes
    git fetch                   # Download changes
    git push -u origin main     # Push and set upstream
    
    # Stash
    git stash                   # Save work
    git stash pop               # Restore work

* * *

Security Best Practices 🔒
--------------------------

### 1. Never Commit Sensitive Data

    # ❌ Don't commit:
    # - Passwords
    # - API keys
    # - Private keys
    # - .env files
    # - Database credentials

### 2. Use SSH Instead of HTTPS

    # More secure for private repos
    git remote set-url origin git@github.com:user/repo.git

### 3. Sign Commits (GPG)

    # Generate GPG key
    gpg --gen-key
    
    # Configure Git
    git config --global user.signingkey YOUR_KEY_ID
    git config --global commit.gpgsign true
    
    # Sign commit
    git commit -S -m "Signed commit"

### 4. Review Before Pushing

    # Always check what you're pushing
    git diff origin/main
    git log origin/main..HEAD

### 5. Use .gitignore

    # Always ignore sensitive files
    echo ".env" >> .gitignore
    echo "config/secrets.yml" >> .gitignore

* * *

Performance Tips ⚡
------------------

### 1. Shallow Clone (Faster)

    # Clone only recent history
    git clone --depth 1 URL

### 2. Sparse Checkout (Large Repos)

    # Clone only specific files/folders
    git clone --filter=blob:none --sparse URL
    cd repo
    git sparse-checkout init
    git sparse-checkout set path/to/folder

### 3. Clean Up

    # Remove old objects
    git gc --aggressive
    
    # Remove unreachable objects
    git prune

* * *

Learning Resources 📚
---------------------

### Official Documentation:

* https://git-scm.com/doc
* https://git-scm.com/book/en/v2

### Interactive Learning:

* https://learngitbranching.js.org/
* https://github.com/jlord/git-it-electron

### Practice:

* https://github.com/skills
* https://www.katacoda.com/courses/git

### GitHub Guides:

* https://guides.github.com/

* * *

Git Полное Руководство - Всё что нужно знать 🚀
===============================================

Русская версия
--------------

* * *

Что такое Git? 🤔
-----------------

**Git** — это **распределённая система контроля версий** (VCS), которая отслеживает изменения в вашем коде с течением времени. Он позволяет нескольким разработчикам работать над одним проектом, не перезаписывая работу друг друга.

**Создатель:** Линус Торвальдс (создатель Linux) в 2005 году

**Ключевые концепции:**

* 📂 **Репозиторий (Repo)** - Папка проекта, отслеживаемая Git
* 💾 **Коммит** - Снимок проекта в определённый момент времени
* 🌿 **Ветка** - Параллельная версия кода
* 🔄 **Слияние (Merge)** - Объединение изменений из разных веток
* ☁️ **Удалённый репозиторий (Remote)** - Версия репозитория, размещённая онлайн (GitHub, GitLab и т.д.)

* * *

Зачем использовать Git? 💡
--------------------------

### Преимущества:

1. **Контроль версий** 📜
   
   * Отслеживайте каждое изменение в коде
   * Возвращайтесь к любой предыдущей версии
   * Смотрите, кто что изменил и когда

2. **Совместная работа** 👥
   
   * Несколько людей работают над одним проектом
   * Объединяйте изменения без конфликтов
   * Проверяйте код перед слиянием

3. **Резервное копирование** 💾
   
   * Код хранится локально И удалённо
   * Никогда не потеряете работу
   * Восстановление после сбоев

4. **Эксперименты** 🧪
   
   * Пробуйте новые функции в ветках
   * Работает → сливайте
   * Не работает → удаляйте ветку

5. **Портфолио** 💼
   
   * Показывайте работу на GitHub
   * Докажите навыки работодателям
   * Вносите вклад в открытый код

* * *

Git vs GitHub 🆚
----------------

| Git                             | GitHub                                |
| ------------------------------- | ------------------------------------- |
| Система контроля версий         | Веб-сайт/сервис                       |
| Работает локально на компьютере | Хранит репозитории в облаке           |
| Инструмент командной строки     | Веб-интерфейс + интеграция Git        |
| Бесплатный и открытый           | Бесплатный для публичных репозиториев |
| Создан Линусом Торвальдсом      | Создан Microsoft                      |

**Аналогия:**

* **Git** = Фотоаппарат (делает снимки/коммиты)
* **GitHub** = Instagram (хранит и делится снимками)

**Альтернативы GitHub:**

* GitLab
* Bitbucket
* Gitea

* * *

Как работает Git: Три состояния 🎭
----------------------------------

Git имеет три основных состояния, в которых могут находиться файлы:
    Рабочая директория → Staging Area → Репозиторий
        (Modified)         (Staged)      (Committed)

### 1. **Рабочая директория (Working Directory)** 📁

* Ваши реальные файлы проекта
* Где вы вносите изменения
* Ещё не отслеживается Git

### 2. **Staging Area (Индекс)** 📦

* Подготовленные файлы, готовые к коммиту
* "Staging" = выбор изменений для сохранения
* Как упаковка коробки перед отправкой

### 3. **Репозиторий (.git директория)** 💾

* Зафиксированные изменения
* Постоянная история
* Безопасно сохранённые снимки

* * *

Базовый рабочий процесс Git 🔄
------------------------------

    1. Изменяете файлы в рабочей директории
             ↓
    2. Добавляете изменения в staging (git add)
             ↓
    3. Коммитите изменения (git commit)
             ↓
    4. Отправляете на удалённый репозиторий (git push)

* * *

Установка Git 📥
----------------

### Windows:

    # Скачайте с: https://git-scm.com/download/win
    # Или используйте Winget:
    winget install Git.Git

### macOS:

    # Используя Homebrew:
    brew install git
    
    # Или Xcode Command Line Tools:
    xcode-select --install

### Linux:

    # Debian/Ubuntu:
    sudo apt update
    sudo apt install git
    
    # Fedora:
    sudo dnf install git
    
    # Arch:
    sudo pacman -S git

### Проверка установки:

    git --version
    # Вывод: git version 2.x.x

* * *

Настройка Git ⚙️
----------------

### Первоначальная настройка (ВАЖНО!):

    # Установите имя (будет отображаться в коммитах)
    git config --global user.name "Ваше Имя"
    
    # Установите email (должен совпадать с email на GitHub)
    git config --global user.email "your.email@example.com"
    
    # Установите имя ветки по умолчанию на 'main'
    git config --global init.defaultBranch main
    
    # Установите редактор по умолчанию (опционально)
    git config --global core.editor "code --wait"  # VS Code
    git config --global core.editor "vim"          # Vim

### Просмотр конфигурации:

    # Посмотреть все настройки
    git config --list
    
    # Посмотреть конкретную настройку
    git config user.name
    git config user.email

### Уровни конфигурации:

    # Системный (все пользователи)
    git config --system
    
    # Пользовательский (ваш аккаунт)
    git config --global
    
    # Для конкретного репозитория
    git config --local

* * *

Основные команды Git 📚
-----------------------

### 1. Создание репозиториев

#### Инициализация нового репозитория:

    # Создать новый репозиторий в текущей директории
    git init
    
    # Создать новый репозиторий в конкретной директории
    git init my-project

**Что это делает:**

* Создаёт скрытую папку `.git`
* Начинает отслеживать изменения
* Настраивает инфраструктуру Git

#### Клонирование существующего репозитория:

    # Клонировать с GitHub
    git clone https://github.com/username/repo-name.git
    
    # Клонировать с пользовательским именем
    git clone https://github.com/username/repo-name.git my-folder
    
    # Клонировать конкретную ветку
    git clone -b branch-name https://github.com/username/repo-name.git

**Что это делает:**

* Загружает весь репозиторий
* Создаёт локальную копию
* Настраивает удалённое соединение

* * *

### 2. Базовые операции со снимками

#### Проверка статуса:

    # Посмотреть текущее состояние рабочей директории
    git status
    
    # Короткий формат
    git status -s

**Значения вывода:**

* `??` - Неотслеживаемый файл
* `M` - Изменённый файл
* `A` - Добавленный (staged) файл
* `D` - Удалённый файл

#### Добавление изменений в staging:

    # Добавить конкретный файл
    git add filename.txt
    
    # Добавить несколько файлов
    git add file1.txt file2.txt
    
    # Добавить все изменения
    git add .
    
    # Добавить все файлы определённого типа
    git add *.js
    
    # Добавить директорию
    git add foldername/
    
    # Интерактивное добавление
    git add -i
    
    # Добавить части файла
    git add -p

#### Убрать из staging:

    # Убрать конкретный файл из staging
    git reset filename.txt
    
    # Убрать все файлы из staging
    git reset

#### Создание коммита:

    # Коммит с сообщением
    git commit -m "Добавить новую функцию"
    
    # Коммит с подробным сообщением
    git commit -m "Добавить функционал входа" -m "Добавлена аутентификация с JWT токенами"
    
    # Добавить в staging и сделать коммит одной командой
    git commit -am "Исправить баг в header"
    
    # Открыть редактор для сообщения коммита
    git commit
    
    # Изменить последний коммит (изменить сообщение или добавить файлы)
    git commit --amend

**Хорошие сообщения коммитов:**
    ✅ "Добавить аутентификацию пользователя"
    ✅ "Исправить null pointer exception в UserService"
    ✅ "Обновить README с инструкциями по установке"

    ❌ "fix"
    ❌ "changes"
    ❌ "asdfasdf"

#### Удаление файлов:

    # Удалить файл из Git и файловой системы
    git rm filename.txt
    
    # Удалить из Git, но оставить в файловой системе
    git rm --cached filename.txt
    
    # Удалить директорию
    git rm -r foldername/

#### Перемещение/Переименование файлов:

    # Переименовать файл
    git mv oldname.txt newname.txt
    
    # Переместить файл
    git mv file.txt newfolder/file.txt

* * *

### 3. Просмотр истории

#### Просмотр истории коммитов:

    # Посмотреть все коммиты
    git log
    
    # Одна строка на коммит
    git log --oneline
    
    # С графом
    git log --oneline --graph --all
    
    # Последние N коммитов
    git log -5
    
    # Показать изменения файлов
    git log --stat
    
    # Поиск коммитов
    git log --grep="исправление бага"
    
    # Коммиты по автору
    git log --author="Иван"
    
    # Коммиты в диапазоне дат
    git log --since="2024-01-01" --until="2024-12-31"
    
    # Красивый формат
    git log --pretty=format:"%h - %an, %ar : %s"

#### Просмотр конкретного коммита:

    # Показать детали коммита
    git show commit-hash
    
    # Показать конкретный файл в коммите
    git show commit-hash:filename.txt

#### Просмотр изменений:

    # Изменения в рабочей директории (не в staging)
    git diff
    
    # Изменения в staging area
    git diff --staged
    # или
    git diff --cached
    
    # Изменения между коммитами
    git diff commit1 commit2
    
    # Изменения в конкретном файле
    git diff filename.txt

* * *

### 4. Отмена изменений

#### Отменить изменения в рабочей директории:

    # Отменить изменения в конкретном файле
    git checkout -- filename.txt
    
    # Отменить все изменения
    git checkout -- .
    
    # Современный способ (Git 2.23+)
    git restore filename.txt
    git restore .

#### Убрать файлы из staging:

    # Убрать конкретный файл из staging
    git reset HEAD filename.txt
    
    # Современный способ
    git restore --staged filename.txt

#### Отмена коммитов:

##### Soft Reset (сохранить изменения):

    # Отменить последний коммит, изменения остаются в staging
    git reset --soft HEAD~1
    
    # Отменить последние 3 коммита
    git reset --soft HEAD~3

##### Mixed Reset (по умолчанию):

    # Отменить последний коммит, изменения остаются не в staging
    git reset HEAD~1
    # или
    git reset --mixed HEAD~1

##### Hard Reset (удалить изменения):

    # ⚠️ ОПАСНО! Отменить последний коммит и удалить изменения
    git reset --hard HEAD~1
    
    # Сбросить к конкретному коммиту
    git reset --hard commit-hash

##### Revert (безопасная отмена):

    # Создать новый коммит, который отменяет изменения
    git revert commit-hash
    
    # Revert без коммита
    git revert --no-commit commit-hash

**Разница:**

* `reset` - Перемещает указатель ветки, переписывает историю
* `revert` - Создаёт новый коммит, сохраняет историю

* * *

### 5. Ветки и слияние

#### Просмотр веток:

    # Список локальных веток
    git branch
    
    # Список всех веток (локальные + удалённые)
    git branch -a
    
    # Список удалённых веток
    git branch -r
    
    # Подробно (показывает последний коммит)
    git branch -v

#### Создание ветки:

    # Создать новую ветку
    git branch feature-login
    
    # Создать и переключиться на ветку
    git checkout -b feature-login
    
    # Современный способ
    git switch -c feature-login

#### Переключение веток:

    # Переключиться на существующую ветку
    git checkout branch-name
    
    # Современный способ
    git switch branch-name
    
    # Переключиться на предыдущую ветку
    git switch -

#### Удаление веток:

    # Удалить слитую ветку
    git branch -d branch-name
    
    # Принудительное удаление (даже если не слита)
    git branch -D branch-name
    
    # Удалить удалённую ветку
    git push origin --delete branch-name

#### Переименование веток:

    # Переименовать текущую ветку
    git branch -m new-name
    
    # Переименовать конкретную ветку
    git branch -m old-name new-name

#### Слияние веток:

    # Слить ветку в текущую ветку
    git merge feature-login
    
    # Слить без fast-forward (создаёт merge commit)
    git merge --no-ff feature-login
    
    # Слить и объединить коммиты
    git merge --squash feature-login

**Типы слияний:**

* **Fast-forward** - Простое, перемещает указатель вперёд
* **Three-way merge** - Создаёт merge commit
* **Squash merge** - Объединяет все коммиты в один

#### Разрешение конфликтов слияния:

    # 1. Git показывает конфликты
    git merge feature-login
    # CONFLICT (content): Merge conflict in file.txt
    
    # 2. Посмотреть конфликтные файлы
    git status
    
    # 3. Открыть файл и разрешить конфликты
    # Ищите:
    # <<<<<<< HEAD
    # Ваши изменения
    # =======
    # Их изменения
    # >>>>>>> feature-login
    
    # 4. После разрешения добавьте в staging
    git add file.txt
    
    # 5. Завершите слияние
    git commit

* * *

### 6. Удалённые репозитории

#### Просмотр удалённых репозиториев:

    # Список удалённых репозиториев
    git remote
    
    # Список с URL
    git remote -v
    
    # Показать детали удалённого репозитория
    git remote show origin

#### Добавление удалённого репозитория:

    # Добавить удалённый репозиторий
    git remote add origin https://github.com/username/repo.git
    
    # Добавить с SSH
    git remote add origin git@github.com:username/repo.git

#### Изменение URL удалённого репозитория:

    # Изменить URL удалённого репозитория
    git remote set-url origin https://github.com/username/new-repo.git

#### Удаление удалённого репозитория:

    # Удалить удалённый репозиторий
    git remote remove origin

#### Получение изменений:

    # Загрузить изменения (не сливает)
    git fetch
    
    # Получить с конкретного удалённого репозитория
    git fetch origin
    
    # Получить конкретную ветку
    git fetch origin main

#### Pull изменений:

    # Получить и слить
    git pull
    
    # Pull с конкретной ветки
    git pull origin main
    
    # Pull с rebase
    git pull --rebase

**Разница:**

* `fetch` - Только загружает изменения
* `pull` - Загружает И сливает (`fetch` + `merge`)

#### Push изменений:

    # Отправить на удалённый репозиторий
    git push
    
    # Отправить на конкретный удалённый репозиторий и ветку
    git push origin main
    
    # Отправить все ветки
    git push --all
    
    # Отправить с тегами
    git push --tags
    
    # Принудительный push (⚠️ ОПАСНО!)
    git push -f origin main
    
    # Более безопасный принудительный push
    git push --force-with-lease origin main
    
    # Установить upstream для будущих push
    git push -u origin main

* * *

### 7. Stash (Временное сохранение)

#### Временно сохранить работу:

    # Сохранить изменения
    git stash
    
    # Сохранить с сообщением
    git stash save "Работа над логином"
    
    # Сохранить включая неотслеживаемые файлы
    git stash -u
    
    # Сохранить всё (включая игнорируемые файлы)
    git stash -a

#### Просмотр stash:

    # Список сохранений
    git stash list
    
    # Показать содержимое stash
    git stash show
    
    # Показать diff stash
    git stash show -p

#### Применение stash:

    # Применить последний stash (сохраняет stash)
    git stash apply
    
    # Применить конкретный stash
    git stash apply stash@{2}
    
    # Применить и удалить stash
    git stash pop
    
    # Применить конкретный stash и удалить
    git stash pop stash@{1}

#### Удаление stash:

    # Удалить конкретный stash
    git stash drop stash@{0}
    
    # Удалить все stash
    git stash clear

* * *

### 8. Теги

#### Создание тегов:

    # Лёгкий тег
    git tag v1.0.0
    
    # Аннотированный тег (рекомендуется)
    git tag -a v1.0.0 -m "Релиз версии 1.0.0"
    
    # Тег для конкретного коммита
    git tag -a v1.0.0 commit-hash -m "Релиз версии 1.0.0"

#### Просмотр тегов:

    # Список тегов
    git tag
    
    # Список тегов с шаблоном
    git tag -l "v1.*"
    
    # Показать детали тега
    git show v1.0.0

#### Push тегов:

    # Отправить конкретный тег
    git push origin v1.0.0
    
    # Отправить все теги
    git push --tags

#### Удаление тегов:

    # Удалить локальный тег
    git tag -d v1.0.0
    
    # Удалить удалённый тег
    git push origin --delete v1.0.0

* * *

### 9. Продвинутые операции

#### Rebase:

    # Rebase текущей ветки на main
    git rebase main
    
    # Интерактивный rebase (редактирование коммитов)
    git rebase -i HEAD~3
    
    # Продолжить rebase после разрешения конфликтов
    git rebase --continue
    
    # Прервать rebase
    git rebase --abort

**Команды интерактивного rebase:**

* `pick` - Использовать коммит
* `reword` - Изменить сообщение коммита
* `edit` - Остановиться для изменения
* `squash` - Объединить с предыдущим коммитом
* `fixup` - Как squash, но отбросить сообщение
* `drop` - Удалить коммит

#### Cherry-pick:

    # Применить конкретный коммит к текущей ветке
    git cherry-pick commit-hash
    
    # Cherry-pick нескольких коммитов
    git cherry-pick commit1 commit2
    
    # Cherry-pick без коммита
    git cherry-pick --no-commit commit-hash

#### Reflog:

    # Посмотреть журнал ссылок (все действия)
    git reflog
    
    # Восстановить удалённый коммит
    git reflog
    git reset --hard HEAD@{2}

#### Clean:

    # Удалить неотслеживаемые файлы (пробный прогон)
    git clean -n
    
    # Удалить неотслеживаемые файлы
    git clean -f
    
    # Удалить неотслеживаемые файлы и директории
    git clean -fd
    
    # Удалить также игнорируемые файлы
    git clean -fdx

* * *

Файл .gitignore 🚫
------------------

**Назначение:** Указать Git, какие файлы игнорировать (не отслеживать)

### Создание .gitignore:

    # Создать файл
    touch .gitignore
    
    # Или
    echo "node_modules/" > .gitignore

### Типичные шаблоны:

    # Файлы ОС
    .DS_Store
    Thumbs.db
    desktop.ini
    
    # Файлы IDE
    .vscode/
    .idea/
    *.swp
    *.swo
    *~
    
    # Специфичные для языков
    
    # Python
    __pycache__/
    *.py[cod]
    *.pyo
    *.pyd
    .Python
    venv/
    env/
    
    # Node.js
    node_modules/
    npm-debug.log
    yarn-error.log
    
    # Java
    *.class
    *.jar
    *.war
    target/
    
    # C++
    *.o
    *.exe
    *.out
    a.out
    
    # Директории сборки
    build/
    dist/
    *.egg-info/
    
    # Логи
    *.log
    logs/
    
    # Переменные окружения
    .env
    .env.local
    
    # База данных
    *.db
    *.sqlite
    
    # Временные файлы
    *.tmp
    *.temp
    *.bak
    
    # Конфиденциальные данные
    config/secrets.yml
    *.key
    *.pem

### Игнорирование уже отслеживаемых файлов:

    # Прекратить отслеживание, но сохранить файл
    git rm --cached filename
    
    # Для директорий
    git rm -r --cached foldername/
    
    # Затем сделайте коммит
    git commit -m "Удалить отслеживаемые файлы из .gitignore"

* * *

Рабочие процессы Git 🔄
-----------------------

### 1. Feature Branch Workflow

    main ветка (продакшн)
        |
        ├── feature-1 (ваша работа)
        ├── feature-2 (работа коллеги)
        └── bugfix-login

**Процесс:**
    # 1. Создать feature ветку
    git checkout -b feature-login

    # 2. Внести изменения и закоммитить
    git add .
    git commit -m "Добавить форму входа"

    # 3. Отправить на удалённый репозиторий
    git push -u origin feature-login

    # 4. Создать Pull Request на GitHub

    # 5. После одобрения слить в main
    git checkout main
    git merge feature-login

    # 6. Удалить feature ветку
    git branch -d feature-login
    git push origin --delete feature-login

* * *

### 2. Gitflow Workflow

    main (продакшн)
        |
    develop (интеграция)
        |
        ├── feature/login
        ├── feature/profile
        └── hotfix/critical-bug

**Ветки:**

* `main` - Продакшн код
* `develop` - Интеграционная ветка
* `feature/*` - Новые функции
* `release/*` - Подготовка релиза
* `hotfix/*` - Экстренные исправления

* * *

### 3. Forking Workflow

**Используется для open source:**

1. Fork репозитория на GitHub

2. Клонировать ваш fork

3. Создать feature ветку

4. Внести изменения

5. Отправить на ваш fork

6. Создать Pull Request в оригинальный репозиторий
   
   # 1. Клонировать ваш fork
   
    git clone https://github.com/YOUR_USERNAME/repo.git
   
   # 2. Добавить upstream remote
   
    git remote add upstream https://github.com/ORIGINAL_OWNER/repo.git
   
   # 3. Создать feature ветку
   
    git checkout -b feature-awesome
   
   # 4. Внести изменения и закоммитить
   
    git add .
    git commit -m "Добавить потрясающую функцию"
   
   # 5. Отправить на ваш fork
   
    git push origin feature-awesome
   
   # 6. Создать Pull Request на GitHub
   
   # 7. Поддерживать fork в актуальном состоянии
   
    git fetch upstream
    git checkout main
    git merge upstream/main
    git push origin main

* * *

Специфичные функции GitHub 🐙
-----------------------------

### 1. Pull Requests (PRs)

**Что это:** Запрос на слияние ваших изменений в другую ветку

**Процесс:**

1. Отправить ветку на GitHub
2. Нажать "Compare & pull request"
3. Заполнить шаблон PR
4. Запросить ревьюеров
5. Адресовать отзывы
6. Слить после одобрения

### 2. Issues

**Отслеживание багов и функций:**
    # Шаблон отчёта об ошибке

    ## Описание
    В чём проблема?

    ## Шаги воспроизведения
    1. Перейти к...
    2. Кликнуть на...
    3. Увидеть ошибку

    ## Ожидаемое поведение
    Что должно произойти?

    ## Фактическое поведение
    Что происходит на самом деле?

    ## Окружение
    - ОС: Windows 10
    - Браузер: Chrome 120
    - Версия: 1.2.3

### 3. GitHub Actions (CI/CD)

**Автоматизация рабочих процессов:**
    # .github/workflows/test.yml
    name: Запуск тестов

    on: [push, pull_request]

    jobs:
      test:
        runs-on: ubuntu-latest
        steps:
          - uses: actions/checkout@v2
          - name: Запустить тесты
            run: |
              npm install
              npm test

### 4. SSH ключи

**Настройка SSH для GitHub:**
    # 1. Сгенерировать SSH ключ
    ssh-keygen -t ed25519 -C "your.email@example.com"

    # 2. Запустить SSH агент
    eval "$(ssh-agent -s)"

    # 3. Добавить ключ к агенту
    ssh-add ~/.ssh/id_ed25519

    # 4. Скопировать публичный ключ
    cat ~/.ssh/id_ed25519.pub

    # 5. Добавить на GitHub:
    # Settings → SSH and GPG keys → New SSH key

    # 6. Проверить соединение
    ssh -T git@github.com

* * *

Лучшие практики ✅
-----------------

### 1. Коммитьте часто, отправляйте регулярно

    # ✅ Хорошо
    git commit -m "Добавить форму входа"
    git commit -m "Добавить валидацию"
    git commit -m "Добавить обработку ошибок"
    
    # ❌ Плохо
    # Подождать 3 дня, затем один огромный коммит
    git commit -m "Добавить всю систему входа"

### 2. Пишите осмысленные сообщения коммитов

    # ✅ Хорошо
    git commit -m "Исправить null pointer exception в UserService.login()"
    git commit -m "Добавить валидацию email в форму регистрации"
    
    # ❌ Плохо
    git commit -m "fix"
    git commit -m "обновления"
    git commit -m "asdf"

**Конвенция:**
    <тип>: <тема>

    <тело>

    <подвал>

**Типы:**

* `feat:` - Новая функция
* `fix:` - Исправление бага
* `docs:` - Документация
* `style:` - Форматирование
* `refactor:` - Реструктуризация кода
* `test:` - Добавление тестов
* `chore:` - Обслуживание

**Пример:**
    git commit -m "feat: добавить аутентификацию пользователя

    - Реализовать JWT токены
    - Добавить endpoints login/logout
    - Добавить хеширование паролей с bcrypt

    Closes #123"

### 3. Делайте коммиты атомарными

* Один коммит = одно логическое изменение
* Легко понять
* Легко откатить при необходимости

### 4. Используйте ветки

    # ✅ Хорошо - используйте ветки
    git checkout -b feature-payment
    # внести изменения
    git commit
    git push origin feature-payment
    
    # ❌ Плохо - работать напрямую в main
    git checkout main
    # внести изменения
    git commit

### 5. Pull перед Push

    # Всегда делайте pull перед push
    git pull origin main
    git push origin main

### 6. Проверяйте перед коммитом

    # Проверьте что коммитите
    git diff
    git status
    
    # Затем коммитьте
    git add .
    git commit -m "Сообщение"

### 7. Используйте .gitignore

* Не коммитьте конфиденциальные данные
* Не коммитьте зависимости
* Не коммитьте артефакты сборки

### 8. Не используйте Force Push на общих ветках

    # ❌ Опасно на общих ветках
    git push -f origin main
    
    # ✅ Только на ваших личных ветках
    git push -f origin feature-my-work

* * *

Распространённые ошибки и решения 🚨
------------------------------------

### 1. Закоммитили не в ту ветку

    # Решение: Stash, переключить ветку, применить
    git stash
    git checkout correct-branch
    git stash pop
    git add .
    git commit -m "Сообщение"

### 2. Случайно закоммитили конфиденциальные данные

    # Решение: Удалить из истории
    git filter-branch --force --index-filter \
      "git rm --cached --ignore-unmatch path/to/file" \
      --prune-empty --tag-name-filter cat -- --all
    
    # Или используйте BFG Repo-Cleaner (проще)
    bfg --delete-files sensitive.txt

### 3. Конфликт слияния

    # 1. Получить последние изменения
    git pull origin main
    
    # 2. Посмотреть конфликты
    git status
    
    # 3. Открыть файлы и разрешить
    # Удалить маркеры <<<<<<, ======, >>>>>>
    # Оставить нужный код
    
    # 4. Добавить разрешённые файлы в staging
    git add resolved-file.txt
    
    # 5. Завершить слияние
    git commit

### 4. Случайно удалили ветку

    # Найти удалённую ветку в reflog
    git reflog
    
    # Восстановить её
    git checkout -b branch-name commit-hash

### 5. Отправили неправильный коммит

    # Если ещё не отправили
    git reset --hard HEAD~1
    
    # Если уже отправили (и это ваша ветка)
    git reset --hard HEAD~1
    git push -f origin branch-name
    
    # Если это общая ветка (безопаснее)
    git revert commit-hash
    git push origin branch-name

### 6. Ошибка больших файлов

    # GitHub отклоняет файлы > 100MB
    
    # Решение: Используйте Git LFS
    git lfs install
    git lfs track "*.psd"
    git add .gitattributes
    git add large-file.psd
    git commit -m "Добавить большой файл с LFS"

* * *

Алиасы Git (Сокращения) ⚡
-------------------------

**Сделайте команды Git короче:**
    # Настройка алиасов
    git config --global alias.st status
    git config --global alias.co checkout
    git config --global alias.br branch
    git config --global alias.cm commit
    git config --global alias.last 'log -1 HEAD'
    git config --global alias.unstage 'reset HEAD --'
    git config --global alias.visual 'log --oneline --graph --all'

    # Использование
    git st          # вместо git status
    git co main     # вместо git checkout main
    git visual      # красивый git log

**Продвинутые алиасы:**
    # Красивый лог
    git config --global alias.lg "log --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit"

    # Отменить последний коммит
    git config --global alias.undo 'reset HEAD~1 --mixed'

    # Amend без изменения сообщения
    git config --global alias.amend 'commit --amend --no-edit'

* * *

Git Hooks (Хуки) 🪝
-------------------

**Автоматизируйте действия на событиях Git:**

### Распространённые хуки:

* `pre-commit` - Выполняется перед коммитом
* `commit-msg` - Валидация сообщения коммита
* `pre-push` - Выполняется перед push
* `post-merge` - Выполняется после слияния

### Пример: Pre-commit Hook

    # .git/hooks/pre-commit
    
    #!/bin/sh
    # Запустить тесты перед коммитом
    
    npm test
    
    if [ $? -ne 0 ]; then
        echo "Тесты провалились! Коммит отменён."
        exit 1
    fi

**Сделать исполняемым:**
    chmod +x .git/hooks/pre-commit

* * *

Внутреннее устройство Git (Как работает Git) 🔬
-----------------------------------------------

### Объекты Git:

1. **Blob** - Содержимое файла
2. **Tree** - Структура директорий
3. **Commit** - Снимок с метаданными
4. **Tag** - Именованная ссылка на коммит

### Внутри директории .git:

    .git/
    ├── HEAD              # Указатель на текущую ветку
    ├── config            # Конфигурация репозитория
    ├── description       # Описание репозитория
    ├── hooks/            # Git хуки
    ├── index             # Staging area
    ├── objects/          # Git объекты (коммиты, blob'ы, деревья)
    ├── refs/             # Ссылки на ветки и теги
    │   ├── heads/        # Локальные ветки
    │   ├── remotes/      # Удалённые ветки
    │   └── tags/         # Теги
    └── logs/             # Журналы ссылок

### Как работают коммиты:

    Объект коммита:
    - Дерево (снимок файлов)
    - Родительский(е) коммит(ы)
    - Информация об авторе
    - Информация о коммитере
    - Сообщение коммита
    - SHA-1 хеш (уникальный ID)

* * *

Команды для устранения неполадок 🔧
-----------------------------------

    # Проверить, является ли директория Git репозиторием
    git rev-parse --is-inside-work-tree
    
    # Показать текущую ветку
    git branch --show-current
    
    # Показать URL удалённого репозитория
    git remote get-url origin
    
    # Проверить репозиторий
    git fsck
    
    # Очистить репозиторий
    git gc
    git prune
    
    # Показать расположение конфигурации
    git config --list --show-origin
    
    # Отладка команды
    GIT_TRACE=1 git status

* * *

Быстрая справочная шпаргалка 📋
-------------------------------

### Основные команды:

    # Настройка
    git init                    # Инициализировать репозиторий
    git clone URL               # Клонировать репозиторий
    
    # Базовый рабочий процесс
    git status                  # Проверить статус
    git add .                   # Добавить всё в staging
    git commit -m "msg"         # Закоммитить
    git push                    # Отправить на удалённый репозиторий
    git pull                    # Получить с удалённого репозитория
    
    # Ветвление
    git branch                  # Список веток
    git branch name             # Создать ветку
    git checkout name           # Переключиться на ветку
    git checkout -b name        # Создать и переключиться
    git merge name              # Слить ветку
    
    # Отмена
    git reset HEAD~1            # Отменить последний коммит (сохранить изменения)
    git reset --hard HEAD~1     # Отменить последний коммит (удалить изменения)
    git revert commit-hash      # Безопасная отмена
    
    # История
    git log                     # Посмотреть коммиты
    git log --oneline           # Компактный вид
    git diff                    # Посмотреть изменения
    
    # Удалённые репозитории
    git remote -v               # Посмотреть удалённые репозитории
    git fetch                   # Загрузить изменения
    git push -u origin main     # Отправить и установить upstream
    
    # Stash
    git stash                   # Сохранить работу
    git stash pop               # Восстановить работу

* * *

Практики безопасности 🔒
------------------------

### 1. Никогда не коммитьте конфиденциальные данные

    # ❌ Не коммитьте:
    # - Пароли
    # - API ключи
    # - Приватные ключи
    # - .env файлы
    # - Учётные данные БД

### 2. Используйте SSH вместо HTTPS

    # Более безопасно для приватных репозиториев
    git remote set-url origin git@github.com:user/repo.git

### 3. Подписывайте коммиты (GPG)

    # Сгенерировать GPG ключ
    gpg --gen-key
    
    # Настроить Git
    git config --global user.signingkey YOUR_KEY_ID
    git config --global commit.gpgsign true
    
    # Подписать коммит
    git commit -S -m "Подписанный коммит"

### 4. Проверяйте перед отправкой

    # Всегда проверяйте что отправляете
    git diff origin/main
    git log origin/main..HEAD

### 5. Используйте .gitignore

    # Всегда игнорируйте конфиденциальные файлы
    echo ".env" >> .gitignore
    echo "config/secrets.yml" >> .gitignore

* * *

Советы по производительности ⚡
------------------------------

### 1. Поверхностное клонирование (Быстрее)

    # Клонировать только недавнюю историю
    git clone --depth 1 URL

### 2. Разреженная проверка (Большие репозитории)

    # Клонировать только конкретные файлы/папки
    git clone --filter=blob:none --sparse URL
    cd repo
    git sparse-checkout init
    git sparse-checkout set path/to/folder

### 3. Очистка

    # Удалить старые объекты
    git gc --aggressive
    
    # Удалить недостижимые объекты
    git prune

* * *

Ресурсы для обучения 📚
-----------------------

### Официальная документация:

* https://git-scm.com/doc
* https://git-scm.com/book/ru/v2

### Интерактивное обучение:

* https://learngitbranching.js.org/
* https://github.com/jlord/git-it-electron

### Практика:

* https://github.com/skills
* https://www.katacoda.com/courses/git

### GitHub Guides:

* https://guides.github.com/

### Русскоязычные ресурсы:

* https://githowto.com/ru
* https://git-scm.com/book/ru/v2

* * *

Практические сценарии 🎯
------------------------

### Сценарий 1: Начало нового проекта

    # 1. Создать директорию проекта
    mkdir my-project
    cd my-project
    
    # 2. Инициализировать Git
    git init
    
    # 3. Создать .gitignore
    cat > .gitignore << EOF
    node_modules/
    .env
    .DS_Store
    EOF
    
    # 4. Создать README
    echo "# My Project" > README.md
    
    # 5. Первый коммит
    git add .
    git commit -m "Initial commit: Project setup"
    
    # 6. Создать репозиторий на GitHub, затем:
    git remote add origin https://github.com/username/my-project.git
    git push -u origin main

* * *

### Сценарий 2: Добавление новой функции

    # 1. Убедиться что main актуален
    git checkout main
    git pull origin main
    
    # 2. Создать feature ветку
    git checkout -b feature/user-auth
    
    # 3. Работать над функцией
    # ... редактировать файлы ...
    
    # 4. Коммитить изменения постепенно
    git add src/auth/
    git commit -m "feat: add login form"
    
    git add src/auth/validation.js
    git commit -m "feat: add email validation"
    
    git add tests/auth.test.js
    git commit -m "test: add auth tests"
    
    # 5. Отправить на GitHub
    git push -u origin feature/user-auth
    
    # 6. Создать Pull Request на GitHub
    
    # 7. После одобрения и слияния
    git checkout main
    git pull origin main
    git branch -d feature/user-auth

* * *

### Сценарий 3: Исправление бага в продакшн

    # 1. Создать hotfix ветку от main
    git checkout main
    git checkout -b hotfix/critical-bug
    
    # 2. Исправить баг
    # ... редактировать файлы ...
    
    # 3. Закоммитить исправление
    git add .
    git commit -m "fix: resolve null pointer in payment processing"
    
    # 4. Отправить и создать PR
    git push -u origin hotfix/critical-bug
    
    # 5. После срочного одобрения - слить
    git checkout main
    git merge hotfix/critical-bug
    git push origin main
    
    # 6. Также слить в develop
    git checkout develop
    git merge hotfix/critical-bug
    git push origin develop
    
    # 7. Удалить hotfix ветку
    git branch -d hotfix/critical-bug
    git push origin --delete hotfix/critical-bug

* * *

### Сценарий 4: Вклад в Open Source проект

    # 1. Fork проекта на GitHub
    
    # 2. Клонировать ваш fork
    git clone https://github.com/YOUR_USERNAME/project.git
    cd project
    
    # 3. Добавить upstream
    git remote add upstream https://github.com/ORIGINAL_OWNER/project.git
    
    # 4. Создать feature ветку
    git checkout -b feature/improve-docs
    
    # 5. Внести изменения
    # ... редактировать файлы ...
    
    # 6. Закоммитить
    git add .
    git commit -m "docs: improve installation instructions"
    
    # 7. Убедиться что fork актуален
    git fetch upstream
    git rebase upstream/main
    
    # 8. Отправить на ваш fork
    git push origin feature/improve-docs
    
    # 9. Создать Pull Request на GitHub к оригинальному репозиторию
    
    # 10. После обратной связи внести изменения
    # ... редактировать файлы ...
    git add .
    git commit -m "docs: address review feedback"
    git push origin feature/improve-docs

* * *

### Сценарий 5: Синхронизация с командой

    # Утро - начало работы
    git checkout main
    git pull origin main
    git checkout -b feature/my-work
    
    # В течение дня
    git add .
    git commit -m "Work in progress"
    
    # Перед обедом - сохранить работу
    git push origin feature/my-work
    
    # После обеда - продолжить
    git pull origin feature/my-work
    
    # Коллега отправил изменения в main
    git checkout main
    git pull origin main
    git checkout feature/my-work
    git rebase main  # или git merge main
    
    # Конец дня - отправить прогресс
    git push origin feature/my-work

* * *

Глоссарий терминов 📖
---------------------

| Термин                | Определение                                      |
| --------------------- | ------------------------------------------------ |
| **Repository (Repo)** | Папка проекта, отслеживаемая Git                 |
| **Commit**            | Снимок изменений в коде                          |
| **Branch**            | Параллельная линия разработки                    |
| **Merge**             | Объединение веток                                |
| **Pull Request (PR)** | Запрос на слияние изменений                      |
| **Fork**              | Личная копия чужого репозитория                  |
| **Clone**             | Локальная копия удалённого репозитория           |
| **Remote**            | Удалённая версия репозитория                     |
| **Origin**            | Имя по умолчанию для удалённого репозитория      |
| **Main/Master**       | Основная ветка проекта                           |
| **HEAD**              | Указатель на текущий коммит                      |
| **Staging Area**      | Промежуточная зона перед коммитом                |
| **Working Directory** | Ваши текущие файлы                               |
| **Stash**             | Временное сохранение изменений                   |
| **Tag**               | Именованная метка на коммите (обычно для версий) |
| **SHA/Hash**          | Уникальный идентификатор коммита                 |
| **Conflict**          | Противоречивые изменения в одном файле           |
| **Rebase**            | Перемещение коммитов на новую базу               |
| **Cherry-pick**       | Применение конкретного коммита                   |
| **Upstream**          | Оригинальный репозиторий (при fork)              |
| **Downstream**        | Ваш fork                                         |

* * *

Частые вопросы (FAQ) ❓
----------------------

### Q: В чём разница между Git и GitHub?

**A:** Git - инструмент контроля версий на вашем компьютере. GitHub - веб-сервис для хранения Git репозиториев онлайн.

### Q: Что лучше: merge или rebase?

**A:**

* **Merge** - сохраняет всю историю, создаёт merge commit
* **Rebase** - создаёт линейную историю, но переписывает коммиты
* Для общих веток используйте merge
* Для личных веток можете использовать rebase

### Q: Как отменить git push?

**A:** Если отправили в свою ветку:
    git reset --hard HEAD~1
    git push -f origin branch-name

Если в общую ветку - используйте `git revert`

### Q: Что делать при конфликте слияния?

**A:**

1. `git status` - посмотреть конфликтные файлы
2. Открыть файлы и разрешить конфликты
3. `git add` - добавить разрешённые файлы
4. `git commit` - завершить слияние

### Q: Как удалить последний коммит?

**A:**

* Сохранить изменения: `git reset --soft HEAD~1`
* Удалить изменения: `git reset --hard HEAD~1`

### Q: Как изменить сообщение последнего коммита?

**A:** `git commit --amend -m "Новое сообщение"`

### Q: Что делать если случайно закоммитил конфиденциальные данные?

**A:**

1. Немедленно удалить из истории (git filter-branch или BFG)
2. Изменить все пароли/ключи
3. Force push очищенную историю
4. Добавить файлы в .gitignore

### Q: Как посмотреть изменения перед коммитом?

**A:** `git diff` (несохранённые) или `git diff --staged` (в staging)

### Q: Можно ли восстановить удалённый коммит?

**A:** Да, если недавно: `git reflog` → `git reset --hard commit-hash`

### Q: Что значит "detached HEAD"?

**A:** Вы переключились на конкретный коммит, а не на ветку. Создайте ветку если хотите сохранить изменения: `git checkout -b new-branch`

* * *

Продвинутые техники 🎓
----------------------

### 1. Git Bisect (Поиск бага)

    # Найти коммит, который внёс баг
    git bisect start
    git bisect bad                  # текущая версия плохая
    git bisect good v1.0.0          # эта версия была хорошей
    
    # Git будет переключать на коммиты посередине
    # Тестируйте каждый и говорите:
    git bisect good   # если работает
    git bisect bad    # если не работает
    
    # После нахождения
    git bisect reset

### 2. Git Blame (Кто изменил?)

    # Посмотреть кто изменил каждую строку файла
    git blame filename.txt
    
    # С номерами строк
    git blame -L 10,20 filename.txt
    
    # Игнорировать whitespace изменения
    git blame -w filename.txt

### 3. Git Worktree (Несколько рабочих директорий)

    # Создать дополнительную рабочую директорию
    git worktree add ../project-feature feature-branch
    
    # Работать в обеих одновременно
    cd ../project-feature
    # ... работа ...
    
    # Удалить worktree
    git worktree remove ../project-feature

### 4. Git Submodules (Вложенные репозитории)

    # Добавить submodule
    git submodule add https://github.com/user/lib.git libs/lib
    
    # Клонировать проект с submodules
    git clone --recurse-submodules https://github.com/user/project.git
    
    # Обновить submodules
    git submodule update --remote

### 5. Git Patch (Отправка изменений по email)

    # Создать patch файл
    git format-patch -1 HEAD
    
    # Применить patch
    git apply 0001-fix-bug.patch

* * *

Заключительные советы 💡
------------------------

### Для новичков:

1. ✅ Начните с базовых команд: init, add, commit, push, pull
2. ✅ Практикуйтесь на личных проектах
3. ✅ Не бойтесь ошибок - почти всё можно откатить
4. ✅ Читайте сообщения об ошибках Git
5. ✅ Используйте git status часто

### Для продвинутых:

1. ✅ Изучите git rebase и cherry-pick
2. ✅ Настройте алиасы для часто используемых команд
3. ✅ Используйте git hooks для автоматизации
4. ✅ Изучите внутреннее устройство Git
5. ✅ Вносите вклад в open source проекты

### Общие советы:

1. ✅ Коммитьте часто, маленькими порциями
2. ✅ Пишите понятные сообщения коммитов
3. ✅ Используйте ветки для новых функций
4. ✅ Проверяйте изменения перед коммитом
5. ✅ Регулярно синхронизируйтесь с командой
6. ✅ Резервируйте важную работу (push на удалённый репозиторий)
7. ✅ Не коммитьте конфиденциальные данные
8. ✅ Используйте .gitignore правильно
9. ✅ Читайте документацию
10. ✅ Практикуйтесь регулярно

* * *

Итоговая шпаргалка - Самые важные команды 🎯
--------------------------------------------

    # НАСТРОЙКА (один раз)
    git config --global user.name "Имя"
    git config --global user.email "email@example.com"
    
    # СОЗДАНИЕ/КЛОНИРОВАНИЕ
    git init                           # новый репозиторий
    git clone URL                      # клонировать репозиторий
    
    # ЕЖЕДНЕВНАЯ РАБОТА
    git status                         # что изменилось?
    git add .                          # добавить всё
    git add file.txt                   # добавить файл
    git commit -m "сообщение"          # закоммитить
    git push                           # отправить на GitHub
    git pull                           # получить с GitHub
    
    # ВЕТКИ
    git branch                         # список веток
    git branch name                    # создать ветку
    git checkout name                  # переключиться
    git checkout -b name               # создать и переключиться
    git merge name                     # слить ветку
    git branch -d name                 # удалить ветку
    
    # ИСТОРИЯ И ИЗМЕНЕНИЯ
    git log                            # история коммитов
    git log --oneline                  # кратко
    git diff                           # что изменилось?
    
    # ОТМЕНА
    git checkout -- file.txt           # отменить изменения
    git reset HEAD~1                   # отменить коммит
    git revert commit-hash             # безопасная отмена
    
    # STASH
    git stash                          # сохранить временно
    git stash pop                      # восстановить
    
    # УДАЛЁННЫЕ РЕПОЗИТОРИИ
    git remote -v                      # список удалённых
    git fetch                          # загрузить изменения
    git push origin main               # отправить
    git pull origin main               # получить
    
    # ПОМОЩЬ
    git help                           # общая помощь
    git help command                   # помощь по команде

* * *

Последнее слово 🎉
------------------

**Git - это мощный инструмент**, и он может показаться сложным на первый взгляд. Но помните:

1. **Все проходят через это** - даже опытные разработчики когда-то были новичками
2. **Практика делает мастера** - чем больше используете Git, тем проще становится
3. **Ошибки - это нормально** - почти всё можно откатить в Git
4. **Начните с основ** - не нужно знать всё сразу
5. **Гуглите без стыда** - все это делают


