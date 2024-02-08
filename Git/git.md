## General
```bash
# See all changed files
git status 
```

## Branch commands
```bash
# create a new branch
git checkot -b branch-name
```

```bash
# switch to another branch
git checkout branch-name
```

## Merge commands
```bash
# Merge 
# you need to go to master branch, and pull the changes
git checkout master
git pull origin master
# then you merge the changes into the 'master' branch

git merge --squash new-branch
# the squash option is used to pack all changes into a single commit
# if you do this you also need to git add and add git commit message.

# otherwise you just simply git merge and all commits done
# in the new branch will be integrated into master.
git merge new-branch

#then you finally push the changes to the master branch
git push origin master
```

## Reset/Undo changes
```bash
# reset local changes
git reset --hard origin/master
git clean -f
# git clean has other parameters
# -f to remove untracked files
# -df to remove untracked files and directories
# -xdf to remove untracked or ignored files
git pull origin master
```

```bash
# return to old commit 
git push -f origin $old_commit_id:master
```
