Rename git branch
1. Rename branch locally
git branch -m old_branch new_branch

2. Delete the old branch
git push origin :old_branch

3. Push the new branch, set local branch to track the new remote
git push --set-upstream origin new_branch