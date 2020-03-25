### Background
This repo acts as notes for git functions, and should be suitable for Linux beginners with no git command line experience. I suck at this, so take these as practices.

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

##### - Create branch

##### - Merge branch

##### - Revert changes


#### GitLab
##### - Create ssh key
ref to https://docs.gitlab.com/ee/ssh/, 
1. Open terminal and command `ssh-keygen -t ed25519 -C "yui.leung.15@ucl.ac.uk"`. Enter if there is no ssh key pair already. Double-enter to skip setting password. 
2. Copy public ssh key `xclip -sel clip < ~/.ssh/id_ed25519.pub`.
3. Go to GitLab account and find **Settings**. 
4. Navigate to **SSH Keys** at the left. Enter the key from the clipboard. 
5. Press **Add Key**.
6. To test the set-up, command `ssh -T git@gitlab.com`.
