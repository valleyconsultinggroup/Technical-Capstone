# Collaboration
One of the greatest features of Github is the ability to work on projects with your peers. Here, the remote repository is king. One remote repository can be shared among multiple users. However, in order to harness this feature, there is a development process that you must follow. While collaboration is one of Github's best assets, if it's misused, it could also be the reason your project becomes irrecoverable. :skull:

## General Overview
Before we dive into the commands and nuances, let's start with a more holistic approach, a roadmap of exactly how Github collaboration goes down. :octocat:

Let's say you and Randy are working on the next hot VR play together. First and foremost, you and Randy create the same repository and add yourselves as collaborators. To get started, you add, commit, and push a couple basic files to the first repository. Let's say your directory contains 'game.cc' and 'character.cc'.

Now, what happens if both you and Randy edit 'game.cc', and attempt to push your commits to the remote repository? In this situation, whoever pushes their commits first will not see any issues. Let's just say you push your commits before Randy. When Randy attempts to push his commits, he will encounter what's called a *merge conflict* :fearful:.

The name is pretty self explanatory. When you commit changes to a file, you are, in technical terms, *merging* the modifications you've made with the previous commit. A merge conflict occurs when there are competing changes that Git does know how to resolve. For example, in this case, if you and Randy both edited the same line(s) in 'game.cc', Git would have no idea which version it should be keeping.

Therefore, keep in mind, in the future, if you and your partner are simultaneously working together on a shared repository (CS61B :open_mouth:), **make sure to not edit the same lines of a file from the same commit**. A good rule of thumb for avoiding merge conflicts is to not work on the same files.

As a last note, there are ways to resolve merge conflicts. In fact in some cases, it's actually a good idea to have Git auto-resolve those conflicts. For example, if you have two conflicting commits on a line in a Python file, you can revert the version you don't want and commit the line that you want to keep. However, files such as simple PDFs or an iOS Storyboard file are visual interpretations of 1000s of lines of byte code and XML. Manually resolving merge conflicts with these files are much more tedious. Abiding by the one-person-one-file rule above will save you a lot of hair-wrenching and time in the future, promise.

## Branching Out!
So your game's going pretty well so far. It's a RPG game set in the 1970s with great graphics :metal:, and now you're looking for the next feature to add. Suddenly, you've got it! Multiplayer is the way to go! But it's no easy task, and to be honest, you're not quite sure it'll come out the way you want to. Do you want to attempt creating the multiplayer feature at the risk of breaking the code in your git repository?

Luckily, Git doesn't force you to choose one or the other. Introducing *git branch* :evergreen_tree:. 'git branch' allows you to create different copies of your project from the same commit. Here's a visualization to help:

![](../Screenshots/branching.png)

Branches are simply pointers to commits. As a convention, the 'master' branch tends to be a pointer to the working version of a project. By the example, the 'master' branch would most likely hold the latest working copy of your game while the 'feature' branch would point to the multiplayer project. When you merge a branch with another, just like before, it's important to make sure there are no conflicts.

## Commands
### Creating / Switching Branches
Let's start from the basics: creating and switching from branch to branch! Every repository has at least one branch, commonly called the master branch. When you create another branch, you're photo-copying your project at its latest commit. Local branches have a corresponding remote branch that exists on Github. With branches, your 'push' command will look a bit different. Instead of 'git push origin master', you'd replace 'origin' and 'master' with your remote and local branch names in that order.

Option & Commands | Purpose
--- | ---
git branch | View list of all branches
git branch (name) | Create a new branch with 'name'
git branch -d (name) | Delete a branch with 'name'
git branch -r | List remote branches
git branch -a | List local + remote branches
git checkout (name) | Switch onto existing branch named 'name'

### Retrieve Updates from Remote Repository
Continuing with Randy, let's say Randy pushed a couple changes to the remote repository. Now, before you keep working, it's important that you retrieve Randy's changes so that your local directory reflects those changes. This is where the 'pull' and 'fetch' commands prove helpful. These commands take unseen remote repository changes and update your local repository.

Keep in mind, however, that this command is where merge conflicts most often appear. If the same file is modified both locally and remotely, git pull is what exposes the conflict. Some best practices are to make sure to 'git stash' conflicting changes before pulling.

Option & Commands | Purpose
--- | ---
git pull (remote) (branch) | Applies 'remote' modifications to local 'branch'
git fetch (remote) | Retrieves changes from 'remote', does not apply them locally
git merge (branch) | Combines two branches by creating a new commit or fast forwarding
