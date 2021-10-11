# Git for Noobs

This documentation will help you get started with Git and also contains the most widely used git commands.

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
- [References](#references)


## What is Git?
Version control, also known as source control, is the practice of tracking and managing changes to 
software code. Version control systems are software tools that help software teams manage changes to 
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
`git --version` prints the Git version that is currently installed.

`git --help` prints the synopsis, and a list of the most commonly used commands. 

`git --help -all` If the option --all or -a is given then all the available commands are printed. 

`git --help config` If a Git command (`config` in this case) is mentioned, this option will bring up the manual page for 
that command in your browser.

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
 - `git config --system` is used for specifying the git configuration for all the users of the system.
 - `git config --global` is used for specifying the git configuration for a specific user of the system.
 - `git config --local` or `git config` is used for specifying the git configuration for the current 
   git project that you're using.
   
### Setting the config properties
Below are a few example that show how a git property is set at any level.
 - `git config --global user.name={username}` sets the `user.name` property on the global level 
   (inside `.git/config` file).
 - `git config --system user.email={useremail}` sets the `user.email` property on the system level 
   (inside `[path]/etc/gitconfig` file).

### Listing the config properties
To see all the properties configured globally in Git, you can use the `–-list` option on the git config 
command. Adding the `-–show-origin` option will also output the .gitconfig file’s location (based on 
what level is selected - local, global or system).

`git config --global --list --show-origin` lists all the properties present in the global gitconfig 
file and also outputs the location of the global gitconfig file on your machine.
   
### Updating the config properties
`git config --global --add core.gitproxy '"proxy-command" for example.com'` to add a new proxy, 
without altering any of the existing ones.

`git config --global --unset core.editor` to remove or unset a config property.

`git config --global --edit` to edit the git config file via the default git editor.

## Concepts and terminology


## Most widely used commands along with their use cases
This list contains some of the most widely used git commands, and is open for accepting contributions

### git add
### git apply
### git branch
### git checkout
### git clone
### git commit
### git config
### git describe
### git diff
### git fetch
### git init
### git log
### git merge
### git mv
### git notes
### git pull
### git push
### git rebase
### git remote
### git replace
### git reset
### git restore
### git revert
### git rm
### git show
### git stash
### git status
### git switch
### git tag

## References
 - [https://git-scm.com/docs](https://git-scm.com/docs)
 - [https://www.atlassian.com/git/tutorials](https://www.atlassian.com/git/tutorials)
 - [https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/The-global-Git-config-files-key-settings-and-usages](https://www.theserverside.com/blog/Coffee-Talk-Java-News-Stories-and-Opinions/The-global-Git-config-files-key-settings-and-usages)