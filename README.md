# Learning Git 
#### references Hitesh choudhary youtube channel

## Learining path 
* get the basics 
* use it daily 
* face the problem 
* solve the problem 

# Terminologies 

* Repo 
* git --version 
* git status
* git init 
* ls --- is for show list of folders 
* ls -la  --> is shows all hidden folders

### Commit 
* this is a check point
* write-->Add--->commit 
### staging area is tells that i am ready to commit

### flow 
* first **initialize the git** in the folder `git init`
* if any changes made you have to **add those chaged files to staging area** `git add .` or `git add fileOne.txt fileTwo.txt` or `git add -A`
* once you add those files to git then git keep track of those files 
* that added files are goes into the staging area. that **staging area tells I am ready to commit** `git commit -m "first commit" `
* `git status` for knowing our git status
* now we have to **commit** those changed files into **local repository**
* if we want to see those files we have **push** that into remote repository that is **github**

### Commit messages like orders to git 
* keep commits centric to one feature, one component or on fix. focused on one thing 
* present or past commit messages 
* dependes present tense, imperative 
* give **order to code base** 
* don't care

## Git configurations 
* `git config --global user.name "durga bhavani"`
* `git config --global user.email "durga@gmail.com"`

### setting code editor 
* this setting is for when you give the command like this `git commit` without commit message it will opens the **VIM** like cmd. so now setting this when enter that command, open the **code editor** 

`git config --global code.editor "code --wait"`

## commit behind the scene 

* First commit : first commit is independent
  - Hash 
  - parent - null 
  - Info 

* second commit : seconde commit is combination of previous and present
  - Hash 
  - parent 
  - Info 

 ## Branches 
* `git branch` for knowing our current branch 
* `git branch nav-bar`  give branch name related to our task
* `git checkout nav-bar` or `git switch nav-bar` this will move to the nav-bar branch 
* `git switch -c nav-bar` or `git checkout -b nav-bar` this will creates a new branch and move to that branch 

* commit before switching to another branch 
* go to .git folder and checkout HEAD file  

* `git log` or `git log --oneline` 

* `git merge nav-bar` this command merge nav-bar branch into current(master) branch

*  `git branch -d nav-bar` it will deletes the brach

* `git Diff` (informative command) shows the differences in onefile like differences of previous version and current version

* `git diff` (compare working with staging) 
### how to read diff 
--- symbols indicate that this is the previous version of the file
+++ this is the current version of the file with changes 

### to exit from the git vim press Q 

### all are same
* `git diff <id of the commit>307074f` 
`git diff <commitid> <commitid>`
`git diff branchOne branchTwo`
`git diff branchOne..branchTwo` 

## git stash 
* it create a repo, work and commit on main 
* switch to another branch and work 
* conflicting changes do not allow to switch branch without commits

* if you work on one branch and if you want to switch to another branch without add your changes to staging area git won't allow you to switch to another branch 
* if you want to move to anothe branch you have to add and commit your changes to staging area then only move to the new branch 
* so we can use **git stash** command this will saves your changes so you can move to new branch without adding the changes to staging area 

* `git stash pop` is used to come back from the stash. after that you can add chages to staging area and commit those

* `git stash list`
* `git stash apply stash@{3}`

### all commands are work in sameway
`git checkout nav-bar`
`git switch master`
`git checkout HEAD~2` look at 2 commit prior 
`git reflag` move to the privous branch
`git restore filename` get back to last commit version

`git commit -am "commit message"` adding and commiting at the same time

## Rebase 
`git rebase main` rebasing the my current branch with the **main** branch
* this command is not recommended to run in the main/master branch
* note: never rebase commits that you have shared pushed to github 
* Moving or combining a sequence of commits to a new base commit.changes introduced in the commits and reapplying them on top of another branch.
* it cleans the commit history 
* confilicts are resolved as they occure

* merge:Combines the histories of two branches, creating a new commit that ties them together. This can lead to a history with multiple branches and merge commits.

* Rebase: Reapplies the changes of one branch onto another, resulting in a linear history without merge commits.

* Rewriting History: Rebasing rewrites commit history. This can be problematic if the branch has already been pushed and shared with others, as it requires force-pushing and can disrupt collaboration.

* Non-Shared Branches: It's safe to rebase branches that haven’t been shared with others. For shared branches, prefer merging or communicate with your team before rebasing

* git is a software and github is a service to host git online 
* github is for collaboration, backup,open source 

* SSH (Secure Shell) 
* setup **SSH keys** to connect with github
* github uses SSH to allow you to push code password based code push is not allowed

* When you use the **-u** or **--set-upstream** option with **git push**, you are telling Git to link the local branch to the remote branch you are pushing to.allow you to run future command

* The **-M** option in **git branch -M** stands for "move" or "rename". 
*  It is used to rename a branch to a new name. The -M flag also has the ability to force the rename if a branch with the new name already exists, effectively overwriting the existing branch.

`git remote -v`
`git remote add name url`
`git remote rename oldname newname`
`git remote remove name` remove the setting repo

`git push <remote> <branch>`
`git push origin main` 
`git push <remote> localbranch:remote branch` 

`git push -u origin main`
`git pash` it push code directly to github

`git clone url_of_remote_remo` this clones the repo into your local system 

`git pull` is used to pull the updates from the remote repo 
`git pull` = `git fetch`+`git merge`
`git pull origin main` changes will be merged to main from the remote repo

`git fetch` get info but don't put in my work
`git pull` get info and add it in my work

## How Real time open-source projects works 

* if you want to add code to one persons repository 
* first you have to fork that repository from that persons github to your github
* second clone that project using url into your ide 
* third create new branch and checkout to new branch 
* then start writing code after completion of writing code 
* fourth push that code into your new branch means github newly created branch not in main/master branch 
* fifth you have to raise the pull request with detailed explanation to that person 

* sixth that person reviews your code if it is okay he merges your pull requests (changed code) into that main codebase 

### if you change the same file in both branches.
* while your merging you will get conflicts 
* after fixing conflicts you need to add those changes to staging area and then commit 
* once you commit. those changes will merges into that branch  

## git Revert HEAD 

* revert is the command we use when we want to take a previous commit and add it as a new commit, keeping the log intact.

`git revert HEAD` revert the latest commit. revert the latest change,  and then commit 
`git revert HEAD~2`  revert to the latest 2nd commit or going back 2more

## Reset 
* reset is the command we use when we want to move the repository back to a previous commit, discarding any changes made after that commit.

## Git amend 
`git commit --amend -m "Added lines to README.md"`
* commit --amend is used to modify the most recent commit.

* It combines changes in the staging environment with the latest commit, and creates a new commit.

* This new commit replaces the latest commit entirely.

#### How to work on a project with team 

* fork the repository into your github 
* clone that forked repo for working: `git clone url of ur forked repo`
* `cd repository-name`
* create newbranch for working: `git checkout -b newbranch`
* Make Your Changes
* `git add .`
* `git commit -m "Description of the changes you made"`
* `git push origin newbranch`
* go to your github and click on **compare&pull** then add note and **create pull request** 

#### if you work on the same project with team 
* once you fork the repo, you don't need to fork the project every time follow the below steps:

* `git remote add upstream url of your old forked repo`
* fetch the latest changes from original repo: `git fetch upstream`
* `git checkout master`
* `git merge upstream/master`
* `git push origin master` 

##### next repeate the steps:
* new branch creation , work on that branch, add,commit,push,raise pull request.