Git Commands
============

### Content

- [Getting & Creating Projects](#Getting--Creating-Projects)
- [Basic Snapshotting](#Basic-Snapshotting)
- [Branching & Merging](#Branching--Merging)
- [Submodules](#Submodules)
- [How to merge a specific commit](#How-to-merge-a-specific-commit)
- [Sharing & Updating Projects](#Sharing--Updating-Projects)
- [Tags](#Tags)
- [Inspection & Comparison](#Inspection--Comparison)
- [Removing & Ignoring In Version Control](#Removing--Ignoring-In-Version-Control)
- [Gitflow](#Gitflow)
- [Vim](#Vim)


## <br/> Translated Versions
- [Versão em português](READMEpt.md)

___

_A list of my commonly used Git commands_

*If you are interested in my Git aliases, have a look at my `.bash_profile`, found here: https://github.com/joshnh/bash_profile/blob/master/.bash_profile*

--


## <br/> Getting & Creating Projects

| Command | Description |
| ------- | ----------- |
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Basic Snapshotting

| Command | Description |
| ------- | ----------- |
| `git status` | Check status |
| `git add [file-name.txt]` | Add a file to the staging area |
| `git add -A` | Add all new and changed files to the staging area |
| `git commit -m "[commit message]"` | Commit changes |
| `git rm -r [file-name.txt]` | Remove a file (or folder) |

To stop tracking a file you need to remove it from the index. This can be achieved with this command.
`git rm --cached <file>`

If you want to remove a whole folder, you need to remove all files in it recursively.
`git rm -r --cached <folder>`

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Branching & Merging

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

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Submodules

| Command | Description | Example |
| ------- | ----------- | ------- |
| `git submodule add <repo> <path_to_submodule_content>` | Adding submodule | `git submodule add https://github.com/p1eXu5/Result.git .submodules/p1eXu5.Result` |
| `git submodule update --init --recursive` | To restore |

#### To remove a submodule you need to:

- Delete the relevant section from the .gitmodules file.
- Stage the .gitmodules changes git add .gitmodules
- Delete the relevant section from .git/config.
- Run git rm --cached path_to_submodule (no trailing slash).
- Run rm -rf .git/modules/path_to_submodule (no trailing slash).
- Commit git commit -m "Removed submodule <name>"
- Delete the now untracked submodule files rm -rf path_to_submodule

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## How to merge a specific commit

`git checkout <source_branch>` <br/>
`git log`  // or (git reflog) <br/>
-- copy branch commit_hash <br/>
`git checkout <target_branch>` <br/>
`git cherry-pick <commit_hash>` <br/>

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Sharing & Updating Projects

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

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Tags

| Command | Description | Example |
| ------- | ----------- | ------- |
| `git tag` | View tags | |
| `git show-ref --tags` | View tag refs | |
| `git ls-remote --tags` | View remote tags | |
| `git tag -a <tag_name> -m <commit>` | Add annotated tag | `$ git tag -a v0.0.002 -m "get drugs through OnExpanded"` |
| `git fetch [--all] --tags` | To fetch tags from your remote repository | |
| `git checkout tags/<tag_name> -b <new_branch_name>` | To checkout to tag from any branch | `git checkout tags/v1.0 -b v1.0-branch` |
| `git log --oneline --graph` | To inspect. Make sure that the HEAD pointer (the latest commit) is pointing to your annotated tag. | |
| ```tag=$(git describe --tags `git rev-list --tags --max-count=1`)``` | Retrieve the latest tag available | `$ git fetch --tags` <br/> ```$ tag=$(git describe --tags `git rev-list --tags --max-count=1`)``` <br/> `$ echo $tag` <br/> `$ git checkout $tag -b latest` <br/> `$ git log --oneline --graph` |
| `git push origin <tag_name>` | Push tag to remote | `$ git push origin v0.0.002` |
| `git push origin --tags` | To push all of the tags to the remote repo | |
| `git push -f origin <tag_name>` | Update the remote tag | | 
| `git tag -a -f <tag_name> <commit_hash>` | Update tag to commit | `$ git tag -a -f v0.0.002 09ffef0a96b107fccf955a6bb74a14493dc06810` |
| `git tag -fa <tagname>` | Update tag to the recent commit | |
| `git push origin :refs/tags/<tag_name>` | Delete the tag on any remote before you push | |
| `git push --follow-tags` | Push commits and tags in one command | |

There are 2 types of tags - lightweight and annotated. Lightweight tags are merely refs that point to some object whereas annotated tags are a separate git object by themselves, and store a lot more information like author, committer, a commit message, etc. [link]()


    `<rev>^{}, e.g. v0.99.8^{}`

A suffix ^ followed by an empty brace pair means the object could be a tag, and dereference the tag recursively until a non-tag object is found. (which I'm guesssing is storing the commit information when you created the tag.(c))
[link 1](https://mirrors.edge.kernel.org/pub/software/scm/git/docs/gitrevisions.html#_specifying_revisions)
[link 2](https://devconnected.com/how-to-checkout-git-tags/)

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Inspection & Comparison

| Command | Description |
| ------- | ----------- |
| `git log` | View changes |
| `git log --summary` | View changes (detailed) |
| `git log --oneline` | View changes (briefly) |
| `git diff [source branch] [target branch]` | Preview changes before merging |
| `gitk [fileName]` | View file commits |
| `gitk --follow [fileName]` | View file commits with to follow filename past renames |

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Removing & Ignoring In Version Control

| Command           | Description              | Example |
| ----------------- | ------------------------ | --------|
| `git rm --cached` | Remove a file from index | $ git rm --cached ./src/MyproofCore.AuthServer/Properties/PublishProfiles/FolderProfile.pubxml |
| `git update-index --assume-unchanged <file>` | | |
| `git update-index --no-assume-unchanged <file>` | | |

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Gitflow

| Command | Description |
| ------- | ----------- |
| `git flow feature start <feature_branch>` | Creating a feature branch |
| `git flow feature finish <feature_branch>` | Finishing a feature branch |
| `git flow hotfix start <hotfix_branch>` | Creating a hotfix branch |
| `git flow hotfix finish <hotfix_branch>` | Finishing a hotfix branch |
| `git branch -d feature/your-feature-name-here` | Delete unfinished hotfix or feature |

<br/><div style="text-align: right"> [Content](#git-commands) </div>


## Vim

To exit Vim:

1. If you are in edit mode, first press the <Esc> key.
2. Then enter :wq + <Enter> to save and exit.

<br/><div style="text-align: right"> [Content](#git-commands) </div>