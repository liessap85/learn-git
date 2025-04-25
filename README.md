
## QUICKSTART: Process when making a new repo

1. **Initialise repo**
 `git init`


2. **Global configuration & setup**
`git config --global user.name "<NAME>"`
`git config --global user.email "<EMAIL>"`
`git config --global core.editor "<EDITOR_NAME>"`


3. *Create repo in GitHub with NO gitignore & no README. Zero files, or the push will hate you*


4. *Check whether remote is already active and set up*
`git remote -v`


5. *Add remote repo 
`git remote add <NAME> <URL>`  
*name is usually origin

*Pull down collaborator's work AND integrate it into working area - If using existing repo*
`git pull <NAME> <BRANCH>`
`git pull origin main`


6. **View branches available**
`git branch`

**Create new branch***
	`git branch <BRANCH_NAME>`
	
	
**Switch to different branch**
	`git checkout <BRANCH_NAME>`
	*best practice is to commit before switching*


7. **Add files to staging area - *don't add all***
`git add <FILENAME>`


8. **Store files in repo from Staging area**
`git commit -m "YOUR MESSAGE HERE"`
*If you don't add a message a nano editor should open to ask for a message*

*git messages should be **present tense and imperative**, giving an order to your repo - "Add file to repo", or "Test new feature"*


9. *Set upstream and push code, so that you can easily just run git push without naming*
`git push -u origin main`


#  Learning from course

## Useful Links
**git docs**
https://git-scm.com/docs


## Setup
 **Initialise repo**
 `git init`
 

**Check file and repo status**
`git status`


**Global configuration & setup**
`git config --global user.name "<NAME>"`
`git config --global user.email "<EMAIL>"`
`git config --global core.editor "<EDITOR_NAME>"`

VS CODE SPECIFIC COMMAND, do not run previous one...
*If changing your editor to VS code you may need to click CMD+SHFT+P then type in `code` to make sure the command get stored to PATH*
`git config --global core.editor "code --wait"`

*If you want to view your config file easily, co to your HOME folder and run 
`cat .gitconfig` 
you can edit this file using nano as well if you want.*

*To see the repo specific config*
`git config --list`


**Ensure you have a .gitignore, and track it too**
*There are gitgnore generators online that give you a template for the language you are using and the files that should normally be ignored.*
https://www.toptal.com/developers/gitignore
https://mrkandreev.name/snippets/gitignore-generator/



## File Management
**Add files to staging area - *don't add all***
`git add <FILENAME>`


**Remove files from staging area - *but not fully deleting***
`git rm --cached <FILENAME>
`

**Store files in repo from Staging area**
`git commit -m "YOUR MESSAGE HERE"`
*If you don't add a message a nano editor should open to ask for a message*

*git messages should be **present tense and imperative**, giving an order to your repo - "Add file to repo", or "Test new feature"*


**View log file of commits**
`git log` #or `git log --oneline`


**Compare a file from previous state to now**
*Run this after running **git add** but before **git commit***
`git diff --staged`

*To compare previous commit to now*
`git diff <COMMIT_ID> <COMMIT_ID>`

*To compare different branches*
`git diff <BRANCH_NAME> <BRANCH_NAME>`

*NB if space between names or ids does not work, put two dots instead*
`git diff <NAME>..<NAME>`


**Restore to previous commit**
`git restore <FILENAME>`


**Look at 2 commits prior or specific commit**
`git checkout HEAD ~2`
`git checkout <COMMIT_HASH>`

*Back to latest commit*
`git checkout <BRANCH_NAME>`
`git reflog`




## Branches
**View branches available**
`git branch`


**Create new branch***
`git branch <BRANCH_NAME>`


**Switch to different branch**
`git checkout <BRANCH_NAME>`
*best practice is to commit before switching*


**Combine commands (create and switch)**
`git checkout -b <BRANCH_NAME>`


**Merging branches**
*Switch to **main** first*
`git merge <BRANCH_NAME> -m "<MERGE_MESSAGE>"`

*If there are code conflicts you will need to sort this and then run the following command to finalise it*
`git commit -m "fixed conflicts"`


**Delete a branch**
`git branch -d <BRANCH_NAME>`


**Move from one branch to another without committing**
*A stash is like a temporary storage location for your unadded changes*
`git stash`

*When you get back to the stashed branch, run*
`git stash pop`

*Stashes can be applies from other branches, but check what the stash id is first*
`git stash list`
`git stash apply stash:{<ID_NO>}`




## Rebase
*Do not ever run this on main!*
`git rebase main`
*This will homogenise the branch commits and join them all to one branch history. Any future commits will once again diverge.*

*If you have conflicting files, accept the changes that you want, and then...*
`git add <FILENAME>`
`git rebase --continue`

OR

`git rebase --abort`




## GitHub
### Set Up 
**Set up SSH Keys**
*In your terminal*
`ssh-keygen -t ed25519 -C "<YOUR-GITHUB-EMAIL-ADDRESS>`

*Might need to come up with a new name, in Windows the format is:*
`/c/Users/hanna/.ssh/<KEY-NAME>`

*On windows do this on Admin Powershell first*
```powershell
Get-Service -Name ssh-agent | Set-Service -StartupType Manual
Start-Service ssh-agent
```
*In terminal*
`ssh-add /c/Users/hanna/.ssh/<KEY-NAME>`

*Copy value to add to GitHub*
`cat /c/Users/hanna/.ssh/<KEY-NAME>.pub`

*Paste into the New SSH Key section on GitHub under settings - ssh & GPG keys*

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/generating-a-new-ssh-key-and-adding-it-to-the-ssh-agent

https://docs.github.com/en/authentication/connecting-to-github-with-ssh/adding-a-new-ssh-key-to-your-github-account




### Remote
*Create repo in GitHub with NO gitignore & no README. Zero files, or the push will hate you*

*Check whether remote is already active and set up*
`git remote -v`

*Add remote repo 
`git remote add <NAME> <URL>`  
*name is usually origin*

*To change name*
`git remote <OLDNAME> <NEWNAME>`

*To remove remote repo*
`git remote remove <NAME>`




### Pushing and Working
*Set upstream and push code, so that you can easily just run git push without naming*
`git push -u origin main`




### Cloning, Fetching & Pulling
*Download a full codebase from a repo - probably one you don't own*
`git clone <URL>`

*Pull down collaborator's work from remote without integrating it*
`git fetch <NAME> <BRANCH>`

*Pull down collaborator's work AND integrate it into working area*
`git pull <NAME> <BRANCH>`
`git pull origin main`
