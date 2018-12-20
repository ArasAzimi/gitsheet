#### SSH Keys:
* A nice guide on Setting up SSH on various platforms can be found [here](https://confluence.atlassian.com/bitbucket/set-up-an-ssh-key-728138079.html#SetupanSSHkey-ssh3).  
> If you get: "Could not open a connection to your authentication agent" try:  
> `eval ssh-agent -s`  
NOTE: On windows use `eval $(ssh-agent -s)` instead  
> `ssh-add path_to_ssh_key` only if you have multiple ones otherwise leave empty to use default location and id "~/.ssh/id_rsa"

#### Inspecting a repo:
* [The Git repository browser](https://git-scm.com/docs/gitk)
>`gitk` or `gitk --all` to see all refs

>`gitk path_to_a_specific_filname`to see the tree for the filename or directory

* Git logs
> show all logs:`git log` - not recommonded  
> Show a number of logs: `git log -3` (3 latest commit messages)  
> Pretty oneline logs: `git log --pretty=oneline`  

* Showing where git configurations are
> `git config --list --global` or  
> `git config --global -e`  This will get a text editor loaded with your global .gitconfig file. From here you can also see where the config file is located.  


#### [Cleaning](https://git-scm.com/docs/git-clean)
* To clean a repo from untracked file
> `git clean -f -dx`  

#### [Stashing](https://git-scm.com/book/en/v1/Git-Tools-Stashing)

* Stash without specifying a stash-name
> `git stash`

* See your stash list:
> `git stash list`

* Apply latest stash
> `git stash apply`

* Apply a specific stash- first see your stash list to know the stash ID/number(i.e., 2 in the bellow example):
> `git stash apply stash@{2}`

* Above does not restage files, if you want to restage files as well use:
> `git stash apply stash@{2} --index`

* To name a stash for easy future refrence
> `git stash save "my_stash_name"`

#### [Branches](https://git-scm.com/docs/git-branch)
* Switch to branch "branch_name"
> `git checkout branch_name`

* Get branch names
> `git branch -a`

* Create new branch. This branch will be off the current branch!
> `git checkout -b branch_name`

* Push your branch to the remote repository
> `git push -u origin branch_name`

* Add (stage) and commit with one single command with commit message
> `git commit -am "Your commit message"`

#### [Merging](https://git-scm.com/docs/git-merge)
* Merge branch 'branch_name' to 'dev'
> `git checkout dev`  
> `git pull origin dev`  
> `git merge branch_name`  
> `git push origin dev`  

* Showing branch trees more decorativly!
> `git log --all --graph --decorate --oneline --simplify-by-decoration` or  
> `git show-branch --all` or  
> `git log --all --graph --decorate --oneline` or  
> `git log --all --color --graph --pretty=format:'%Cred%h%Creset -%C(yellow)%d%Creset %s %Cgreen(%cr) %C(bold blue)<%an>%Creset' --abbrev-commit`

#### Git tags: [[Git docs](https://git-scm.com/docs/git-tag)] and [[Git book](https://git-scm.com/book/en/v2/Git-Basics-Tagging)]
	-- Annotated Tag
	-- Lightwave tag

* Annotated tag- on the current branch:
> Check existing tag; `git tag`  
> Create annotated tag: `git tag -a tag_name -m "Your tag message"`  
> Check that the new tag is created uaing `git tag`  
* Lightwave tag- on the current branch:
> Check existing tag; `git tag`  
> Create lightwave tag: `git tag -a tag_name -lw`  
> Check that the new tag is created uaing `git tag`  

* Rename a tag- on the current branch:
> `git tag new_tag_name old_tag_name`

* Push tags to remote:
> `git push origin tag_name`  

* Pull a specific tag:
> `git clone repo_link tag_name`  

* Tag a specific commit:
> see the commits: `git log --pretty=oneline`  
> `git tag -a tag_name -m "tag message" commit_id` (first 7 characters of the commit ID)  

* Delete tags
> `git push --delete origin tagname` to remove tag from remote repo  
> `git tag --delete tagname` to remove tag locally OR git tag -d tagname  

#### Amend a commit: Modifying an already committed change
> `git commit --amend` in the opened window modify the commit message and save  
> Push the amended commit to emote: `git push --force origin branch_name`  
> To amend last commit without modifying the commit message: `git commit --amend --no-edit`  

#### rebasing:
> To rebase to the last commit `git rebase -i HEAD~1`
> Once the editor opened, delete the line starting with "pick" and save exit i.e., `:wq`. This line should also show the commit message.
> Verify the local rebase by `git log -2` Last commit should be gone
> Push the changes to remote by `git push origin branch-name --force`. It is assumed that the right permissions for the branch exists for the user.

#### Syncing fork
* To sync a fork with the remote use this [link](https://help.github.com/articles/syncing-a-fork/) from github help

#### My favorite aliases
> To use these aliases, add them to the .gitconfig file and to use them simply do `git alias_key` i.e., `git st` for `git status`

[alias]  
&emsp; st = status  
&emsp; co = checkout  
&emsp; br = branch  
&emsp; ci = commit  
&emsp; unstage = 'reset HEAD --'  
&emsp; visual = !gitk  

&emsp; lp1= "log --pretty=oneline"  
&emsp; lp2= "log --oneline --graph --color --all --decorate"
