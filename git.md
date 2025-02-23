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
git restore .
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