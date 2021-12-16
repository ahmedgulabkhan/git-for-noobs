# Git for Noobs

![Git for Noobs](./assets/git.jpg)

This documentation will help you get started with Git, it's terminology, and also contains the most 
widely used git commands.

This documentation is open for contribution and for updating any mistakes.

## Table of contents
- [What is Git?](#what-is-git)
- [Setting it up locally](#setting-it-up-locally)
- [Configuring Git](#configuring-git)
- [Concepts and terminology](#concepts-and-terminology)
- [Most widely used commands along with their use cases](#most-widely-used-commands-along-with-their-use-cases)
  - [git add](#git-add)
  - [git apply](#git-apply)
  - [git branch](#git-branch)
  - [git checkout](#git-checkout)
  - [git clone](#git-clone)
  - [git commit](#git-commit)
  - [git config](#git-config)
  - [git describe](#git-describe)
  - [git diff](#git-diff)
  - [git fetch](#git-fetch)
  - [git init](#git-init)
  - [git log](#git-log)
  - [git merge](#git-merge)
  - [git mv](#git-mv)
  - [git notes](#git-notes)
  - [git pull](#git-pull)
  - [git push](#git-push)
  - [git rebase](#git-rebase)
  - [git remote](#git-remote)
  - [git replace](#git-replace)
  - [git reset](#git-reset)
  - [git restore](#git-restore)
  - [git revert](#git-revert)
  - [git rm](#git-rm)
  - [git show](#git-show)
  - [git stash](#git-stash)
  - [git status](#git-status)
  - [git switch](#git-switch)
  - [git tag](#git-tag)
- [Miscellaneous](#miscellaneous)
- [References](#references)


## What is Git?
Version control, also known as source control, is the practice of tracking and managing changes to 
software code. Version control systems (VSCs) are software tools that help software teams manage changes to 
source code over time. As development environments have accelerated, version control systems help 
software teams work faster and smarter.

Git is the most widely used modern version control system in the world today. Having a distributed 
architecture, Git is an example of a DVCS (hence Distributed Version Control System). Rather than have 
only one single place for the full version history of the software as is common in once-popular 
version control systems like CVS or Subversion (also known as SVN), in Git, every developer's 
working copy of the code is also a repository that can contain the full history of all changes.

## Setting it up locally
### Installation

To install Git on your local machine, visit [https://git-scm.com/downloads](https://git-scm.com/downloads). 
Depending on your operating system, download and install the latest version accordingly. During the 
installation process, make sure that you select thr option to add **git** to your path. This makes 
sure that the git commands are recognized from any location in the terminal.

### Verify the installation
Open your terminal and type the command `git --version`, if you see the git version in the output, it 
means that the installation was successful.

### Some useful options
To print the Git version that is currently installed:
```
$ git --version
```

To print the synopsis, and a list of the most commonly used commands:
```
$ git --help
```

If the option `--all` or `-a` is given then all the available commands are printed:
```
$ git --help --all
```

If a Git command (`config` in this case) is mentioned along with `--help`, it brings up the manual 
page for that command in your browser:
```
$ git --help config
```

## Configuring Git
Git uses a series of configuration files to determine non-default behavior that you may want. The 
first place Git looks for these values is in the system-wide `[path]/etc/gitconfig` file, which 
contains settings that are applied to every user on the system and all of their repositories. 
If you pass the option `--system` to git config, it reads and writes from this file specifically.

The next place Git looks is the `~/.gitconfig` (or `~/.config/git/config`) file, which is specific 
to each user of the system. You can make Git read and write to this file by passing the `--global` 
option.

Finally, Git looks for configuration values in the configuration file in the Git directory 
(`.git/config`) of whatever repository you’re currently using. These values are specific to that 
single repository, and represent passing the `--local` option to git config. If you don’t specify which 
level you want to work with, this is the default.

Each of these “levels” (system, global and local) overwrites values in the previous level, so values 
in `.git/config` (global config, which applies to a single user of the system) trump those in 
`[path]/etc/gitconfig` (system config, which applies to all users of the system), for instance.

### Configuration levels
In order to specify the git configuration for all the users of the system, use:
```
$ git config --system
```

In order to specify the git configuration for a specific user of the system, use:
```
$ git config --global
```

In order to specify the git configuration for the current git project that you're using, use:
```
$ git config --local
```

If no level is specified along with the `git config` command, then the default level is local. 
Therefore, using `git config --local` or `git config` would be the same.
   
### Setting the config properties
Below are a few example that show how a git property is set at any level.
To set the `user.name` property on the global level (inside `.git/config` file):
```
$ git config --global user.name={username}
```

To set the `user.email` property on the system level (inside `[path]/etc/gitconfig` file):
```
$ git config --system user.email={useremail}
```

### Listing the config properties
To see all the properties configured globally in Git, you can use the `–-list` option on the git config 
command. Adding the `-–show-origin` option will also output the gitconfig file’s location (based on 
what level is selected - local, global or system).

List all the properties present in the global gitconfig file and also output the location of the 
global gitconfig file on your machine:
```
$ git config --global --list --show-origin
```
   
### Updating the config properties
To add a new proxy, without altering any of the existing ones:
```
$ git config --global --add core.gitproxy '"proxy-command" for example.com'
```

To remove or unset a config property:
```
$ git config --global --unset core.editor
```

To remove or unset all the values of a property:
```
$ git config --global --unset-all core.editor
```

To edit the git config file via the default git editor:
```
$ git config --global --edit
```

## Concepts and terminology
### Local Repository
Every version control system tool provides a private workplace as a working copy. Developers make 
changes in their private workplace and after commit, these changes become a part of the repository. 
Git takes it one step further by providing them a private copy of the whole repository. Users can 
perform many operations with this repository such as add file, remove file, rename file, move file, 
commit changes, and many more.

### Working Directory and Staging Area or Index
The working directory is the place where files are checked out. Git does not track each and every 
modified file. Whenever you do commit an operation, Git looks for the files present in the staging 
area. Only those files present in the staging area are considered for commit and not all the 
modified files.

Let us see the basic workflow of Git.

Step 1 − You modify a file from the working directory.

Step 2 − You add these files to the staging area.

Step 3 − You perform commit operation that moves the files from the staging area. After push operation, 
it stores the changes permanently to the Git repository.

![Basic workflow of Git](./assets/working-directory.png)

### Blobs
Blob stands for Binary Large Object. Each version of a file is represented by blob. A blob holds 
the file data but does not contain any metadata about the file. It is a binary file, and in Git 
database, it is named as SHA1 hash of that file. In Git, files are not addressed by names. 
Everything is content-addressed.

### Trees
Tree is an object, which represents a directory. It holds blobs as well as other sub-directories. 
A tree is a binary file that stores references to blobs and trees which are also named as SHA1 hash 
of the tree object.

### Commits
Commit holds the current state of the repository. A commit is also named by SHA1 hash. You can consider 
a commit object as a node of the linked list. Every commit object has a pointer to the parent commit 
object. From a given commit, you can traverse back by looking at the parent pointer to view the 
history of the commit. If a commit has multiple parent commits, then that particular commit has been 
created by merging two branches.

### Branches
Branches are used to create another line of development. By default, Git has a master branch, which 
is same as trunk in Subversion. Usually, a branch is created to work on a new feature. Once the 
feature is completed, it is merged back with the master branch and we delete the branch. Every branch 
is referenced by HEAD, which points to the latest commit in the branch. Whenever you make a commit, 
HEAD is updated with the latest commit.

### Tags
Tag assigns a meaningful name with a specific version in the repository. Tags are very similar to 
branches, but the difference is that tags are immutable. It means, tag is a branch, which nobody 
intends to modify. Once a tag is created for a particular commit, even if you create a new commit, 
it will not be updated. Usually, developers create tags for product releases.

### Clone
Clone operation creates the instance of the repository. Clone operation not only checks out the 
working copy, but it also mirrors the complete repository. Users can perform many operations with 
this local repository. The only time networking gets involved is when the repository instances are 
being synchronized.

### Pull
Pull operation copies the changes from a remote repository instance to a local one. The pull operation 
is used for synchronization between two repository instances. This is same as the update operation in 
Subversion.

### Push
Push operation copies changes from a local repository instance to a remote one. This is used to store 
the changes permanently into the Git repository. This is same as the commit operation in Subversion.

### HEAD
HEAD is a pointer, which always points to the latest commit in the branch. Whenever you make a commit, 
HEAD is updated with the latest commit. The heads of the branches are stored in `.git/refs/heads/` 
directory.

### Revision
Revision represents the version of the source code. Revisions in Git are represented by commits. 
These commits are identified by SHA1 secure hashes.

### URL
URL represents the location of the Git repository. Git URL is stored in config file.

## Most widely used commands along with their use cases
This list contains some of the most widely used git commands, and is open for accepting contributions

### git add
The git add command adds a change in the working directory to the staging area. It tells Git that 
you want to include updates to a particular file in the next commit. Changes are not actually recorded 
until you run `git commit` after.

To add all changes of the mentioned file to the staging area:
```
$ git add <file>
```

To add all changes of the mentioned directory to the staging area:
```
$ git add <directory>
```

To add all the changes in all the files to the staging area:
```
$ git add .
```

### git apply
The changes present in a patch file (e.g. the output of git diff) can be applied to the working directory 
by using the git apply command. With the `--index` option the patch is also applied to the index, 
and with the `--cached` option the patch is only applied to the index.
```
$ git apply <patch-file>
```


### git branch
In Git, branches are effectively a pointer to a snapshot of your changes. When you want to add a new 
feature or fix a bug no matter how big or how small you spawn a new branch to encapsulate your changes.

List all the branches in your local repository (`git branch --list` can also be used to generate the same 
output):
```
$ git branch
```

Create a new branch locally. This does not check out the new branch:
```
$ git branch <branch>
```

Delete the specified local branch. This is a “safe” operation in that Git prevents you from deleting the 
branch if it has unmerged changes:
```
$ git branch -d <branch>
```

Force delete the specified local branch, even if it has unmerged changes.
```
$ git branch -D <branch>
```

Rename the current local branch:
```
$ git branch -m <new-branch>
```

List all the branches of the current repository both local and remote:
```
$ git branch -a
```

Deleting a remote branch:
```
$ git push origin --delete <branch>
```
or
```
$ git push origin :<branch>
```

### git checkout
The git checkout command operates upon three distinct entities: files, commits, and branches.

**Checking out branches:**

The git checkout command lets you navigate between the branches created by git branch. Checking out a 
branch updates the files in the working directory to match the version stored in that branch, and it 
tells Git to record all new commits on that branch.

Switch to an existing local branch:
```
$ git checkout <branch>
```

Create a new local branch and switch to it:
```
$ git checkout -b <new-branch> (The <new-branch> is based off of the current HEAD)
```

By default git checkout -b will base the new-branch off the current HEAD. If an optional additional 
parameter is passed, then the new-branch is based off of branch specified instead of the current HEAD.
```
$ git checkout -b ＜new-branch＞ ＜existing-branch＞ (The <new-branch> is based off of <existing-branch>)
```

Checking out to a remote branch (In order to checkout a remote branch you have to first fetch the contents of the branch):
```
$ git fetch --all
$ git checkout ＜remote-branch＞
```

**Checking out commits:**

To checkout a specific commit, you can use the git checkout command and provide the commit hash 
as a parameter:
```
$ git checkout <commit-hash> (e.g. git checkout 123abc123)
```

**Checking out files:**

The git checkout command when used along with a file discards all the file changes in the working 
directory:
```
$ git checkout <file-name>
$ git checkout . (discards all the changes in all the modified files in the working directory)
```

### git clone
git clone is a Git command line utility which is used to target an existing repository and create a 
clone, or copy of the target repository.
```
$ git clone <repo>
```

Cloning to a specific folder:
```
$ git clone <repo> <directory>
```

Cloning a specific tag:
```
$ git clone --branch <tag> <repo>
```

Cloning a specific branch:
```
$ git clone -b <branch> <repo>
```

### git commit
The git commit command captures a snapshot of the project's currently staged changes. Committed 
snapshots can be thought of as “safe” versions of a project—Git will never change them unless you 
explicitly ask it to. Prior to the execution of git commit, The git add command is used to promote or 
'stage' changes to the project that will be stored in a commit.

Commit the staged snapshot. This will launch a text editor prompting you for a commit message. 
After you’ve entered a message, save the file and close the editor to create the actual commit.
```
$ git commit
```

Commit with an inline message:
```
$ git commit -m "Initial commit"
```

Instead of creating a new commit, add/append staged changes to the previous commit:
```
$ git commit --amend
```

### git config
This command is used to display or set the config properties of git at various levels (system, global and local):

List all the config properties:
```
$ git config --global --list (lists all the global git config properties)
```

Display the value of a property:
```
$ git config --local user.name
```

Set the value of a property:
```
$ git config --system color.ui false
```

Add a value to an existing property without changing the previous values:
```
$ git config --global --add core.gitproxy '"proxy-command" for example.com'
```

To remove or unset a config property:
```
$ git config --global --unset core.editor
```

To remove or unset all the values of a property:
```
$ git config --global --unset-all core.editor
```

To edit the git config file via the default git editor:
```
$ git config --system --edit
```

### git describe
The command finds the most recent tag that is reachable from a commit. If the tag points to the commit, 
then only the tag is shown. Otherwise, it suffixes the tag name with the number of additional commits 
on top of the tagged object and the abbreviated object name of the most recent commit.

Describing a branch:
```
$ git describe <branch>
```
The above outputs the tag that the branch is based on along with the number of commits on top and an 
abbreviated object name for the commit at the end.

Describing a tag:
```
$ git describe <tag>
```

### git diff
git diff is a multi-use Git command that when executed runs a diff function on Git data sources. 
These data sources can be commits, branches, files and more.

Changes since last commit:
```
$ git diff
```

Comparing files between two different commits:
```
$ git diff <commit-hash-1> <commit-has-2>
```

Comparing two branches:
```
$ git diff <branch-1> <branch-2>
```

Comparing files from two branches:
```
$ git diff<branch-1> <branch-2> <file-path>
```

### git fetch
The git fetch command is used to pull the updates from remote-tracking branches. Additionally, we 
can get the updates that have been pushed to our remote branches to our local machines.

To fetch the remote repository:
```
$ git fetch <repository-url>
```

To fetch a specific branch:
```
$ git fetch <branch-url> <branch>
```

To fetch all the branches simultaneously:
```
$ git fetch --all
```

To synchronize the local repository:
```
$ git fetch origin
```

### git init
The git init command creates a new Git repository. It can be used to convert an existing, unversioned 
project to a Git repository or initialize a new, empty repository. Executing git init creates a .git 
subdirectory in the current working directory, which contains all of the necessary Git metadata for 
the new repository. This metadata includes subdirectories for objects, refs, and template files. A HEAD 
file is also created which points to the currently checked out commit.

To transform the current directory into a Git repository:
```
$ git init
```

Create an empty Git repository in the specified directory. Running this command will create a new 
subdirectory containing nothing but the .git subdirectory:
```
$ git init <directory>
```

Initialize an empty Git repository, but omit the working directory. Shared repositories should always 
be created with the --bare flag (see discussion below). Conventionally, repositories initialized with 
the --bare flag end in .git:
```
$ git init --bare <directory>
```

Initialize a new Git repository and copy all the .git files from the **template-directory** into the new 
repository:
```
$ git init <directory> --template=<template-directory>
```

Using the `--quiet` option, we can only print "critical level" messages, errors, and warnings. All other 
output is silenced:
```
$ git init --quiet
```

### git log
Git log is a utility tool to review and read a history of everything that happens to a repository.

The basic git log command will display the most recent commits and the status of the head:
```
$ git log
```

The `--oneline` option is used to display the output as one commit per line. It also shows the output 
in brief like the first seven characters of the commit SHA and the commit message:
```
$ git log --oneline
```

The `--stat` option displays the files that have been modified. It also shows the number of lines and a 
summary line of the total records that have been updated:
```
$ git log --stat
```

The `--patch` or `-p` option displays the files that have been modified. It also shows the location 
of the added, removed, and updated lines:
```
$ git log --patch
```
or
```
$ git log -p
```

Showing the git log as a graph using `--graph` option:
```
$ git log --graph
```

**Git log command to filter out commit history**
By amount:
```
$ git log -n (will print the log of "n" recent commits)
```

By date and time:
```
$ git log --after="yyyy-mm-dd"
```
or
```
$ git log --after="21 days ago"
```
or
```
$ git log --after="yyyy-mm-dd" --before="yyyy-mm-dd"
```

By Author:
```
$ git log --author=<author-name>
```

By commit message:
```
$ git log --grep=<commit-message>
```

By file:
```
$ git log -- <file-1> <file-2> (displays the commit logs of the files file-1 and file-2)
```

### git merge
The git merge command lets you take the independent lines of development created by git branch and 
integrate them into a single branch.

Note that all of the commands presented below merge into the current branch. The current branch will be 
updated to reflect the merge, but the target branch will be completely unaffected. Make sure that both 
the branches are up to date with the remote repository before doing a merge. If there are conflicts 
in the merge operation, then it results in a merge conflict.

To merge the specified commit to currently active branch:
```
$ git merge <commit>
```

To merge the speciified branch into the currently active branch:
```
$ git merge <branch-name> (<branch-name> is the branch whose changes are merged into the current branch)
```

### git mv
This command is used to move or rename a file or directory. The file or directory that has to be moved 
or renamed has to be present in the staging area.

To rename a file or directory:
```
$ git mv <file-1> <file-2> (to rename a file)
```
or
```
$ git mv <directory-1> <directory-2> (to rename a directory)
```

To move a file or directory:
```
$ git mv <source-file> <destination-file> (to move a file)
```
or
```
$ git mv <source-directory> <destination-directory> (to move a directory)
```

### git notes
This command adds, removes, or reads notes attached to objects, without touching the objects themselves.
By default, notes are saved to and read from `refs/notes/commits`, but this default can be overridden.

List notes of any object:
```
$ git notes list (lists notes of all the objects)
$ git notes list <object> ((lists notes of the object specified)
```

Add notes to an object:
```
$ git notes add -m "note contents" <object> (if object is not specified the default is taken as HEAD)
```
Note: If there is an already existing notes for an object, then the add command gives an error. If the 
`--force` or `-f` option is used along with the add command, it overrides the existing notes and creates a 
new one.

Append to the notes of an existing object (defaults to HEAD). Creates a new notes object if needed:
```
$ git notes append -m "note contents" <object> (if object is not specified the default is taken as HEAD)
```

Show notes of an object:
```
$ git notes show <object> (if object is not specified the default is taken as HEAD)
```

Edit notes of an object:
```
$ git notes edit <object> (if object is not specified the default is taken as HEAD)
```

Remove the notes for given object:
```
$ git notes remove <object> (if object is not specified the default is taken as HEAD)
```

Remove all the notes of all the objects:
```
$ git notes prune
```

### git pull
The `git pull` command is used to fetch and download content from a remote repository and immediately update 
the local repository to match that content. The git pull command first runs git fetch which downloads content 
from the specified remote repository. Then a git merge is executed to merge the remote content refs and heads 
into a new local merge commit.

Pull changes from a remote branch (Fetch the specified remote’s copy of the current branch and immediately 
merge it into the local copy):
```
$ git pull <remote>
```

Fetch the remote content but does not create a new merge commit:
```
$ git pull --no-commit <remote>
```

Pulling with rebase instead of merge:
```
$ git pull --rebase <remote>
```

Output the content being downloaded and the merge details during the pull:
```
$ git pull --verbose
```

### git push
The git push command is used to upload local repository content to a remote repository.

Push changes to the specified remote and branch:
```
$ git push <remote> <branch>
```

Push all of your local branches to the specified remote:
```
$ git push <remote> --all
```

Tags are not automatically pushed using the push command, in order to push local tags:
```
$ git push <remote> --tags
```

### git rebase
Rebasing is the process of moving or combining a sequence of commits to a new base commit.

Rebase the current branch onto the specified base, which can be any kind of commit reference(for example an ID, 
a branch name, a tag, or a relative reference to HEAD):
```
$ git rebase <base>
```

### git remote
The `git remote` command manages the set of remotes that you are tracking with your local repository.

List the current remotes associated with the local repository:
```
$ git remote -v
```

Adding a remote:
```
$ git remote add <name> <url>
```

Removing a remote:
```
$ git remote remove <name>
```

### git replace
The replace command lets you specify an object in Git and say "every time you refer to this object, pretend it’s 
a different object".
```
$ git replace <object> <replacement>
```

### git reset
### git restore
### git revert
### git rm
### git show
### git stash
### git status
### git switch
### git tag

## Miscellaneous
### The `.gitignore` file
Git sees every file in your working copy as one of three things:

 - tracked - a file which has been previously staged or committed
 - untracked - a file which has not been staged or committed or
 - ignored - a file which Git has been explicitly told to ignore.

If you don't want to commit some files/folders to Git, and want Git to completely ignore them, then 
you can have a file called **.gitignore** created at the root of your repository and add file/folder 
patterns to ignore. All the files/folders that match the patterns mentioned in the **.gitignore** 
file are completely ignored by Git. Refer this link: 
[https://linuxize.com/post/gitignore-ignoring-files-in-git](https://linuxize.com/post/gitignore-ignoring-files-in-git)
to know more about patterns that can be used in the **.gitignore** file.

### `git fetch` vs `git pull`
`git fetch` really only downloads new data from a remote repository - but it doesn't integrate any of this 
new data into your working files. Fetch is great for getting a fresh view on all the things that happened 
in a remote repository. Due to it's "harmless" nature, fetch will never manipulate, destroy, or 
screw up anything.

`git pull` in contrast, is used with a different goal in mind: to update your current HEAD branch with 
the latest changes from the remote server. This means that pull not only downloads new data, it also 
directly integrates it into your current working copy files. This has a couple of consequences:
 - Since `git pull` tries to merge remote changes with your local ones, a so-called "merge conflict" 
  can occur.
 - Like for many other actions, it's highly recommended to start a "git pull" only with a clean 
   working copy. This means that you should not have any uncommitted local changes before you pull.

## References
 - [https://git-scm.com/docs](https://git-scm.com/docs)
 - [https://www.atlassian.com/git/tutorials](https://www.atlassian.com/git/tutorials)
 - [https://github.com/git-guides](https://github.com/git-guides)
 - [https://www.tutorialspoint.com/git](https://www.tutorialspoint.com/git/git_basic_concepts.htm)
 - [https://linuxize.com/post/gitignore-ignoring-files-in-git](https://linuxize.com/post/gitignore-ignoring-files-in-git)
 - [https://www.git-tower.com/learn/git/faq](https://www.git-tower.com/learn/git/faq)
 - [https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/The-global-Git-config-files-key-settings-and-usages](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/The-global-Git-config-files-key-settings-and-usages)