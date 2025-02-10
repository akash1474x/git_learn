# git_learn

GIT

### Rename Branch
`git branch -m new_name`

### Performing Amend
- `git commit --amend`
- `git commit --amend -m "an updated commit message"`
- `git commit --amend --no-edit`

The `--no-edit` flag will allow you to make the amendment to your commit without changing its commit message. 


### Rebase
![Rebase Image](https://www.themoderncoder.com/uploads/git-rebase-graphic.png)
- Takes all of the commits on your feature branch and move them on top of the master commits.
- Behind the scenes, git deletes the feature branch commits and duplicating them as new commits on top of the master branch.
- Gives a nice clean tree with all your commits laid out nicely in a row, like a timeline. Easy to trace.
Steps:
- git pull (on master) - to get all the latest changes
- git checkout -b my_cool_feature
- git add .
- git commit -m 'This is a new commit, yay!'

Note: while I’m developing it’s likely that my fellow developers will have shipped some of their own changes to remote master. so we will goto master and pull all the changes made on master branch

- git checkout master
- git pull

re-anchor my branch against the latest changes I just pulled from remote master. Additionally at this point, Git will let me know if I have any conflicts and I can take care of them on my branch
- git checkout my_cool_feature
- git rebase master

Now that my feature branch doesn’t have any conflicts, I can switch back to my master branch and place my changes onto master.
- git checkout master
- git rebase my_cool_feature

Since I synced with remote master before doing the rebase, I should be able to push my changes up to remote master without issues.
- git push


### Patch
In Git, a patch is a file that contains the differences between two versions of a file or set of files. It represents changes made in your code (such as added, modified, or deleted lines) and can be applied to other branches or repositories.
`git diff --word-diff` - gives diff word by word
`git diff --stat` - gives summary of diff

#### For Unstaged changes
`git diff > local.patch` - storing the diff in a local.patch file
#### For Staged changes
`git diff --cached > local.patch` - storing the diff in a local.patch file
#### Between commits
`git diff chash1 chash2 > local.patch` - storing the diff in a local.patch file
#### Applying patch
`git apply > local.patch` - apply the diff from local.patch file

#### To see the last commit changes:
git show
#### To create patch file of last committed changes:
git show --full-index > /Desktop/commited_changes.patch


## Reverting changes:
-- If you want to remove the changes from unstaged area, use below command:
`git checkout file_name` OR `git checkout .` (to remove all changes)
-- If we want to remove the changes from staged area, use below command:
`git reset .` (will move the staged changes to unstaged area)
`git reset --hard` (will delete all staged changes)
-- If you want to remove the committed changes, use below command:
`git reset --soft HEAD^` : this will remove the changes, but will keep the changes in working area
`git reset --hard HEAD^` : this will remove the all changes and will not keep any of these changes
in working area
