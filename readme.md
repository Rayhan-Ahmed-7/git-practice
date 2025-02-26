# Git Commands Cheat Sheet 📜

## Configuration ⚙️

### Set Global User Information
```bash
git config --global user.name "Rayhan Ahmed"
git config --global user.email "dev.rayhan7@gmail.com"
```
- **Description:** Configures your Git username and email for all repositories on your machine. This information is included in each commit message.

### Set Local User Information for a Specific Project
```bash
git config user.name "Rayhan Ahmed"
git config user.email "dev.rayhan7@gmail.com"
```
- **Description:** Configures your Git username and email for the current repository only, overriding the global settings. This allows different identities for different projects.

## Tracking Changes 📈

### Check Status
```bash
git status
```
- **Description:** Displays the state of the working directory and staging area, including untracked files. 

### Stage Changes
```bash
git add QnA.txt
git add --all
git add .
```
- **Description:** Prepares changes for the next commit. 
  - `git add QnA.txt`: Stages a specific file for the next commit.
  - `git add --all`: Stages all changes in the working directory (tracked and untracked).
  - `git add .`: Stages all changes in the current directory.

### Commit Changes
```bash
git commit -m ":zap: contact numbers added"
```
- **Description:** Records the staged changes in the repository with a descriptive message. Each commit serves as a snapshot of your project at a point in time.

## Undo Changes ❌

### Restore Files
```bash
git restore friend-list.txt
git restore <directory>
git restore .
```
- **Description:** Restores modified files back to their last committed state.
  - `git restore friend-list.txt`: Restores a specific file to its last committed state.
  - `git restore <directory>`: Restores all files in a specific directory to their last committed state.
  - `git restore .`: Restores all changes in the current directory to their last committed state, undoing local unstaged and uncommitted changes.

### Undo Staged Changes
```bash
git restore --staged .
```
- **Description:** Unstages files that have been added to the staging area, keeping the changes in the working directory.

## Commit History 📜

### View Commit History
```bash
git log
```
- **Description:** Displays the commit history for the repository. Press `q` to exit or use the up/down arrow keys to scroll.

### Compact Commit History
```bash
git log --oneline
```
- **Description:** Shows a more compact version of the commit history, displaying each commit on one line for a quicker overview.

### Checkout a Specific Commit
```bash
git checkout e0ac7bd
```
- **Description:** Switches to a specific commit, making the repository reflect its state at that commit. Commits are essentially branches with unique names.

## Branching 🌱

### Create and Manage Branches
```bash
git branch table-version
git branch
git checkout table-version
git checkout -b table-version-new
git branch -D table-version-new
```
- **Description:** Manages branches in the repository.
  - `git branch table-version`: Creates a new branch named `table-version`.
  - `git branch`: Lists all branches in the repository.
  - `git checkout table-version`: Switches to the `table-version` branch.
  - `git checkout -b table-version-new`: Creates and switches to a new branch `table-version-new` in a single command.
  - `git branch -D table-version-new`: Deletes the branch `table-version-new`, even if it has unmerged changes.

### Merge Branches
```bash
git merge table-version
```
- **Description:** Merges the specified branch (`table-version`) into the current branch, integrating changes from both branches.

## Differences Between Commits 🔍
```bash
git diff cc3b2eb e0ac7bd
```
- **Description:** Shows the differences between two commits (`cc3b2eb` and `e0ac7bd`). The difference will be shown from the perspective of the right commit since it's the last parameter. Any additions or deletions will be highlighted accordingly.

## SSH Keys 🔑

### Check SSH Keys
```bash
ls -al ~/.ssh
```
- **Description:** Lists SSH keys in the `.ssh` directory.

### Generate SSH Key
```bash
ssh-keygen -t rsa -b 4096 -C "dev.rayhan7@gmail.com"
```
- **Description:** Creates a new SSH key pair (public and private key) for secure access to repositories.

### Start SSH Agent and Add Key
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_rsa
```
- **Description:** 
  - `eval "$(ssh-agent -s)"`: Starts the SSH agent in the background, allowing it to manage your SSH keys.
  - `ssh-add ~/.ssh/id_rsa`: Adds the specified private SSH key to the agent for authentication when connecting to remote repositories.

### Copy Public Key to Clipboard
```bash
cat ~/.ssh/id_rsa.pub | clip
```
- **Description:** Copies the public SSH key to the clipboard, which can then be added to your GitHub account for SSH access.

### Add SSH Key to GitHub
- **Steps:**
  1. Go to GitHub settings.
  2. Navigate to **SSH and GPG keys**.
  3. Click **New SSH key** and add the copied SSH key.
  4. On the first push, it will ask for confirmation; type `yes` to continue.

### Pull Changes
```bash
git pull origin main
```
- **Description:** Fetches changes from the remote `main` branch and merges them into your current branch.

### Create a Branch for Location Version
```bash
git checkout -b location-version
```
- **Description:** Creates and switches to a new branch named `location-version`.

### Forking Repositories
- **Description:** Forking is essentially cloning a repository into your GitHub account. Instead of cloning locally, it creates a copy on your GitHub account.

## Working with Multiple GitHub Accounts
- **Note:** One SSH key can be used for only one account. To connect to another GitHub account, you need to create a new SSH key pair.

### Generate a New SSH Key for a Different Account
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
```
- **Description:** Generates a new SSH key pair with a different email.

### Save the New Key with a New Name
- **Prompt:** When prompted, save it with a new name, e.g., `id_github_personal`.

### Start SSH Agent and Add New Key
```bash
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_github_personal
```
- **Description:** Starts the SSH agent and adds the new private key for authentication.

### Add the New Public Key to GitHub
- **Steps:** Similar to previous steps for adding SSH keys.

### Make a Pull Request
- **Description:** After forking and making changes, you can create a pull request to suggest your changes to the original repository. Wait for the owner to merge.

## Stashing Changes 🗂️

### Stash Commands
```bash
git stash
git stash -u
git stash list
git stash pop
git stash apply
git stash drop stash@{1}
git stash clear
```
- **Description:** Temporarily saves changes in the working directory that are not ready to be committed.
  - `git stash`: Stashes all changes (tracked files) in your working directory.
  - `git stash -u`: Stashes changes including untracked files.
  - `git stash list`: Lists all stashed changes.
  - `git stash pop`: Restores the most recent stash and removes it from the stash list.
  - `git stash apply`: Restores the most recent stash without removing it from the stash list.
  - `git stash drop stash@{1}`: Removes a specific stash from the stash list.
  - `git stash clear`: Removes all stashed changes.

## Resetting Commits ⏪

### Different Reset Types
```bash
git reset --soft HEAD~1
```
- **Description:** Moves HEAD to the specified commit but keeps changes staged. Useful when you want to undo commits but keep staged changes.

```bash
git reset --mixed HEAD~1
```
- **Description:** Moves HEAD to the specified commit and unstages changes but keeps them in the working directory. Useful for undoing commits without losing changes.

```bash
git reset --hard HEAD~1
```
- **Description:** Moves HEAD to the specified commit and discards all changes (both staged and unstaged). This is a destructive operation and cannot be undone easily.

### Unstage a Specific File
```bash
git reset HEAD git.md
```
- **Description:** Unstages a specific file without discarding changes.

### Reset to Original Head
```bash
git reset --hard ORIG_HEAD
```
- **Description:** Resets to the original HEAD. 
  - **Note:** If another operation updates `ORIG_HEAD`, this may not work as expected. Use `git reflog` to view history and manually reset to a previous commit if needed.

### Reset After a Specific Commit
```bash
git reset <commit-id>
```
- **Description:** Changes after the specified commit will become uncommitted.

```bash
git reset --hard <commit-id>
```
- **Description:** If you don't want the changes after that commit, use `--hard`.

### Caution with Pushed Commits
- **Note:** If you have already pushed a commit to a remote repository, resetting that commit is not recommended. In such cases, `git revert` is more useful.

## Reverting Changes 🔄

### Revert a Commit
```bash
git revert <commit-id>
```
- **Description:** Undoes a commit or removes the code of a commit by creating a new commit that reverses the changes made by a previous commit. This preserves history by adding a new commit instead of removing previous ones.

## Rebasing and Squashing 🧹

### Rebase with Main
```bash
git rebase main
```
- **Description:** Maintains a cleaner git history by applying the commits from the current branch on top of the latest commits in the `main` branch. This does not affect your git log history.

### Merge with Squash
```bash
git merge new-feature --squash
```
- **Description:** When merging a branch, the `--squash` flag combines all changes into a single commit, maintaining a cleaner git log history. This is useful when you have multiple commits for a feature that you want to merge as one.

## Interactive Reset ✂️
```bash
git reset -p <commit-id>
```
- **Description:** Allows you to unstage parts of a commit interactively. It does not delete commits or modify history; the unstaged changes remain in the working directory unless discarded.

# Git Scenarios Cheat Sheet 📜

## Git Commands for Common Scenarios

| **Scenario**                                                      | **Command**                   | **Description**                                                                                  |
|-------------------------------------------------------------------|-------------------------------|--------------------------------------------------------------------------------------------------|
| You committed something but want to unstage some parts            | `git reset -p`               | Interactively unstage specific changes from the most recent commit.                            |
| You want to reuse changes from an old commit but not create a new commit yet | `git cherry-pick -n <commit>` | Applies changes from the specified commit to your working directory without committing them.     |
| You want to apply changes from an old commit and create a new commit automatically | `git cherry-pick <commit>`    | Applies changes from the specified commit and creates a new commit in your current branch.       |
