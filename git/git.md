
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




### Push a local branch to another remote repo (because I don't have permission to push it to the original remote repo)

Ref: https://stackoverflow.com/a/5181968

1. On github.com, create a new, empty repo 
2. `git remote rename origin upstream`

```

λ git remote -v
origin  git@github.com:username/forkedRepo.git (fetch)
origin  git@github.com:username/forkedRepo.git (push)
upstream        git@github.com:projname/Repo.git (fetch)
upstream        git@github.com:projname/Repo.git (push)
```

4. `git remote add origin URL_TO_THE_NEW_EMPTY_GITHUB_REPO`
5. `git push origin master` or replace `master` with the branch name


### Add another remote URL
```
git remote add other https://github.com/shashankNREL/amr-wind.git
git fetch other
git cherry-pick 1b6b2121f2843381c5ee76a20dee999f26901fb1
```

### A remote branche vs. A branch that exists in a remote repo
[Ref](https://stackoverflow.com/questions/35941566/git-says-remote-ref-does-not-exist-when-i-delete-remote-branch)

Usually:
```
git branch -d <local_branch>              # to delete a local branch
git push origin --delete <remote_branch>  # to delete a remote branch
```

The command `git branch -a` shows *remote branches that exist in your local repository*. This may sound a bit confusing but to understand it, you have to understand that there is a difference between *a remote branch*, and *a branch that exists in a remote repository*. Remote branches are local branches that map to branches of the remote repository. So the set of remote branches represent the state of the remote repository.

The usual way to update the list of remote branches is to use `git fetch`. This automatically gets an updated list of branches from the remote and sets up remote branches in the local repository, also fetching any commit objects you may be missing. However, by default, git fetch does not remove remote branches that no longer have a counterpart branch on the remote. In order to do that, you explicitly need to prune the list of remote branches: `git fetch --prune`. This will automatically get rid of remote branches that no longer exist on the remote. Afterwards, `git branch -r` will show you an updated list of branches that really exist on the remote, and those you can delete using `git push`.

That being said, in order to use `git push --delete`, you need to specify the name of the branch on the remote repository; not the name of your remote branch. So to delete the branch `test` (represented by your remote branch `origin/test`), you would use `git push origin --delete test`.
