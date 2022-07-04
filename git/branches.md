# Git branches

## Push a local branch to another remote repo ([Ref](https://stackoverflow.com/a/5181968))

This is because I don't have permission to push it to the original remote repo. 

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

---------------

## Add another remote URL

```
git remote add other https://github.com/shashankNREL/amr-wind.git
git fetch other
git cherry-pick 1b6b2121f2843381c5ee76a20dee999f26901fb1
```

---------------------


## A remote branche vs. A branch that exists in a remote repo ([Ref](https://stackoverflow.com/questions/35941566/git-says-remote-ref-does-not-exist-when-i-delete-remote-branch))

Usually:
```
git branch -d <local_branch>              # to delete a local branch
git push origin --delete <remote_branch>  # to delete a remote branch
```

The command `git branch -a` shows *remote branches that exist in your local repository*. This may sound a bit confusing but to understand it, you have to understand that there is a difference between *a remote branch*, and *a branch that exists in a remote repository*. Remote branches are local branches that map to branches of the remote repository. So the set of remote branches represent the state of the remote repository.

The usual way to update the list of remote branches is to use `git fetch`. This automatically gets an updated list of branches from the remote and sets up remote branches in the local repository, also fetching any commit objects you may be missing. However, by default, git fetch does not remove remote branches that no longer have a counterpart branch on the remote. In order to do that, you explicitly need to prune the list of remote branches: `git fetch --prune`. This will automatically get rid of remote branches that no longer exist on the remote. Afterwards, `git branch -r` will show you an updated list of branches that really exist on the remote, and those you can delete using `git push`.

That being said, in order to use `git push --delete`, you need to specify the name of the branch on the remote repository; not the name of your remote branch. So to delete the branch `test` (represented by your remote branch `origin/test`), you would use `git push origin --delete test`.

