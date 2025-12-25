# TCS GitHub Interview Preparation - Complete Question Bank

## 1️⃣ Basics (100% MUST)

### What is Git?

Git is a distributed version control system that tracks changes in files and coordinates work among multiple developers. It allows you to save snapshots of your project and manage different versions efficiently.

### What is GitHub?

GitHub is a cloud-based hosting service for Git repositories. It provides a web interface for Git repositories plus additional features like issue tracking, pull requests, and project management tools.

### Difference between Git and GitHub

| Feature | Git | GitHub |
|---------|-----|--------|
| Type | Version control system | Hosting service |
| Location | Local computer | Cloud-based |
| Interface | Command line | Web interface |
| Functionality | Version control | Git + collaboration tools |
| Dependency | Standalone | Requires Git |

### Why do we use Git?

- **Version Control**: Track changes and history
- **Collaboration**: Multiple developers can work together
- **Backup**: Distributed nature provides backup
- **Branching**: Work on features independently
- **Rollback**: Easily revert to previous versions
- **Merge**: Combine changes from different sources

### What is a repository?

A repository (repo) is a storage location for your project that contains all files, folders, and version history. It's like a project folder that Git tracks.

### Local repository vs remote repository

**Local Repository:**
- Stored on your computer
- Where you make changes
- Work offline

**Remote Repository:**
- Stored on server (like GitHub)
- Shared with team members
- Requires internet connection

Local repos sync with remote repos using push/pull operations

### What is version control?

Version control is a system that records changes to files over time so you can recall specific versions later. It helps track who made what changes and when.

### Centralized vs distributed version control

**Centralized:**
- Single central server stores all versions
- Example: SVN
- Requires server connection

**Distributed:**
- Every developer has complete copy of project history
- Example: Git
- Can work offline and have full backup

### What is a commit?

A commit is a snapshot of your project at a specific point in time. It includes:
- Changes made to files
- Commit message describing changes
- Author information
- Timestamp
- Unique hash ID

### What is a branch?

A branch is an independent line of development. It allows you to work on features without affecting the main codebase. Think of it as a parallel universe of your project.

### What is the default branch?

The default branch is the main branch of repository (usually called "main" or "master"). It's the primary branch where stable code lives and other branches merge into.

### What is a clone?

Clone creates a complete copy of a remote repository on your local machine, including all files, branches, and commit history.

### What is a fork?

Fork creates a personal copy of someone else's repository on your GitHub account. You can make changes without affecting the original repository.

### What is a pull?

Pull downloads and merges changes from remote repository to your local repository. It's combination of `git fetch` + `git merge`.

## 2️⃣ Core Git Commands (Very Common)

### git init – what does it do?

`git init` initializes a new Git repository in current directory. It creates a hidden `.git` folder that contains all Git metadata and tracking information.

### git status – purpose

`git status` shows the current state of your working directory:
- Which files are modified
- Which files are staged for commit
- Which files are untracked
- Current branch information

### git add – what happens internally?

`git add` stages changes for the next commit. It moves files from working directory to staging area (index). Git creates blob objects for file contents and updates the index.

### git commit – what does it store?

`git commit` creates a snapshot containing:
- Tree object (directory structure)
- Blob objects (file contents)
- Commit object (metadata: author, timestamp, message, parent commits)
- Unique SHA-1 hash

### git log – use

`git log` displays commit history showing:
- Commit hashes
- Author and date
- Commit messages
- Branch information

### git diff – when to use

`git diff` shows differences between:
- Working directory and staging area
- Staging area and last commit
- Different commits or branches
- Use before committing to review changes

### git branch – create/list/delete

```bash
git branch                    # List branches
git branch feature-name       # Create new branch
git branch -d feature-name    # Delete branch
git branch -m new-name        # Rename current branch
```

### git checkout – usage

`git checkout` switches between branches or restores files:
```bash
git checkout branch-name      # Switch to branch
git checkout -b new-branch    # Create and switch to new branch
git checkout -- filename     # Restore file from last commit
```

### git switch – difference from checkout

`git switch` is newer command specifically for switching branches:
- `git switch branch-name` (switch branch)
- `git switch -c new-branch` (create and switch)
- More intuitive than checkout for branch operations

### git merge – how it works

`git merge` combines changes from different branches:
1. Git finds common ancestor commit
2. Applies changes from both branches
3. Creates merge commit if needed
4. Updates current branch pointer

### git pull vs git fetch

**git pull:**
- Downloads + merges changes
- Updates working directory
- Can cause merge conflicts
- `fetch + merge` combined

**git fetch:**
- Only downloads changes
- Updates remote tracking branches
- Safe operation
- Just fetches remote changes

### git push – what happens during push?

`git push` uploads local commits to remote repository:
1. Compares local and remote branch
2. Uploads missing commits and objects
3. Updates remote branch pointer
4. May reject if remote has newer commits

### git remote – purpose

`git remote` manages connections to remote repositories:
```bash
git remote -v                 # List remote repositories
git remote add origin URL     # Add remote repository
git remote remove origin      # Remove remote
```

### git remote add origin

Adds a remote repository named "origin" (conventional name for main remote):
```bash
git remote add origin https://github.com/user/repo.git
```

### git reset vs git revert

**git reset:**
- Moves branch pointer backward
- Rewrites history
- Dangerous for shared repos
- Example: `git reset --hard HEAD~1`

**git revert:**
- Creates new commit that undoes changes
- Preserves history
- Safe for shared repos
- Example: `git revert commit-hash`

### git stash – use case

`git stash` temporarily saves uncommitted changes:
- Switch branches without committing
- Pull updates when you have local changes
- Experiment with code without losing work

```bash
git stash                     # Save changes
git stash pop                 # Restore changes
```

## 3️⃣ Branching & Merging (Asked Often)

### What is branching strategy?

Branching strategy defines how team organizes branches:
- **Git Flow**: main, develop, feature, release, hotfix branches
- **GitHub Flow**: main branch + feature branches
- **Feature Branch**: Each feature gets its own branch

### Why do we create branches?

- **Isolation**: Work on features without affecting main code
- **Parallel Development**: Multiple features simultaneously
- **Experimentation**: Try ideas without risk
- **Code Review**: Review changes before merging
- **Release Management**: Separate development from production

### Merge vs rebase

**Merge:**
- Preserves branch history
- Creates merge commit
- Non-destructive
- Shows when branches diverged

**Rebase:**
- Creates linear history
- No merge commit
- Rewrites commit history
- Cleaner history

### What is a fast-forward merge?

Fast-forward merge happens when target branch hasn't diverged from source branch. Git simply moves the branch pointer forward without creating merge commit.

### What is a merge conflict?

Merge conflict occurs when Git cannot automatically merge changes because:
- Same lines modified in both branches
- File deleted in one branch, modified in another
- Binary files changed differently

### How do you resolve a merge conflict?

1. Git marks conflicted files with conflict markers
2. Open files and manually resolve conflicts
3. Remove conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`)
4. Stage resolved files with `git add`
5. Complete merge with `git commit`

### What happens if two people modify same file?

- If different lines: Git merges automatically
- If same lines: Merge conflict occurs
- Must resolve conflicts manually
- Last person to push must resolve conflicts

### How do you keep your branch updated?

```bash
git checkout main
git pull origin main          # Update main branch
git checkout feature-branch
git merge main               # Merge main into feature
# OR
git rebase main              # Rebase feature on main
```

### What is HEAD?

HEAD is a pointer to the current commit you're working on. It usually points to the tip of current branch.

### Detached HEAD state

Detached HEAD occurs when HEAD points directly to a commit instead of a branch. Happens when you checkout a specific commit. Changes made here can be lost if not saved to a branch.

## 4️⃣ GitHub-Specific Questions

### What is GitHub used for?

- **Code Hosting**: Store Git repositories in cloud
- **Collaboration**: Team development and code sharing
- **Issue Tracking**: Bug reports and feature requests
- **Project Management**: Organize work with boards
- **Documentation**: README, wikis, GitHub Pages
- **CI/CD**: Automated testing and deployment

### What is a pull request (PR)?

Pull request is a GitHub feature that lets you propose changes to a repository. It allows code review and discussion before merging changes into main branch.

### Steps to raise a pull request

1. Fork repository (if not collaborator)
2. Create feature branch
3. Make changes and commit
4. Push branch to GitHub
5. Click "New Pull Request"
6. Add title and description
7. Select reviewers
8. Submit PR

### What is code review?

Code review is the process where team members examine proposed changes before they're merged. Reviewers check for:
- Code quality and standards
- Bugs and security issues
- Performance implications
- Documentation completeness

### What are issues in GitHub?

Issues are used to track bugs, feature requests, and tasks. They include:
- Title and description
- Labels for categorization
- Assignees
- Milestones
- Comments and discussions

### What are labels and milestones?

- **Labels**: Tags to categorize issues/PRs (bug, enhancement, priority)
- **Milestones**: Group issues/PRs for specific releases or goals
- Help organize and track project progress

### What is README.md?

README.md is a markdown file that serves as the front page of your repository. It's the first thing visitors see and should explain what your project does.

### What should a good README contain?

- **Project Title**: Clear name
- **Description**: What the project does
- **Installation**: How to set up
- **Usage**: How to use the project
- **Contributing**: How others can contribute
- **License**: Legal information
- **Contact**: How to reach maintainers

### What is .gitignore?

.gitignore is a file that tells Git which files and directories to ignore. These files won't be tracked or committed to repository.

### Why is .gitignore important?

- **Security**: Avoid committing secrets, passwords
- **Performance**: Exclude large files, build artifacts
- **Cleanliness**: Keep repository focused on source code
- **Platform**: Ignore OS-specific files (.DS_Store, Thumbs.db)

### What are GitHub releases?

Releases are packaged versions of your software with:
- Version tags
- Release notes
- Downloadable assets
- Pre-release options

### Public vs private repositories

**Public:**
- Visible to everyone
- Free unlimited repos
- Good for open source
- Anyone can fork

**Private:**
- Only visible to collaborators
- Limited free private repos
- Good for proprietary code
- Restricted access

### What is GitHub Pages?

GitHub Pages is a static site hosting service that publishes websites directly from GitHub repositories. Great for documentation, portfolios, and project websites.

### How do you deploy a project using GitHub?

- **GitHub Pages**: For static websites
- **GitHub Actions**: For CI/CD pipelines
- **Third-party services**: Heroku, Netlify, Vercel
- **Container registries**: Docker Hub integration

## 5️⃣ Team & Collaboration Scenarios (VERY IMPORTANT)

### How does a team collaborate using GitHub?

1. **Central Repository**: Team shares main repository
2. **Branching**: Each developer creates feature branches
3. **Pull Requests**: Propose changes for review
4. **Code Review**: Team reviews and discusses changes
5. **Merge**: Approved changes merged to main branch
6. **Continuous Integration**: Automated testing

### How do multiple developers work on same project?

- **Clone** repository to local machine
- **Create branches** for different features
- **Regular pulls** to stay updated
- **Push changes** to remote branches
- **Pull requests** for code review
- **Merge** approved changes

### What is a fork-and-pull workflow?

1. **Fork** the original repository
2. **Clone** your fork locally
3. **Create branch** for changes
4. **Make changes** and commit
5. **Push** to your fork
6. **Create pull request** to original repository

### How do you avoid merge conflicts?

- **Frequent pulls**: Stay updated with main branch
- **Small commits**: Make focused, small changes
- **Communication**: Coordinate with team on file changes
- **Feature branches**: Isolate work
- **Regular merges**: Don't let branches diverge too much

### How do you review someone's code?

1. **Read the PR description** and requirements
2. **Check code quality**: Style, readability, best practices
3. **Test functionality**: Does it work as expected?
4. **Security review**: Look for vulnerabilities
5. **Performance**: Check for efficiency issues
6. **Leave comments**: Constructive feedback
7. **Approve or request changes**

### What happens after a PR is merged?

1. Changes are integrated into target branch
2. Feature branch can be deleted
3. Local repositories should pull updates
4. CI/CD pipelines may trigger
5. Issue linked to PR gets closed

### How do you rollback a bad commit?

```bash
# If not pushed yet
git reset --hard HEAD~1

# If already pushed (safe way)
git revert commit-hash

# Emergency rollback
git reset --hard good-commit-hash
git push --force-with-lease
```

### What if you pushed wrong code?

- **Recent commit**: Use `git revert` to create fixing commit
- **Multiple commits**: Revert each commit in reverse order
- **Force push**: Only if no one else pulled (dangerous)
- **Hotfix**: Create immediate fix and deploy

### How do you handle production bugs using Git?

1. **Create hotfix branch** from main/production
2. **Fix the bug** with minimal changes
3. **Test thoroughly**
4. **Create PR** for review
5. **Merge to main** and deploy
6. **Merge back** to development branch

## 6️⃣ Advanced / Scenario-Based (Sometimes Asked)

### Difference between reset, revert, and checkout

**reset:**
- Move branch pointer
- Dangerous
- Rewrites history

**revert:**
- Undo with new commit
- Safe
- Preserves history

**checkout:**
- Switch branches/restore files
- Safe
- No change to history

### What is git cherry-pick?

`git cherry-pick` applies a specific commit from one branch to another without merging the entire branch.

```bash
git cherry-pick commit-hash
```

### What is git tag?

Tags mark specific points in Git history, typically for releases:

```bash
git tag v1.0.0                # Lightweight tag
git tag -a v1.0.0 -m "Release 1.0"  # Annotated tag
```

### Lightweight vs annotated tag

**Lightweight:**
- Just a pointer to commit
- No additional metadata
- Simple reference

**Annotated:**
- Full object with tagger info
- Includes date and message
- Recommended for releases

### What is git blame?

`git blame` shows who last modified each line of a file and when. Useful for understanding code history and finding who to ask about specific changes.

### What is git bisect?

`git bisect` helps find the commit that introduced a bug using binary search through commit history.

### What is submodule?

Submodule allows you to include one Git repository as subdirectory of another. Useful for including libraries or shared code.

### What is monorepo?

Monorepo is a single repository containing multiple projects or services. Benefits include shared tooling and easier cross-project changes.

### What is CI/CD?

- **CI (Continuous Integration)**: Automatically build and test code changes
- **CD (Continuous Deployment)**: Automatically deploy tested changes
- Ensures code quality and faster releases

### How GitHub integrates with CI/CD?

- **GitHub Actions**: Built-in CI/CD platform
- **Webhooks**: Trigger external CI/CD systems
- **Status checks**: Show build results on PRs
- **Protected branches**: Require passing tests before merge

### What is GitHub Actions?

GitHub Actions is a CI/CD platform that automates workflows:
- Run tests on every commit
- Deploy applications
- Automate repetitive tasks
- Custom workflows with YAML files

### When NOT to use GitHub Actions?

- **Complex enterprise workflows**: May need specialized tools
- **Heavy computational tasks**: Limited compute resources
- **Proprietary CI/CD systems**: When already invested in other tools
- **Specific compliance requirements**: May need certified platforms

## 7️⃣ Security & Best Practices (Good Impression)

### Why should we not commit secrets?

- **Security risk**: Exposed to anyone with repository access
- **Version history**: Secrets remain in Git history even if removed
- **Public repositories**: Secrets visible to entire internet
- **Automated scanning**: Bots scan for exposed credentials

### How to remove sensitive data from Git history?

```bash
# Remove file from all history
git filter-branch --force --index-filter \
'git rm --cached --ignore-unmatch secrets.txt' \
--prune-empty --tag-name-filter cat -- --all

# Or use BFG Repo-Cleaner (easier)
bfg --delete-files secrets.txt
```

### What is SSH vs HTTPS authentication?

**SSH:**
- Uses SSH keys
- More secure
- No password prompts
- Port 22

**HTTPS:**
- Uses username/password or token
- Easier to set up
- May require credentials
- Port 443 (firewall friendly)

### How do you protect main branch?

- **Branch protection rules**: Require PR reviews
- **Status checks**: Require passing tests
- **Restrict pushes**: Only allow through PRs
- **Require signed commits**: Ensure authenticity
- **Dismiss stale reviews**: Re-review after changes

### What is code ownership?

Code ownership assigns responsibility for specific files or directories to individuals or teams. Implemented through CODEOWNERS file.

### What are protected branches?

Protected branches have rules that:
- Prevent force pushes
- Require pull request reviews
- Require status checks to pass
- Restrict who can push directly

### Why should commits be small?

- **Easier review**: Reviewers can understand changes better
- **Easier debugging**: Isolate problems to specific changes
- **Easier rollback**: Revert specific features without affecting others
- **Better history**: Clear progression of changes

### What is semantic commit message?

Semantic commits follow a standard format:

```
type(scope): description

feat(auth): add login functionality
fix(api): resolve null pointer exception
docs(readme): update installation instructions
```

## 8️⃣ Resume-Linked Questions (They WILL ask if applicable)

### How many projects on your GitHub?

*Be honest about your project count and be ready to discuss 2-3 projects in detail.*

### Which project are you most proud of?

*Choose a project that demonstrates your skills and be ready to explain:*
- What problem it solves
- Technologies used
- Challenges faced
- Your specific contributions

### How many commits did you make?

*Know your approximate commit count and explain your commit frequency and style.*

### What was your role in team repo?

*Explain your responsibilities:*
- Code contributions
- Code reviews
- Issue management
- Documentation

### How do you manage issues?

*Describe your process:*
- Creating clear issue descriptions
- Using labels and milestones
- Linking PRs to issues
- Following up on bug reports

### How did Git help in your project?

*Explain specific benefits:*
- Version control for rollbacks
- Branching for feature development
- Collaboration with team members
- Code review process

### Have you faced merge conflict? Explain.

*Describe a real scenario:*
- What caused the conflict
- How you identified it
- Steps to resolve it
- How you prevented future conflicts

### Explain your Git workflow step-by-step.

```
1. git pull origin main          # Update local main
2. git checkout -b feature-name  # Create feature branch
3. # Make changes
4. git add .                     # Stage changes
5. git commit -m "message"       # Commit changes
6. git push origin feature-name  # Push to remote
7. # Create pull request on GitHub
8. # Code review and merge
9. git checkout main             # Switch back to main
10. git pull origin main         # Update local main
11. git branch -d feature-name   # Delete feature branch
```

### Show your GitHub profile (sometimes)

*Be ready to:*
- Navigate your GitHub profile
- Explain your pinned repositories
- Discuss your contribution graph
- Show code examples

## 9️⃣ Rapid-Fire / Trick Questions

### Can we use Git without GitHub?

Yes! Git is a standalone version control system. GitHub is just one hosting service. You can use Git locally or with other services like GitLab, Bitbucket.

### Is GitHub mandatory for Git?

No, GitHub is optional. Git works independently. GitHub provides additional collaboration features but isn't required for version control.

### What happens if internet goes down?

Git works offline! You can:
- Make commits locally
- Switch branches
- View history
- Only push/pull require internet

### Can two people commit at same time?

Yes, but only one can push first. The second person must pull and resolve any conflicts before pushing.

### Can we undo a commit?

Yes, multiple ways:
- `git reset` (rewrites history)
- `git revert` (creates new commit)
- `git commit --amend` (modify last commit)

### Can Git track binary files?

Yes, but not efficiently. Git stores entire binary files for each change, making repository large. Better to use Git LFS for large binaries.

### Why is Git fast?

- **Local operations**: Most operations don't need network
- **Efficient storage**: Uses compression and delta compression
- **Smart algorithms**: Optimized for common operations
- **Distributed**: No single point of failure

### Difference between fork and clone

**Fork:**
- Creates copy on GitHub
- Your own repository
- Can create PR to original
- GitHub feature

**Clone:**
- Creates copy on local machine
- Local working copy
- Direct connection to original
- Git command

## 🔥 MUST-PREPARE SHORT ANSWERS (Prime level)

### Git vs GitHub

**Git:**
- Version control system (software)
- Works locally
- Command-line tool

**GitHub:**
- Cloud hosting service for Git repositories
- Web-based platform
- Additional collaboration features

### Branch vs fork

**Branch:**
- Different line of development within same repository
- Same repository, different timeline
- Used for features/experiments

**Fork:**
- Personal copy of entire repository on your account
- Separate repository
- Used for contributing to others' projects

### Pull vs fetch

**Pull:**
- Downloads and merges changes
- `fetch + merge` combined
- Updates working directory

**Fetch:**
- Only downloads changes
- Doesn't merge
- Safe operation

### Merge conflict handling

1. Identify conflicted files
2. Open and manually resolve conflicts
3. Remove conflict markers
4. Stage resolved files
5. Complete merge with commit

### reset vs revert

**Reset:**
- Moves branch pointer backward
- Rewrites history
- Dangerous for shared repos

**Revert:**
- Creates new commit that undoes changes
- Preserves history
- Safe for shared repos

### PR workflow

1. Create feature branch
2. Make changes and commit
3. Push to remote
4. Create pull request
5. Code review
6. Merge after approval

### .gitignore

File that tells Git which files to ignore:
- Secrets and credentials
- Build artifacts
- OS-specific files
- Dependencies

### How your project uses GitHub

*Customize based on your actual project:*
- Version control for source code
- Issue tracking for bugs
- Pull requests for code review
- GitHub Actions for CI/CD
- Documentation with README
- Collaboration with team members

---

**Total Questions Covered: 100+**

This comprehensive guide covers all GitHub/Git questions with proper formatting for easy reading! 🎯