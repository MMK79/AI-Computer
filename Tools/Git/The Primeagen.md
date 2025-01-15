147 command in git $\rightarrow$ we only learn 13 $\rightarrow$ last 1% of git is not efficient and it is time consuming
# Before we Git we Man
man stands for manual
 ```
man man
man git
```
* Press Q to exit man 
How to use man:
* `j` goes one line down
* `k` goes one line up
* `d` goes one half page down
* `u` goes one half page down
* `/<term>` will search for term
* `n` goes to next search term
* `N` goes to prev search term

> [!important] `man` output is different in each OS, you will not find any "bold" in mac os

# What is Git?
Git is a distributed version control system (VCS)

> [!question] What is the meaning of Distributed System?
## What is the difference of Git with other VCS?
Instead of the traditional centralized control system where even checking out a file required admin privileges, git allows any work to be locally and may diverge as much as you want.

## Why the Git is so damn Good?
You have your version, your version doesn't have to represent the reality of some remote version, it is just your version until you wish to update it.

# Git Commands
In Git, commands are divided into:
* High level ("porcelain")
* Low level ("plumbing")
we mostly go through porcelain commands.
We want you to understand "How Git works?", "What is the Data Structure of Git?"

## Key Terms
* Repo: A Git tracked project
* Commit: A point in in time representing the project in its entirety. $\rightarrow$ you may be think that git will just store differential or things like that but NO! each commit carry the whole your codebase project and you can regenerate your codebase from only one commit!
	* How commits denoted? $\rightarrow$ The `sha` (Secure Hashing Algorithm) that represents a commit, 40 a-f 0-9 characters, is calculated from contents of change, author, time, and more 
* Index/Staging: The Git index is a critical data structure in Git. It serves as the "Staging area" between the files you have on your filesystem and your commit history. When you run `git add`, the files from your working directory are hashed and stored as objects in the index, leading them to be "staged changes".
	* Staging is the area in which you prepare the changes that you WISH to commit.
* Squash: to take several commits and turn it into one commit.
	* Technically a squash would be taking N commits and turning it into N-1 to 1 commit. But typically its N commits to 1 commit.
* Remote: The same git repo on another computer or directory. You can accept changes from or potentially push changes too. Think GitHub
* Work tree, working tree, main working tree: This is your git rep. this is the set of files that represent your project. Your working tree is setup by `git init` or `git clone`.
![[3-step-process-using-git]]
1. Untracked files:
	This means files are not staged for the first time (indexed) or already committed/tracked by the repo. These files are the easiest to accidentally lose work on since git does not have any information about these files
2. Indexed/Staged:
	 This is where the changes are be committed. You must stage before you commit and you stage changes by using the `git add` command. see `man git-add` for more information
3. Tracked:
	These are files that are already tracked by git. Now a file could be tracked AND have staged changes (changes stored in the index) ready to be committed.
## Key Facts about Git
* Git is an acyclic graph, meaning the following cannot exist. (Data Structure understanding needed)
	* A Directed Acyclic Graph (DAG) is a finite graph with no directed cycles. If you start at any node and follow the directed edges, you will never return to the starting node. In other words, a DAG is a structure where edges have a direction and no loops or cycles in the graph.
	![[Direct-Acyclic-Graph]]
* In Git, each commit is a node in the graph, and each pointer is the child to parent relationship
	* You can have more than one parent but you can't have cycle in the graph
* If you delete untracked files they are lost forever. Commit early, commit often, you can always change history to make it one commit(Squashing)
* `man git-<op>` is your friend, use it to read a friendly manual (don't depend on it too much, search the internet too)
## Git State:
We will be doing some changes to the default settings throughout this course.
```
git config --get --global init.deafultBranch

master # or any name to show up here

## PLEASE DO THIS
git config --global --unset init.defaultBranch
```
 Ensure that `rerere` isn't true
 ```
git config --global rerere.enabled

git config --global -unset rerere.enabled
git config --global rerere.enabled
```
* use github/gitlab email, this is no reply email. $\rightarrow$ when you delete the work email from your account, it will show that you did not do anything in github, safe your git commit history
## Your First Git Repo
### Configuring your Git Experience:
Before we begin, we need to configure git to contain your information. Every commit comes with author's name and email. So to ensure you get proper credit and/or blame for all the wonderful code you add, we need to set our name and email!
```
git config
```
Git comes with a config that is global, for all projects, and local, project level. There are other git config levels, but they are irrelevant for the average git experience. 
* Project level config overrides global level config as its more specific (global and local settings, there is 3d and 4th to it too but for now just ignore it)
#### Key Facts:
* All git config keys are in the following shape: `<section>.<key>`
* `--global` flag will ensure you set this key value for all future uses of git and repos
* `user.name` and `user.email` are the keys' used in creating a commit tied to you
* to add a key value, execute `git config --add --global <key> "<value>"`
* you can view any value of git config by executing `git config --get <key>`
#### How to add username and email to my Git?
```
# First check if you already have it or not
git config --get user.name
git config --get user.email

# No result, so now lets add them
git config --add --global user.name "Masoud"
git config --add --global user.email "masoud@gmail.com"

# If you want to change them use the same command
git config --add --global user.name "Milad"
```
## Creating a New Repo
The very first step of any project is to create a repo. To create a rep we use `git init`. There are some options to creating repos but they are out of the scope of this and largely will never be used in your entire career
To create a new git repo you first have to create a new directory or use an existing on with no version control.
Once inside the directory type `git init` and it will create a `.git` folder. (use ls -la to see the result and `.git` folder) 
```
# Going in Desktop
cd ~/Desktop
# Making new Directory
mkdir MyFirstGitDirectory
# Go in the new Directory
cd MyFirstGitDirectory
# Initialize Git
git init -b main
git init
```
* Every git repo comes with a directory that contains all of the state of the git repo. this repo is found in `.git`
	* if you want to see if you have git initialized in a repo you can simply list the files and find if you have `.git` directory or not, you can list all files with `ls -la` command or you can use `find .git` and it will list every file
	* don't use `hook`, Primeagen personal opinion, that is what your CI's for, that is your responsibility 
	* if you want to delete git from your repo you simply delete this `.git` folder
	```rm -rf .git```
* Git keeps its state by using a series of files and directories
## Git Basics
* `git add <path-to-file | pattern>` will add zero or more files to the index/staging area.
* `git commit -m '<message>'` will commit what changes are present in the index.
* `git status` will describe the state of your git repo which will include tracked, staged, and untracked changes.
```
# Create a file first.md
touch first.md
# Check the Status of the git to see untrack files
git status
# add first.md to staging area
git add first.md
# Check the Status of the Git to see its now tracked in the staging area
git status
# Commit with friendly massage
git commit -m 'friendly massage'
# Check the Status of git to see there are no changes pending or untracked
git status
```
### What Changes are in a Repo?
`git log` has many options to make viewing of history a pleasant experience.
### Search for --graph and --decorate in git log manual
--graph: graph representation
--decorate: ref name of commits.(You can reference commits with some sort of name item, branches, tags etc.)
```
# lets open the manual of git-log
man git-log
# search for --graph
/--graph
# search for --decorate
/--decorate
# you can go next and previous items by n and N
# q to quit the manual
# use --graph and see the results
git log --graph
# use --decorate and see the results
git log --decorate
# lets save the results into a file
git log --graph > out
# lets see the file
ls -la
# see the content of the file
cat out
# you see that there is no HEAD->main
# now we will use decorate to list out all the named commit for you
git log --graph --decorate > out
# see the content
cat out
# as you can see now you have the HEAD->main in your file
```
* `--decorate` is not very practical but it is nice to know
* `*` in the start of your `--graph` means that it is a node
## Git Internals
To understand git you must go past the porcelain and check out the plumbing
### SHAs:
git commits come with a SHA (a hash with a 0-9,a-f characters).
* First 7 characters of a SHA $\rightarrow$ git identify what you are referring to.
* To get the SHA of a commit $\rightarrow$ `log` command + copy the long hex string.
#### Why each SHA is different?
Because it capture so many thing, time, user, email and etc.
* SHA stands for Secure Hashing Algorithm
	* SHA is a modified version of MD5
Find commit's file of data within `.git` folder
```
# You can use grep command
grep -rnw ./ -e 9d3303b924151207580b11056a0ec88ae23fa675
# OR
ls -la .git
# then
ls -la .git/objects
# see the 2 first character of your SHA is in the objects
# OR
find .git
```
* Commits exist in the `.git/objects` directory with the first 2 letters as a directory, and the remaining 38 letter as a file
* if you cat the commit file you will see nothing useful
```
cat .git/objects/9d/3303b924151207580b11056a0ec88ae23fa675
#result in
xA
��Zo՗q�,_g�zX���)w�o�}C%
```

> [!important] All of git state is stored in files. Everything!

## Tools of the Plumber
```
git cat-file -p <some-SHA>
```
This will echo out the contents of the SHA.
* you can find the content of your file by going throw repeating the command said before.
* Tree = Directory, Blob = File

> [!important] Git does not store diffs, Git stores complete version of the entire source at the point of each commit. In other words, each commit contains all the information to completely reconstruct the source code that was tracked.

 make a `second.md` file and put some text in it
 * To understand the statement above now go throw the process of finding the files, and the interesting part is that the first file is exist in the second commit with the same SHA
 * Don't think of Git as a "Link List" in "link list" each node is connected to next node, but in Git you can have multiple parents
 * Git stores pointers to the Entire Worktree, not the entire worktree itself, which means its significantly more efficient space wise.
## Git Config
##### --add
add value
```
git config --add <section>.<keyname> <value>
```

```
fem.dev is great
fem.marc is ok
fem.git would
```
```
git config --add fem.dev "is great"
git config --add fem.marc "is ok"
git config --add fem.git "would"
```

### Listing out values
* `--list`: it will list out the entirety of the config
* `--get-regexp <regax>`: this takes a pattern and looks for all names matching 
```
# show all the fem section values
get config --get-regexp fem
```

Try this, change one of the keys value to anything else and then see the result of command above
* you can have keys with same names with different values, it is good cause you can have local setting and global setting, but it is bad cause you can have same keys by accident 
if you try `git config --get fem.dev` you will see `is amazing!` the last one that you added
* Git will use the latest value
* `--get-all` give you call the values
## Unsetting:
you can "unset" a value and you can remove and entire section.
* `--unset`: Unsets one key
* `--unset-all`: Unsets all matching keys
* you can't `--unset` a key with multiple values (you will get an error and nothing will change, try it), you need to `--unset-all`
* `--remove-section` removing whole section
## Locations:
There are several location for git configs and they merge together to produce your final config.
the locations are: `--system`, `--global`, `--local`, `--worktree` and you can even provide a file path for the config via `--file`
* you can use `--global` or `--local` when using commands like `--get`, `--list`, `--add`, `--unset`
* Local values have a higher priority to global values
## Git Branching:
You don't always want to be developing on the main branch. Sometimes you need a feature that is developed off the main line, such that you can return to the main line, update the code, branch off, and perform some immediate needed fix.
This is where git branches come in. They are cheap, virtually free, to create.
```
# make new repo name it hello-git
# cd to the place that you want to create the branch
cd ~/Desktop
mkdir hello-git
# create a file named README.md and write 'A' init
touch README.md
echo A > README.md
# now initialize git
git init
# in every step check git status, add and commit your git
git add .
git status
git commit -m 'A'
git status
```
### Create the Branch
```
git branch foo
```
Nothing happened! $\xrightarrow{actually}$ branch was created pointing to the same commit, but it will not switch branches $\rightarrow$ you are still in main
* Branch will start from commit you are at right that time.
### List out branches
`git branch` $\rightarrow$ all of our local branches, `*` shows what branch you already at
I got the same result when I used `git log` and `git log --decorate`, if this happened for you too there are some internal process in git that is doing this for you, but to see the real version and understand the difference check this out and compare:
```
git log > out
cat out
```
* find where is the branches stores in git directory
```
# find the foo place
grep -rnw ./ -e foo
# find what is in the foo file
cat .git/refs/heads/foo
# it returns you a SHA, go follow the SHA
git cat-file -p d1cd5bf91398c22d456aabab479a5ca3d3abebf3
```
* Branch is just a SHA $\leftarrow$ this is why the branch is free
### Switching Branches
* `git switch <branch name>`
* `git checkout <branch name>`
`checkout` is more versatile, use whatever you comfortable with.
```
# add B to the end of the file
echo B >> README.md
git add .
git commit -m 'B'
# see your log in one line 
git log --grpah --oneline
# add C to the end of the file
echo C >> README.md
git add .
git commit -m 'C'
```
### Delete Branches
if you created a branch and now you wish to delete it, you can use `-d`, `-D`

```
# switch branch
git checkout main
# add D, E to the end of the file and commit them one by one
echo D >> README.md
git add .
git commit -m 'D'
echo E >> README.md
git add .
git commit -m 'E'
```
## Git Merge and Rebase

> [!important] A commit is a point in time with a specific state of the entire code base

There really is one strategy to `merge` code from one branch to another, but depending on the state different outcomes can happen. `rebase` can help put a branch into a pristine state.
### What is Merge?
A merge is attempting to combine two histories together that have diverged at some point in the past.
There is a common commit point between the two, this is referred to as the best merge base (The first in common parent)
git then merges the sets of commits onto the merge base and creates a new commit (merge commit, which have 2 parents) at the tip of the branch that is being merged on with all the changes combined into one commit.
There is also extra information in the logs about these types of commit.
#### How to Merge?
The branch your on is the `target` branch and the branch you name in `<branchname>` will be `source` branch
```
git merge <branchname>
```
 * `git merge --abort` when you see a error that wants you to merge, cause it will not let you `switch`, `checkout`
 * `git checkout HEAD~2` $\rightarrow$ getting back 2 commits before
 * `git reset --hard HEAD~2` $\rightarrow$ hard reseting a branch
```
# this will show you nothin
git log
# but even after hard reset you can see the changes in git
git reflog
# now you can copy that commit 7 first sha character that showing
git checkout 6a52f04
# you recovered that branch
```

* When you use merge you can have 2 different outcomes, it happen because of the history 
	* has a merge commit (you need to input a massage, best common ancestor was the tip of the branch you were merging onto, it can just take the commits and upgrade the pointer, one is diverged and it )
	* doesn't have a merge commit (you don't need to input a message, both are diverged)
* `--parents` add 1 to two extra SHAs signifying the parent chain. This is duplicated by `--graph` but instead of graphical representation, its with SHAs. 
```
# after the merge check the parents
git log --graph --oneline --parents
```
* In this setup foo and main-merge-foo was diverged but in the next set up main and bar are not diverge and merge base is the top of the main

### Rebase
You can update underneath your set of changes (updates the commit where the branch originally points to, change history) $\rightarrow$ it is allowing us to have what is currently our reality then your changes, as oppose to your changes that are tested against some previous reality that is no longer reality, no you can properly inline them and then find out if you actually write something good that works or not
```
   B --- C foo
  /
 A --- D --- E --- X --- Y main	
```
With rebase
```
                           B --- C foo
                          / 
 A --- D --- E --- X --- Y main	
```
* now if you decide to merge `foo` into `main` you can do a ff-merge (fast forward merge)
* rebase allow you to have no merge commits and this is good
#### What Rebase Does?
1. execute `git rebase <targetbranch>`. I will refer to the current branch as `<currentbranch>` later on
2. checkout the latest commit on `<targetbranch>`
3. play one commit at a time from `<currentbranch>` (in order)
4. once finished will update `<currentbranch>` to the current commit SHA (will update your `<currentbranch>` to point to the latest commit)
* You are in a `<currentbranch>` and you want to make this branch be your new base for the next commits
* moves your commit forward in time, and place them one at a time
#### Pros
* When using rebase you can have a clean history with no merge commits. If you are someone who uses `git log` a lot this can really help with searching. (clean history, less commits to track)
#### Cons
* It alters history of a branch. That means that means that if you already had the branch on a remote git, you would have `force` push it to the remote again. (you have the same branch name but with different history)

> [!important] Never Change History Of a Public Branch
> don't ever change history of `main`.

> [!important] What about Personal/Private Branch?
> Having a nice clean history can be beneficial if you use git to search for changes through time.

* `git clone <adress> --depth 1` will result for you to get the last commit on the repo
## HEAD
* try not to play with it, you can use it for interactive rebase
### What is HEAD?
It is a pointer to what you currently use (it is a commit)
## Reflog
The default command of `git reflog` allows you to see where HEAD has been

> [!warning] If histories have diverged far enough, merge the deleted commit could cause some problems as you wouldn't just be merging the one commit, but all the commits between them too 

## Cherry Pick
* `man git-cherry-pick`
allow you to pick one or more existing commits specifically, apply the change each one introduces, recording a new commit for each. This requires your working tree to be clean (no modification from the HEAD commit).

## Remote Git
Often we need code changes that have been created by our fellow college. But how do we get their changes into our repo? Or how to we push our changes to someone else repo?
* It doesn't have to be remote
	* Often we think of remotes repos as GitHub or GitLab, but it doesn't have to be that way.
* A remote is simply a copy of the repo somewhere else

> [!important] Distributed Version Control
> A remote is just another git repo that is of the same project and has changes we may need.

### Add Remote
to add remote the syntax is:
`git remote add <name> <uri>` this `uri` can be anything, ssh, path to your local directory, link to a site
### List Remote
`git remote -v` to list out your remotes and their locations

## Gitism
* Remote is project repo
Typically when you have a remote git repo its called `origin`. This is the source of truth repo.
* Remote is your fork of some other repo
Sometimes you have your remote repo (fork), which you will name `origin` and you have the project repo which is typically named `upstream`.

> [!important] you set your default git branch name `main` and it will be main in every new project, so keep close watch that these are all main but they are different

## Fetch
We can fetch all the git state from our remote repository by executing `git fetch`. This won't update the current branches checked out, just where the `origin/*` has them set to.
* what you doing now is just `fetch` you need to merge so you will have the information locate in the remote folder too.
* `git log <remote name(origin)>/<branch name>`
* if you want to see what branches came down with `git fetch` you can execute `git branch -a` to see all branches that currently exist.
* Branch names can contain the remote they come from.
* Anytime you see a branch that is `<remote>/<name>` it means that it is the last known state of the `<remote>` repo's `<branchname>`. Practically what this means is that at any moment you are likely out of sync with your remote.
	* You don't have to update, you can use yours until you are ready to fetch in changes.
	* Update regularly. The large the out of sync is, the likelihood of conflict goes north.
## Git Pull
Fetching is always a good idea. It keeps your local repo's remotes up to date, but it doesn't alter your state.
The thing is that a lot of the time you just want the changes merged for you into your branch. This can be done with once convenient command, `git pull`.
```
git pull <remote> <branch>
```
* You will fail when you try to `git pull` why? The reason is that we did not setup our `main` branch to track the `origin/main` branch. Git will not automatically track state in a "remote" because that may not be what you want to do. Therefore if you `git pull` it won't know where to pull from since nothing has been specified. This becomes even more obvious once you have more than one remote.
* Target brach. Git assumes that just because two branches have the same name doesn't mean they are the same. So you need to tell git to track branches manually on preexisting branches. `git branch --set-upstream-to=origin/<branch> <branch>`
## GitHub
Actually what is happening with github/gitlab/stash. Its just another repo that everyone has agreed to commit to. (your repo on another computer)

### What About Rebase?
Typically whenever I pull in changes from the remote authority repo I will `rebase` the changes. I do not like adding in a bunch of merge commits. This is a personal preference, but I think its a superior one
* A long lived branch with a bunch of merge commits is much more difficult to revert.
* If every change is a single commit, then the ability to revert is very trivial.
* I prefer to test my changes against the current state of master not against the current state I have fetched
#### Rebase Config
two Strategies for `rebase` changes
1. add `--rebase` flag to a pull. `git pull --rebase`
2. edit your config to make this behavior the default behavior.
```
git config --add --global pull.rebase true
```

## Git Push
If you wish take your changes and move the remove repo, you can do this by using `git push`. Much like pull, if you are not "tracking" then you cannot simply `git push` but instead you will have to specify the remote and branch name.
* When you `checkout` git will start the tracking for you
	* Explanation: When we checked out `bar` we automatically started tracking. We didn't have to create the branch. This is because locally we do not have a `bar` branch, but origin does. Also `origin` is our ONLY remote. Therefore it makes sense to create a local branch and track the remote it came from.
* `git push <remote> <local_name>:<remote_name>` allows you to push and have it received with a different name
* `git push <remote> :<remote_name>` will delete a branch on the remote

> [!important] When we fetch it didn't made us move forward, but when we pushed it moved forward, why?
> We are not using that repo and branch in any capacity, and we are doing a push which is an alias to doing fetch and the merge, we are just doing for them.

### Problem we will Face
You have made a change but you need to pull in changes from a remote repo, what do you do?
commit changes then rebase or merge?
* If you create a commit with changes that are half baked just to pull in origin changes you will have your (potentially) broken commit, a merge commit, then your fixing commit. If you need to revert these changes, it will get more difficult (more on reverting later).
	* Your changes with rebase, will get put on top of all the incoming changes which allows your partial commit easier to work with. This style also makes squashing easier
* Or you can Stash, so you can have your partial commit
* Work-trees
## Stash
`git stash` will take every change tracked by git (change to index + change to work-tree) and store that result, much like a commit, into the 'Stash'.
Use git stash when you want to record the current state of the working directory and the index, but want to go back to clean working directory. The command saves your local modifications away and reverts the working directory to match the HEAD commit.
* Stash is a Stack of temporary changes
`git stash` to push your changes into the stack
* Stashes, much like commits, can come with a message (`-m "<your message>"`)
* list amount of stash you have `git stash list`
* `git stash show [--index <index>]` show changes
* `git stash pop` pop the latest stash
* `git stash pop --index <index>` 
* `man git-stash` keep the `man` command in your head and use it
* RTFM = Read The Friendly Manual

* you can't pull when you have un-staged changes
* `git log -S <character>` search commit changes
* `git log -S <character> -p`

## Worktrees
Is another copy of your repo without all the weight of the repo

## MOAR Rebasing
Rebasing as being ables to realign where the branch point exists for one branch onto another. In other words, you make history linear.
* You get new commits when you rebase, cause commit contain history and you changing history and etc.
### Interactive Rebasing and Squashing
```
                           B --- C personal branch
                          / 
 A --- D --- E --- X --- Y master	
```
Turn it to:
```
                           BC personal branch
                          / 
 A --- D --- E --- X --- Y master	
```
Along with squashing, interactive rebasing allows you to edit messages and more
#### To Create a Conflict
The easiest way to create a conflict is when you have two changes to a rep that cannot be resolved by the merging strategies. In other words, edit the same line.
Often is not obvious what is in conflict just by the message (if there is a large set of changes). So a simple way to see what is conflicted by checking out the status.
* `git status` to get more information on the merge conflicts
* You can abort the merge due to the conflict by executing `git merge --abort`
*  From HEAD till the equal sign is your change in this repo, and from equal sign till the sha of the commit, is the commit on the other repo
	* when you handled the conflict and `git add .` then `git status` you will see nothing in the staging phase, cause you already did this process in the previous steps, what you did now was just simply handling the conflict
*  once you resolve a conflict and you don't take upstream's you will get merge commits until you sync your changes back to the remote
* Merge finds the best common ancestor, replace things, creates a merge commit. Rebase move changes forward to the tip and then replay a change at a time.
	* Problem with Rebase: What if a conflict happened in the past? 
		* If you rebase a repo that already conflict in it, but it solved when you rebase it, it will replay commit that contained the conflict it will conflict again, again and again.
	* You can't push from the main branch to origin/main; simply someone else changing your environment without telling you and etc. so what you need to do in remote repo is to simply change your branch then push (We cannot push to a brach that is the current branch of the target repo)
		* It is a problem that you pretty much won't run into cause you're not gonna have 2 exact same repo on the same machine
* We can `git rebase --abort` due to the conflict
* Once you have resolved the conflict we need to `git rebase --continue` instead of `git commit`
* When you `git pull --rebase` and you see a merge conflict, when you into the file you see that the upstream change is in the higher than your personal change why is that? when you rebase you checkout the branch your rebasing on, then you play your commits one at a time, THEN you checkout the branch once you came from, and then it updated. so it is merge conflict message is inverted when you looking at rebase (ours is theirs and their is ours) 
	* You can fully remove something, danger of rebase
## RERERE
how to handle the problem with rebase? `rerere`
rerere is just one of the strangest options in all of git. There are some basic commands that can be ran.
* You just need to config, but you can check `man git rerere`
The git `rerere` functionality is a bit of a hidden feature. The name stands for "reuse recorded resolution" and, as the name implies, it allows you to ask Git to remember how you've resolved a hunk conflict so that the next time it sees the same conflict, Git can resolve it for you automatically.
* You can enable `rerere` globally or locally with `git config --add rerere.enabled true`
	* `git config --list --local` to see the local value
### Ours vs Theirs
* Ours is the change of the current branch
* Theirs is the change of the incoming branch
* `git checkout --ours <file name>` (in merge ours is really ours, but in rebase ours is theirs)
* `git checkout --theirs <file name>` (in merge theirs is really theirs, but in rebase ours will be theirs)
* If the remote had changes that aren't conflicted, it still pull everything on `--ours`, it is a full deal
## Interactive Rebase
Primary use case of interactive rebase is squashing which can be very nice for history.
You can also edit individual commit messages and more, But Primeagen didn't used it that much.
To Begin an interactive rebase we need to provide a point in time to rebase with. Typically, the simplest way to do this is with `HEAD~<number>` . `HEAD~1` means one commit back from `HEAD`. 
```
git rebase -i <commit-ish>
```
## Primeagen Workflow
1. Many small commits with a message "SQUASHME:"
2. At the end of the dev cycle, I squash and give a proper message
3. Pr with a singular commit
4. Before I PR I ensure I am at the tip of the branch and that any CI runs against latest master changes

# Git Bisect Problem
* somewhere in the last 500 commits something has gone wrong.
* To test if something has gone wrong takes several minutes or longer.
This is not a common problem, but it is a problem you will run into in the real world. And it can be complete pain to resolve if you do not know the tools you have at your disposal.
## Logs
One very straight forward strategy to determine where a bug began is manually reviewing logs and identifying when a file changed.
### Pros
* If you know the file/module in which the bug exists and the file changes infrequently then logs can be a very fast method to identify the problem commit.
	* This can be particularly useful when people use good commit massages. It will help you understand why they made the change they did.
* If people take seriously their commit messages and add keywords then searching can provide fast and powerful mechanism to find the correct change.
### Cons
* The file/module in which contains the bug changes frequently
* Poor/No commit messages
* You cannot boil down the bug to a specific keyword
* If there are too many commits that match searching it can much more cumbersome than using other methods
* You simply don't know any keywords to narrow down your search
### Searching with token
1. install any deps with `npm i`
	* check if you have `node` and `npm` installed
		* `node -v`, `brew install node`
		* `npm -v`, `brew install npm`
			* make sure you have `homebrew` installed
2. run tests with `npm run test`
* Use `man git-log`
* Diffs of the logs could be useful
* Search often referred as grep `git log --grep=<pattern> -p`, `-p` will show you the changes too 
### Searching with filename
One flaw in our previous search is that we were looking for occurrences of a word in commit messages which may not be the most efficient way to look. We know the file that is probably the problem, we could always check it history
```
git log -p -- file1 file2 ...
```
* `-S` allows you to search for text in the change itself
## Bisect
Bisect search through git commits, and you get to mark if something is good or bad, and it will determine which commit you should look at.
To perform `bisect` you need two things to be true:
1. All commits are ordered. They are ordered by time
	* If there is a problem that is currently plaguing the project and you go back 10 commits and observe the problem is still there. You don't have to check 9 commits back, or 8 back, you know that the problem currently exists and 10 commits ago its present. Therefore its present betwixt HEAD and 10 commits ago
2. You know a commit that the issues is not present or can find it easily enough (It doesn't matter how much commit you go back, you just need a point in time that it works)
### Pros
* You need not to know anything about the bug and you don't have to rely on commit messages. Simply a failing test case or a way to reproduce the bug mannually or programmatically.
* It is the fastest way to search a stored space.
* You don't have to be searching only for a bug but for any change in your project. You can also use this to find where a bug got fixed, where a performance regression happened, or anything else you can think of.
### Cons
* Not really any. Unless it s trivial but that works via log searching this is pretty much the best possible option.
### Performing Bisect
Git bisect requires you to have a last known good commit and a last known bad commit. From there it is able to perform the binary search.
The last known bad commit doesn't have to be best fit and neither does the last known good commit. The point is that bisect does the searching, not you.
* O(log(n))
### The Basics of Bisect
1. Start git bisect `git bisect start`
2. Set the known bad commit `git bisect bad`, uses the current one
3. Set the known good commit `git bisect good <commit>`
4. test
5. `git bisect <good | bad>` depending on how the test runs
6. repeat the 4 step until git tells you the commit 
### Git Bisect -Automated
* `git bisect reset`
1. `git bisect reset`
2. `git bisect bad`
3. `git bisect good <SHA>`
4. `git bisect run <cmd> --run`

## The Decision We All Face
Push forward OR Roll back
* Rolling back can often require you to revert changes made to the main branch.
	* restore effectively change everything to what previous state was
	* revert antimatter to matter, invert a change as a commit and then you commit that, changes what you done invertedly, it do what you did backward
## Git Revert
You just need to provide the commit-ish
```
git revert <commitish>
```
* You can get conflict in reverting
* You get the commit message at the end of the revert
	* This is the greatest argument why you want to rebase squash, because there is no merge commit, there is no more this history that you changed and etc. if you just rebase squash you can simply remove the change
* revert is a inverse commit, it is not that it removes it from our history, cause if it was removed from our history then every branch would now have invalid state.
## Git Reset
This has such a wide range of responsibilities from get rid of what is in the work-tree or the index to walking back a commit
* get rid of current changes
### Git Reset Soft
Git reset soft can be very useful if you need to make a commit that is partially finished and you want to edit that commit and change the contents
You walk back a commit, your branch come back a commit with you, and that commit that you just effectively forgot and changed history will become a change inside a work-tree index. (undo the commit but save the changes)
Now lets say we need to continue to edit our previous commit. We have two options:
1. We could make changes and use `commit --amend`. If you are not familiar with `git commit --amend` it allows you to meld the current staged changes into the previous commit and edit the message.
	* `commit --amend` allows you to take your current changes and retroactively apply them to the commit that you already on, `--amend --noedit` edit the commit your just on but you don't have to change the commit message
	* Using CI instead of showing useless changes, you will see one change:
		* echo a space into the end of the file, `echo " " >> filename`
		* `git commit --amend --noedit`
		* `git force push`
2. We could use `git reset --soft HEAD~1` to move `main` back one commit and alter the index and work-tree to match the contents of the commit
 * Both operations will change the SHA since we are changing the graph fundamentally
### Git Reset Hard
Hard will do the same thing as soft except it will drop changes to the index and work-tree. That means any work that is being tracked by git will be destroyed 
* Only destroy the thing that git already know about (staged files)
* You can get back what you lost by simply using `reflog` and find the position that you want

## Worktree
Generally when we say `worktree` we mean a `linked working tree`
When you `git init` a repo it creates the `main working tree`. A `linked working trees` (a branch from main tree in its own state) is a just another tree much like main working tree just without all the git history within the `.git` directory. In fact, the `.git` directory is not a directory at all, but just a file pointing to the `main working tree` directory.
### Add
```
git worktree add <path>
```
* The `basename` of the `path` will be used as the branch name
	* `basename /foo/bar/baz` >> `baz`
### List
```
git worktree list
```
### Delete
There are couple ways to do this:
1. You can use `git` and
	* `git worktree remove ../<folder>`
2. you can use `rm -rf` and `git worktree prune`
### Pros
They are cheap to make since they don't need `.git` history. They are just a pointer. They are just slightly more expensive than a branch. But you get a commit to work on that is outside your main working tree. That means if you need to pivot quickly you don't have to commit, stash, or anything just create a new linked working tree!

### Cons
If each branch has a high setup cost. Like if your `npm` install takes 100 minutes due to everything-js dependency, work-trees can be more of a pain
* rust can easily eat up a couple gits per branch
* npm installing on each branch can take a minute
* go is great
* .env files can be a bit of pain
	* if it is checked into the repo your fine
	* if it is not checked out into the repo, you will have copy of your env file around

* Wroktree makes you to have another entrance to your folder, so that way you can actually have a 2 running copies, so you can have your feature development in a worktree and your main line in the main worktree, so when you do update code on main and simply leave your working tree in whatever states it's in without need to switch branches
* Branch Switching is like a anti-pattern, instead just use worktree to constantly to build everything, and you will don't need to stashing, and when you are done you just prune it.
## Named locations within Git History
At some point there are changes in which represents a version of your software you want named.
This could be a version you are releasing as an open source library or an internal note for the public version of a website
Git has covered with `tags`
## Tags
tag is branch that cannot be changed (immutable object). It can only be deleted.
```
git tag <name> # to create
git tag -d <name> # to delete
git tag # to list
git chekcout <tagname> # to checkout a tag
git pull --tags
```
* It will be shown in `git log`

# Tools
T-pope (vim-fugitve)

* git-lfs, don't care about history size
* Keep things small, do more review, life will be easier
* Cloak to not show .env paths
* gitignore, `.git/info/exclude` gitignore but only for you

Resources:
[Everything You Need To Know About Git - Note with Problem & Solution in it](https://theprimeagen.github.io/fem-git)
[Everything You Need To Know About Git - Videos](https://frontendmasters.com/courses/everything-git/)
[GitHub Documents](https://docs.github.com/en)
[Git Documents](https://git-scm.com/)
