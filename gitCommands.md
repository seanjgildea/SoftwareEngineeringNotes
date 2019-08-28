
# Git Commands

## push branch to remote
git push origin <branch_name>

## show latest commits on branch
git log

## show files changed on commit
git log -p

## push modifications for current commit without pushing new commit
git commit --amend --no-edit

## remove last local commit but save modifications to be re-committed
git reset --soft HEAD~1

## remove remote branch
git push --delete origin <branch_name>
