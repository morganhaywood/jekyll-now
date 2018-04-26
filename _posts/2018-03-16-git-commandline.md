---
layout: post
title: Git from the Command line
tags:
  - learnings
  - git
  - CLI
---

In the last few days I've a few questions about how to use git from the command line. Given that, and since I spent some time making myself a quick (but very messy and handwritten) cheat sheet for a whole bunch of commands, I thought it might be worthwhile writing that cheat sheet up a little more neatly, and with a little more explanation. Hence this post.

You can find (a neater version of) my cheat sheet for all the commands covered in this post [here]({{site.url}}/post-assets/git-commandline/git_cheat_sheet.pdf).

Note: I'm assuming that you already understand how git works (at least at a high level); if you're not comfortable with that then I recommend reading [this overview](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics) or a similar one first.

Also note: All git commands **must** be run from you repo's directory unless otherwise stated. I'll say this explicitly for the setup ones, but if it starts with `git` then assume you'll need to have your console open to your repo (again, unless I specifically say otherwise). Use `pwd` if you need to check where you are.

Also also note: I'm assuming throughout this that your remote is called _origin_. If you've named it anything else, or you want to name it anything else, then you should replace the word _origin_ with your preferred name in all of the following commands.

---

## Setting up Your Repo

The first thing you'll need to do is to set up your repo. There's two methods for doing this: creating your local repo first, or from an existing remote.

#### Creating a local repo

On your computer, create a directory (folder) where your repo will be stored, and navigate to it in your console. Then run the command `git init` to turn that directory in to a git repository. This might look like:  
```
cd Documents
mkdir myRepo
cd myRepo
git init
```
Congratulations, you now have a repo!

#### Linking an existing local repo to a remote

Of course, most of the time you'll want a remote repo to which to push. So, create one on whatever server you want (e.g. GitHub, Bitbucket; just go through the online GUI for this bit if you're using a web service). Then find the HTTPS or SSH URL to clone it (there should be a link or button somewhere). Back in your computers terminal window, run `git remote add origin <URL>` in your repo's directory to link your newly-created remote to your local repo. e.g.
```
cd myRepo
git remote add origin example.com:user/myRepo
```
If you're not using SSH, you might get prompted for a password.  
You can run `git remote -v` to verify that this worked correctly, or check to which remote your local is linked.

#### Changing to which remote your local is linked

To change the URL of the remote (e.g. if you're sick of getting asked for passwords and want to switch to SSH), you can run `git remote set-url origin <URL>`.

#### Linking branches

When you create a repo (whether local or remote) it will come with a _master_ branch. If you've just linked your local repo to a remote, then you'll also need to link up these two master branches (note that the same method can be used for linking any two branches which have been created separately). Make sure you're on _master_ (or whichever branch you want to link), then run `git push --set-upstream origin master` (replace _master_ with the name of the branch on your remote which you want to link if it's different). Note that this will also push any local changes to the remote branch.

#### Cloning a remote repo

Instead of creating a local repo, you can instead clone an existing remote. This is probably the easier option, and the one which you'll use more often if you're working with other people's code. Run `git clone <URL>` to clone the remote found at that URL (again it could be HTTPS or SSH). This does **not** need to be run from your repo's directory; it will create a new directory with the same name as the remote repo inside the current directory. If you want it to be called something else, then use `git clone <URL> <directory-name>` instead; this will create a new directory called _directory-name_ and clone into there.

---

## Committing

#### Seeing what you've changed

`git status` will show you what's changed. It will split any changes into three categories: staged files, upstaged files, and untracked files. Staged files will be included in your next commit. Unstaged files have previously been committed, but any changes you have made since will **not** be included in your commit. Untracked files have never been included in a commit.  
In general you can commit with unstaged or untracked changes, but can't do much else.

#### Staging files

`git add <file-name>` will add said file to staging. It will then be included in your next commit.  
`git add .` will add **everything** to staging, including untracked files.

#### Committing

`git commit -m "<message>"` will commit your staged files with the given commit message.  
This message should generally be short and to the point, but descriptive enough that your team can understand what your changes do. It should also generally start with a verb in the imperative form (e.g "Create index file", "Fix typos in readme").

---

## Looking at the History

`git log` will show you a list of commits for the current branch. Note that depending on how many there are, this may act like a read-only vim editor. You should be able to scroll normally, and press `q` and enter to quit (see [this]({{site.url}}{% post_url 2018-02-19-vim-crash-course %}) for more info on vim).  
Each commit in the log should have a SHA listed. To see more information about a specific commit, run `git show <SHA>`.

---

## Pushing and Pulling

#### Push to remote

`git push` will push all your changes to the remote. If there are changes on the remote which you don't have, then you must pull them first (you'll get an error message to this effect).  
If you're using HTTPS, you might be asked for a password. If you are having touble with this, I recommend switching to SSH (I find it a lot more reliable).

#### Pulling from the remote

`git fetch` will download any changes from the remote. `git pull` will both fetch and integrate the changes. In general I use the latter, unless I know I just want to view changes in the remote (e.g. which branches have been created).

---

## Stashing

Sometimes changes get in the way of doing things in git. If you don't want to commit them, but do want to pull, switch branches, etc, you can stash them instead. This adds your unfinished changes to a stack, which you can then reapply whenever you want.  
`git stash` will add your current uncommitted changes to you stash. `git stash list` and `git stash show` will show you what's currently in your stash (the former all items and the latter a more detailed view of the top). See below for sample output.  
![stash list vs show]({{site.url}}/post-assets/git-commandline/stash-list-and-show.png)  
Finally, `git stash apply` will apply the top of the stash to your current working branch.

---

## Dealing with Mistakes

Check out the man page for `git reset` (`man git-reset`) for more options, but what follows are some of the most useful commands.

#### Removing files from staging

If you accidentally add the wrong file to staging  (e.g. not checking what's changed before running `git add .`) you can use `git reset HEAD --<file-name>` to remove it. This will keep any changes you made to file, it just won't be staged anymore.

#### Reverting changes to a file

If you want to remove changes you've made to a file (but not committed yet) you can use `git checkout --<file-name>`.

#### Reverting a branch to remote

If you made commits you didn't want to, use `git reset origin/<branch-name>` to reset the _branch_ to what's on origin. This will keep any changes you've made, but they won't be committed any more. `git reset --hard origin/<branch-name>` will discard any changes you've made.

---

## Ignoring Files

Sometimes you need to have certain files in you repo, but you don't necessarily want to push them to the main repo. In this case we can tell git to ignore them (so you can use `git add .` without worrying about them). A quick search for "gitignore" will give you a lot of suggestions for what falls in to this category, but for starters if you're using IntelliJ I suggest the _.idea_ folder.  
The list of files to ignore are stored in a file called _.gitignore_. You'll need to create and edit this manually. File names (or paths) should be added one per line, and * can be used as a wildcard. e.g.
```
.idea/
mytestdata.zip
*.txt
```
will ignore the _.idea folder_, the file _mytestdata.zip_, and all text files.  
If you want to do it from the command line, I suggest:
```
touch .gitignore
vim .gitignore
```
(or just `vim .gitignore` to create and edit it in one step). See [this]({{site.url}}{% post_url 2018-02-19-vim-crash-course %}) post if you're unfamiliar with vim.

---

## Branching

#### Viewing branches

`git branch` will show you all of your local branches. `git branch -r` will show you all the branches on your remote, and `git branch -a` will show you all branches (both local and remote).

#### Creating a branch

`git checkout -b <branch-name>` will create a new branch locally and switch you to it. Alternatively, `git branch <branch-name>` will only create it, not change your working branch as well. Finally, `git push origin <branch-name>` will create a new branch on origin.

#### Getting a branch from remote

If a branch already exists on origin, you can use `git branch <branch-name> origin/<branch-name>` to create a local branch which will track the remote branch.

#### Switching branches

`git checkout <branch-name>` to change your working branch (similar to creating one above, but note the lack of the `-b` option, which is the flag to create a new branch).

#### Deleting a branch

`git branch -d <branch-name>` will delete a branch locally. Make sure you've merged your changes before doing this! I find that it's generally easier to delete branches on the remote through the GUI (e.g. if you're using GitHub) since you'll probably handle pull requests that way anyway (and it's part of the same screen), but if you **really** want to, you can use `git push origin --delete <branch-name>`.

---

## Combining Branches

#### Merging

`git merge <branch-name>` will merge the given branch into your current one.  
The way I remember which way around this goes is that you only make changes to your **current** branch. Merging branch A into branch B effectively adds commits to B, so you have to be on B.  
If you have any conflicts then you'll get a failure message:  
![merge conflict message]({{site.url}}/post-assets/git-commandline/merge-conflict-message.png)  
Open the files listed in your editor, and resolve the marked conflicts:  
![conflict in file]({{site.url}}/post-assets/git-commandline/conflict.png)  
Then add your resolutions to staging by using `git add <file>` or `git add .`. Finally, finish the marge by running `git commit`. This may dump you into vim; if you're unfamiliar you can hit `:wq` and enter to use the default message, or see [this]({{site.url}}{% post_url 2018-02-19-vim-crash-course %}) blog post for a crash-course.  
If you can't resolve the conflicts, or you have a sudden change or heart, you can use `git merge --abort` to abort mission (so long as you haven't committed yet).

#### Squash and merge

Use `git merge --squash <branch-name>` to squash and merge the given branch into your current one. The main difference between this and a normal merge is that you'll need to run `git commit` to commit the squashed commit and finish the merge (again, this will dump you into vim; see above). If you have conflicts, then the workflow is the same as for a normal merge. Likewise, aborting works the same.

#### Rebase

Note that this is a contentious move, since it changes the git history. People have **very** strong feelings about this. In general, don't rebase unless your team has okayed it first (if you're working on a personal repo, do whatever you want).  
`git rebase <new-base-branch>` will rebase your current branch **onto** the given one (you're moving A to the latest commit on B, so A is what's changing). `git rebase <new-base-branch> <branch-name>` will rebase _branch-name_ onto _new-base-branch_.  
If you have conflicts then you will need to resolve them and stage your resolutions (`git add <file>`/`git add .`). Then use `git rebase --continue` to continue rebasing. Expect several rounds of conflicts (possibly in the same places), since the commits are added one at a time.  
If you can't resolve the conflicts, or something goes wrong, you can use `git rebase --abort` to abort mission.
Finally, after a rebase you will need to use `git push --force` in order to force a push to the remote. This is because you are overwriting the exisiting history.

---

I hope that helps get you started with using git from the command line!
