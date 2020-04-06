### Background
This repo acts as notes for git functions, and should be suitable for Linux beginners with no git command line experience.
 
Working in a dev team is not the same as working alone. During development stages, many changes are made by different developers, which may lead to conflicts between versions of the same project. To encounter this problem, developers use different version control softwares to keep track of the changes, including, git (will discuss here), p4v, etc. Typically, they create a repository (repo) and its main branch (master). Every developer in the same repo then copies master as branches to the local, and makes changes on the branches. To update master, they merge changes from different branches into master. The advantages of using version control software are, the developers can keep track of what changes others have made, see the difference between versions, revert the changes, etc. 

This repo describes how I practise using git. It describes, how to initialize your repo, connect your local to git server, make changes, edit branches, pull changes from branches, etc.

#### GitHub
##### - Initialize a repo and commit the first changes 
1. Create a repo in github. For example, test/
2. Create a folder in your desktop, and change to that directory in your terminal window.
3. Command `git init` to initialize the folder, this creates a .git/ folder.
4. Create whatever file in this folder. Then command `git add .` or `git add <dir>`. 
5. Command `git commit -m "First commit (or any commit message)"`.
6. Command `git remote add origin <repo URL.git>`, for example, my username is zcemycl and the repo name is test. The repo URL.git is 'https://github.com/zcemycl/test.git'.
7. `git remote -v`.
8. Command `git push origin master`. Enter your username (e.g. zcemyl) and password. \
a. If rejected, `git fetch`, `git rebase --continue` or `git rebase --abort`, `git pull --rebase origin master ` and `git push origin master`. **This is due to the fact that, your folder does not have README.md from repo, so it is the latest version of the repo, then you cannot push since not yet pull.**

##### - Remove the link from repo to the folder
1. Change directory to the target folder. 
2. Command `rm -rf .git*`.

##### - Pull changes
is used with a different goal in mind: to update your current HEAD branch with the latest changes from the remote server. This means that pull not only downloads new data; it also directly integrates it into your current working copy files. 
1. `git pull origin master`.

##### - Fetch changes
really only downloads new data from a remote repository - but it doesn't integrate any of this new data into your working files. Fetch is great for getting a fresh view on all the things that happened in a remote repository.
1. `git fetch origin`.

##### - Routine to commit new changes
1. Always rememeber to fetch and pull. `git fetch origin` and `git pull origin master`.
2. Change new existing files.
3. Git add changes `git add .`. 
4. Git commit message `git commit -m "messages"`. 
5. Git push changes `git push origin master`.

##### - Create branch
1. Make sure master is up-to-date by `git pull origin master`.
2. Create branch on your local machine. `git checkout -b [branch name]` e.g. 'leobranch1'
3. Push the branch on github. `git push origin [branch name]`

##### - List all branches
1. `git branch -a`

##### - Commit changes for branch
1. Change the files. 
2. Add changes `git add .`.
3. Commit changes `git commit -m "messages"`.
4. Push changes `git push origin leobranch1`.

##### - Delete remote in the local
1. Command `git remote -v` to show the remote list.
2. Remove the target remove via `git remote rm [remote name]`, for example `git remote rm origin`.

##### - Show git status
1. Command `git status` to show anything to commit and which branch git is on.

##### - Pull updates from master to branch
1. Command `git status` to make sure you're on the branch.
2. Command `git pull origin master` to pull updates.
3. Commands `git add . && git commit && git push origin leobranch1`. 

##### - Switch branch your local on
1. Command `git checkout master` or `git checkout leobranch`.
2. Command `git status` to check which branch you are on.

##### - Merge two branches
1. Command `git checkout [branch to merge]`. e.g. merge branch into master, `git checkout master`
2. Command `git merge [branch being merged]`. e.g. `git merge leobranch1`.
3. Command `git push origin master`. 


##### - Delete branch
1. Delete your branch in git via `git push -d origin [target branch]`, e.g. `git push -d origin leobranch1`.
2. Delete branch in your local. Make sure you are on another branch first, e.g. `git checkout master`. Then run `git branch -d leobranch1`.


##### - Read changes 
1. `git diff`

##### - Change git remote url (Use this to change repo name)
1. `git remote set-url origin https://github.com/zcemycl/learnGit.git`.

##### - Revert changes
1. Navigate to repo page. 
2. Press commits and copy the commit id.
3. Revert by `git revert [commit id]`.
4. Push changes by `git push origin [branch name]`.

##### - Resolve problems when stopping long `git add .`
Error: Another git process seems to be running in this repo.
1. `rm -f .git/index.lock`

##### - Pull request

##### - Code review


#### GitLab
##### - Create ssh key
ref to https://docs.gitlab.com/ee/ssh/, 
1. Open terminal and command `ssh-keygen -t ed25519 -C "yui.leung.15@ucl.ac.uk"`. Enter if there is no ssh key pair already. Double-enter to skip setting password. 
2. Copy public ssh key `xclip -sel clip < ~/.ssh/id_ed25519.pub`.
3. Go to GitLab account and find **Settings**. 
4. Navigate to **SSH Keys** at the left. Enter the key from the clipboard. 
5. Press **Add Key**.
6. To test the set-up, command `ssh -T git@gitlab.com`.
