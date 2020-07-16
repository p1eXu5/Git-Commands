Git Commands
============

## Translated Versions
- [Versão em português](READMEpt.md)

___

_A list of my commonly used Git commands_

*If you are interested in my Git aliases, have a look at my `.bash_profile`, found here: https://github.com/joshnh/bash_profile/blob/master/.bash_profile*

--

### Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

### Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

### Branching & Merging

| Command | Description |
| ------- | ----------- |
| `git branch` | List branches (the asterisk denotes the current branch) |
| `git branch -a` | List all branches (local and remote) |
| `git branch [branch name]` | Create a new branch |
| `git branch -d [branch name]` | Delete a branch |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git checkout -b [branch name]` | Create a new branch and switch to it |
| `git checkout -b [branch name] origin/[branch name]` | Clone a remote branch and switch to it |
| `git checkout -t origin/[branch name]` | Clone a remote branch, take it name and switch to it |
| `git branch -m [old branch name] [new branch name]` | Rename a local branch |
| `git checkout [branch name]` | Switch to a branch |
| `git checkout -` | Switch to the branch last checked out |
| `git checkout -- [file-name.txt]` | Discard changes to a file |
| `git merge [branch name]` | Merge a branch into the active branch |
| `git merge [source branch] [target branch]` | Merge a branch into a target branch |
| `git stash` | Stash changes in a dirty working directory |
| `git stash clear` | Remove all stashed entries |

### Submodules
| Command | Description | Example |
| ------- | ----------- | ------- |
| `git submodule add [repo] [path]` | Add submodule | $ git submodule add https://github.com/p1eXu5/p1eXu5.Wpf.git ./submodules/p1eXu5.Wpf |
| `git submodule update --init --recursive` | Update submodule | |

### How to merge a specific commit

`git checkout <source_branch>` <br/>
`git log`  // or (git reflog) <br/>
-- copy branch commit_hash <br/>
`git checkout <target_branch>` <br/>
`git cherry-pick <commit_hash>` <br/>


### Sharing & Updating Projects

| Command | Description |
| ------- | ----------- |
| `git push origin [branch name]` | Push a branch to your remote repository |
| `git push -u origin [branch name]` | Push changes to remote repository (and remember the branch) |
| `git push` | Push changes to remote repository (remembered branch) |
| `git push origin --delete [branch name]` | Delete a remote branch |
| `git pull` | Update local repository to the newest commit |
| `git pull origin [branch name]` | Pull changes from remote repository |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Set a repository's origin branch to SSH |

### Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging |
| `gitk [fileName]` | View file commits |
| `gitk --follow [fileName]` | View file commits with to follow filename past renames |

### Service

| Command           | Description              | Example |
| ----------------- | ------------------------ | --------|
| `git rm --cached` | Remove a file from index | $ git rm --cached ./src/MyproofCore.AuthServer/Properties/PublishProfiles/FolderProfile.pubxml


### Gitflow

| Command | Description |
| ------- | ----------- |
| `git flow feature start <feature_branch>` | Creating a feature branch |
| `git flow feature finish <feature_branch>` | Finishing a feature branch |
| `git flow hotfix start <hotfix_branch>` | Creating a hotfix branch |
| `git flow hotfix finish <hotfix_branch>` | Finishing a hotfix branch |

### Vim

To exit Vim:

1. If you are in edit mode, first press the <Esc> key.
2. Then enter :wq + <Enter> to save and exit.

