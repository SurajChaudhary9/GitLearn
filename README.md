# Git Commands
##### (Learning to push, pull, fetch... etc)
##### (And to resolve merge conflicts if any)


## Git commands to start from scrach (from empty repo in local system)
1. `git init`
	-	 Current working directory is intialized as empty Git repo
	-	 Default branch name of this local repo: `master`
	-	 `git branch` will display nothing since 1st commit is missing
2. `git status`
3. `git add <file>`
	-	Use this command if you want git to add these files to local repo
	-	`git add --all` adds all untracked files
	-	When added they move to staging area
		-	Basically stored temporarily in branch until committed
		-	`git rm --cached <file>` to undo `git add`
		-	`git rm -r --cached <files>` for multiple files
4.	`git stash` will delete all uncommitted changes made in branch
5.	`git commit -m "<commit message>"`
	-	Always give a commit msg. Never leave it empty
6. `git branch <branch name>`
	-	Creates new branch of name: `<branch name>`
7. `git branch -m <old branch name> <new branch name>`
	-	When you init git in local machine it creates `master` branch. But all the GitHub repos online create `main` as the default branch. So better to change the name of the master branch to main.
		-	Use `git branch -m master main` to change the branch name from master to main
	-	If it is your own repo then you have another option. You can set the default repo created by Github as `master` in settings.
8. `git checkout <branch name>`
	-	Switches from current branch to `<branch name>`
9.	`git remote add <variable name> <repo clone link>`
	-	Creates a variable `<variable name>` and stores the repo clone link
	-	This will be useful to push/pull/fetch...etc from online repo
10. `git pull --rebase <remote variable/ repo link> <branch main>`
	-	This is done when you online repo has a commit that the local doesn't have
	-	Use `git pull --rebase origin main` when pulling from online repo for first time and if you have already made commit(s) in local repo
	-	Rebase basically adds all the commits of the online main branch and repositions all aditional commits to start after the online main branch commits. This ensures that the local branch commits are in sync with the online branch
11.	`git push <variable name/ repo clone link> <branch name>`
	-	Will push committed changes of < branch name > to online repo
12.	`git push -u <variable name/ repo clone link> <branch name>`
	-	Use this if:
		-	this is your 1st push, and you have not made any clone, fetch, pull from this online repo prior to this


## Git cloning
### If you are cloning from online repo and do not wish to create your own local machine repo before that then the following applies:
1.	`git clone <repo clone link>`
	-	A new directory named after the cloned project will appear
2.	The following commands are not applicable for cloning:
	-	`git init`
	-	`git push -u <variable name/ repo clone link> <branch name>`
	-	These 2 commands are not applicable since local machine repo was never created from scratch

## Git merge conflict resolution
1.	If conflict occurs when merging branches on the local machine:
	-	Use `git mergetool`. It allows you to edit the files by comparing with merging branch
	-	After successful mergetool edit, do `git commit -m "<commit message>"`
3.	If conflict occurs when pushing to remote branch then:
	-	Do `git pull --rebase <variable name/ repo clone link> <branch name>`
		-	Above command will give you the details of the conflict
		-	Now use `git mergetool`
		-	After mergetool edit is successful, do `git rebase --continue`
		-	No need to commit at this point
	-	After rebase is successful, push the local branch
