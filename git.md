git config --global user.name "Rayhan Ahmed"
git config --global user.email “dev.rayhan7@gmail.com”

for different user different project
git config user.name "Rayhan Ahmed"
git config user.email “dev.rayhan7@gmail.com”

git status
to track untracked files
git add QnA.txt
git add --all
git add .
git commit -m ":zap: contact numbers added"
now a commit will create a new version
git restore friend-list.txt
git restore <directory>
git restore . for local unstaged & uncommitted change to undo local unstaged & uncommitted change
git restore --staged . to undo local staged change
git log to see commit history to exit press q or to see more press up down
git log --oneline to see more compact
git checkout e0ac7bd commits are basically branch which is a unique name 
git branch table-version
git branch
git checkout table-version
git checkout -b table-version-new
git branch -D table-version-new
git merge table-version
git diff cc3b2eb e0ac7bd to see difference between commits the difference will be shown from second commit side wise. wanted to see the difference between the left commit with right commit the difference will be show from the right commit side since it's the last parameter any addition or deletion will be shown from it's perspective
ls -al ~/.ssh too see ssh
ssh-keygen -t rsa -b 4096 -C "dev.rayhan7@gmail.com"
eval "$(ssh-agent -s)” to run the ssh agent in background
ssh-add ~/.ssh/id_rsa to add the private key in ssh agent
cat ~/.ssh/id_rsa.pub | clip copy the public key
then goto github settings then go to SSH and GPG keys then click the New SSH key and add the copied ssh key then on first push it will ask for confirmation type yes to continue
git pull origin main
git checkout -b location-version
fork is basically clone instead of cloning locally it clones the project on you github
one ssh key can be only used to one account now if you wan't connect to another github account you have to create brand new ssh key pairs
for example 
ssh-keygen -t ed25519 -C "your_email@example.com"
When prompted, save it with a new name, e.g., id_github_personal
then do these
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/id_github_personal
then add the pub key to your github account
do fork add something make pull request wait for owner to merge

git stash
git stash -u
git stash list
git stash pop
git stash pop stash@{1}
git stash apply
git stash apply stash@{1}
git stash drop stash@{1}
git stash clear

git reset --soft HEAD~1
👉 Moves HEAD to <commit> but keeps changes staged.

Useful when you want to undo commits but keep staged changes.
The changes remain in the index, so you can recommit them.
git reset --mixed HEAD~1
👉 Moves HEAD to <commit> and unstages changes but keeps them in the working directory.

Useful when you want to undo commits and unstage changes without deleting them.
The unstaged changes are still available in the working directory.
git reset --hard HEAD~1
👉 Moves HEAD to <commit> and discards all changes (both staged and unstaged).

This is a destructive operation and cannot be undone easily.
Useful when you want to completely discard changes.

git reset HEAD git.md
Used to unstage a specific file without discarding changes.

git reset --hard ORIG_HEAD
### **When Will `ORIG_HEAD` Not Work?**
❌ **If another operation updates ORIG_HEAD** (e.g., another reset, merge, or rebase), then `ORIG_HEAD` will change, and you might not be able to undo your reset.

✅ **Safer Alternative?**
Use:
```sh
git reflog
```
This shows a history of HEAD movements, and you can manually reset to a previous commit:
```sh
git reset --hard <commit-id-from-reflog>
```
git reset <commit-id> changes after that commit will become uncommitted
git reset --hard <commit-id> if you don't want the changes after that commit use --hard

note if you have already pushed a commit on remote repository resetting that commit is not recommended on such case git revert is more useful
get revert <commit-id>
git revert is used to undo a commit or remove the code of a commit by creating a new commit that reverses the changes made by a previous commit. Unlike git reset, which moves HEAD and can remove commits, git revert preserves history by adding a new commit.

git rebase main rebase is used to maintain a cleaner git history if you want the latest changes in your branch from main do this this won't effect your git log history
* first git will check what's the last commit that match with my branch with main then it will put aside our branch commit's and start to add all the new commit of the main branch then it will apply the out branch commits on top of it serially

git merge new-feature --squash 
when to use squash ? lets say we need to add simple feature to out main project we have created a branch new feature and we made some changes add a lot of commit's during development now development is done. and we want to merge out branch to main but we want to maintain a cleaner git log history we don't want these lot of commits to get added on out main branch to do that we can add --squash flag while merging by doing that all the changes of new feature branch will come to main in staged state now you can make a single commit for all that change.

git reset -p 54b60ba allows you to unstage parts of that commit interactively.
It does NOT delete commits or modify history.
The unstaged changes remain in the working directory unless discarded.

Scenario	Use This
You committed something but want to unstage some parts	git reset -p
You want to reuse changes from an old commit but not create a new commit yet	git cherry-pick -n
You want to apply changes from an old commit and create a new commit automatically	git cherry-pick <commit>