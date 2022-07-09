# Basic Git commands

## diff

`git diff      file.txt` (1)

`git diff HEAD file.txt` (2)=(1), compare working dir version (unstaged) with the repo version

`git diff --cached file.txt` (3)

`git diff --staged file.txt` (4)=(3), compare staged changes with the repo version

`git log --pretty=oneline` 

`git diff hash1 hash2` (5) compare 2 commits

`git diff branch1 branch2` (6)

`git diff branch1..branch2` (7)=(6), the ".." is an operator

`git diff branch1...branch2` (8), compare branch0 with branch2, where branch0 is the common ancestor commit for 1 and 2

`git diff branch1 branch2 filet.txt` (9), compare a single file between 2 branches

---------------------

## stash

- Both committed changes and uncommited changes go to a stash.
- Stash is local (not part of the push).

`git stash` (10)

`git stash pop` (11), move stashed changes to the working dir

`git stash apply` (12), copy the stashed changes to the working dir (so the stashed changes may be applied to different branches)

By default, git doesn't stash changes made to untracked or ignored files.

`git stash -u` (13)

`git stash --included-untracked` (14)=(13)

`git stash -a` (15)

`git stash --all` (16)=(15), add ignored+unstaged

`git stash list` (17), multiple stashes are allowed, this shows a list of them. `WIP`=Work in progress.

`git stash save "add message"` (18) add annotations to a stash

`git stash pop stash@{2}` (19)~(11), `pop` by default uses the most recent stash, and one can specify exactly which to use

`git stash show` (20)

`git stash show -p` (21)

`git stash branch <new_branch_name> stash@{1}` (22) turn a stash into a branch

`git stash drop stash@{1}` (23)

`git stash clear` (24) delete all stashes

---------------------

## Replacing LF with CRLF
```
git config --global core.safecrlf false
```