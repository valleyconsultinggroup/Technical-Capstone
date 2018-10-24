# Basic Commands
Here, we're going to review some of the basic commands in git, especially the options associated with adding, removing, and monitoring changes in your files. An option can be thought of as a parameter for a unix command, and they usually come in the form of -(character) or --(word).

There are a multitude of options with varying utility, but for now, we'll review the staples. If you're interested in learning about more options out there, you can always type in just the git command itself (i.e. 'git add') and you'll be given a list where you can read about the syntax, parameters, and utility of each option. :octocat:

## An Anecdote
Perhaps the greatest initial barrier to learning Git is understanding what each command is actually doing. Here's an anecdote that, I hope, will serve as a roadmap for comprehending Git going forwards.

Imagine an apple farmer :apple:. As a farmer, the first thing you'd probably do is pick every apple off of your tree. Then, you'd inspect your harvest, throwing out the bad apples that have mold, insects, etc., while keeping the good ones. Finally, you'd pack the good apples and send them off to the store and turn it into profit.

Git works in a similar fashion. You're the apple farmer. An apple is the equivalent to modifying your project. In other words, every changed file is recorded with a unique signature aka the apple. When you 'git add', you're telling the computer which modifications, or which apples, you want to keep. Finally, with 'git commit', you've packed up the modifications and officially saved a new version of your directory.

## Commands
### Adding / Staging Changes
```unix
git add -A
git add (name of change here)
```
'git add' :heavy_plus_sign: is the Git command responsible for selecting modifications. When a file is modified, your computer has no idea which modifications are or aren't important. 'git add' is essentially your way of picking out the modifications that you're telling your computer you'd like to keep. A file that has been added is considered 'staged'. To select a change individually, just 'git add (name of modification here)'. Out of the options, you will most likely be using 'git add -A' the most.

Option | Purpose
--- | ---
-A | Stage *all* recorded changes. Same combination of '.' and '-u'
. | Stage *new* and *changed* files, but not *deleted* files
-u | Stage *changed* and *deleted* files, but not *new* files
-v | Verbose, provides more information about execution
-f | Allows you to add ignored files
-i | Interactive mode, a bit confusing

### Committing Staged Changes
```unix
git commit -m 'Commit Message Here'
```
It's time to ship the apples. 'git commit' :heavy_check_mark: finalizes the staged changes you want to keep and revises the .git file to store a new latest version of the directory. With git commit, you can view previous versions of the directory, compare different commits, and revert back to a previous commit in case something happens to your project.

Option | Purpose
--- | ---
-a / --all | Stage *changed* and *deleted* files, but not *untracked* files
-p | Interactive patch allowing you to choose changes to commit
-m | Edit commit message, multiple -m's are separated into paragraphs

### Removing or Postponing Changes
```unix
git rm (name of file)
git rm --cached (name of file)
git stash save --keep-index
git stash drop
```
You've encountered a change that you don't want. Time for cleanup. There are two ways to deal with changes that you want. Either delete those changes, or store these changes to be introduced later.

One way to go about deleting a file is 'git rm' :heavy_minus_sign:. This command removes a file from a working directory. Unlike a regular unix 'rm', 'git rm' not only removes the file, but also stages that deletion. If you only want to delete the file from your .git file, but would like to keep a copy in your local directory, use the '--cached' option. Keep in mind, 'git rm' removes *files*, not *changes*.

On the other hand, if you're not sure you want to keep the changes you've made, use the 'git stash' :question: command. 'git stash save' allows you to remember the modifications you've made while returning you to the latest commit of your working directory.

Option & Commands | Purpose
--- | ---
(stash) list | list stashed modifications
(stash) show | inspect stashed modifications
(stash) apply | restore stashed modifications to working directory (watch for conflicts)
(rm) -r | recursive removal. Useful for removing files
(rm) -f | remove files not up to date with last checked commit. Guards against removing files w/ unregistered changes

### Remote Repository Interaction
```unix
git remote add origin ...
git remote prune
```
So far, the above commands have been enacting change on a local level. With 'git remote' :cloud:, we are able to manage Github repositories stored in remote servers. Most remote commands will revolve around getting/setting repository URLs or renaming branches. A sizable set of remote commands also deal with branch management, so we will touch on them in this table, but if you're unclear as to what those are, refer to the collaboration section.

Option & Commands | Purpose
--- | ---
add <branch> <URL> | Create a remote alias (branch) for a repository URL
get-url / set-url | Retrieve or change a remote alias' associated URL
prune | Removes deprecated remote branch references
rename <old alias name> <new alias name>| Rename an alias

### Miscellaneous
Command | Purpose | Options
--- | --- | ---
git config | Configuration. Change your username and password, use --global for every repository |
git blame | Show who, what, and when something changed in a file |
git diff | View changes that have occurred in tracked files |
git log | Show history of commits starting with latest commit | -p <file> (file changes over time)
git status | Show the status of different files and changes since the most recent commit | -s (short)
