---
layout: post
title: Git from the Commandline
---

In the last few days I've a few questions about how to use git from the commandline. Give that, and since I spent some time making myself a quick (but very messy and handwritten) cheat sheet for a whole bunch of commands, I thought it might be worthwile writing that cheatsheet up a little more neatly, and with a little more explaination. Hence this post.

Note: I'm assuming that you already understand how git works (at least at a high level); if you're not comfortable with that then I recommend reading [this overview](https://git-scm.com/book/en/v2/Getting-Started-Git-Basics) or a similar one first.

Also note: All git commands **must** be run from you repo's directory. I'll say this expcitly for the setup ones, but if it starts with `git` then assume you'll need to have your console open to your repo. Use `pwd` if you need to check where you are.

Also note: I'm assuming throughout this that your remote is called _origin_. If you've named it anything else, or you want to name it anything else, then you should replace the word _orgin_ with your preferred name in all of the following commands.

---

## Setting up your repo

The first thing you'll need to do is to set up your repo. There's two methods for doing this: creating your local repo first, or from an existing remote.

#### Creating a local repo

On your computer, create a directoy (folder) where your repo will be stored, and navigate to it in your console. Then run the command `git init` to turn that directory in to a folder. This might look like:  
```
cd Documents
mkdir myRepo
cd myRepo
git init
```
Congradulations, you now have a repo!

#### Linking an exisitng local repo to a remote

Of course, most of the time you'll want a remote repo to which to push. So, create one on whatever server you want (e.g. github, bitbucket; just go through the online GUI for this bit if you're using a web service). Then find the HTTPS or SSH URL to clone it (there should be a link or button somewhere). Back in your computers terminal window, run `git remote add origin <URL>` in your repo's directory to link your newly-created remote to your local repo. e.g.
```
cd myRepo
git remote add origin example.com:user/myRepo
```
If you're not using SSH, you might get prompted for a password.  
You can run `git remote -v` to verify that this worked correctly, or check to which remote your local is linked.

#### Changing to which remote your local is linked

To change the URL of the remote (e.g. if you're sick of getting asked for passwords and want to switch to SSH), you can run `git remote set-url origin <URL>`.

#### Linking branches

When you create a repo (whether local or remote) it will come with a _master_ branch. If you've just linked your local repo to a remote, then you'll also need to link up these two master branches (note that the same method can be used for linking any two branches which have been created seperately). Make sure you're on _master_ (or whichever branch you want to link), then run `git push --set-upstream origin master` (replace _master_ with the name of the branch on your remote which you want to link if it's different). Note that this will also push any local changes to the remote branch.

#### Cloning a remote repo

Instead of creating a local repo, you can instead clone an existing remote. This is probably the easier option, and the one which you'll use more often if you're working with other people's code. Run `git clone <URL>` to clone the remote found at that URL (again it could be HTTPS or SSH). 
