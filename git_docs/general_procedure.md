Create a new branch:
```
git checkout -b branch_name
```
Add new files:
```
git add [--all|file_name]
```
Commit changes:
```
git commit [-m message]
```
> If you need to change a commit message already commited:
	```
	git commit --amend
	```
Push new branch to git repo:
```
git push --set-upstream origin branch_name

or

git push origin branch_name
```
To remove a no more needed file from the remote branch:
```
git rm file_name
git commit -m "Message"
git push origin branch_name
```
If we need to remove an old branch we consider no more needed:
* Delete branch locally
	```
	git branch -d localBranchName
	```
The -d option will delete the branch only if it has already been pushed and merged with the remote branch. Use -D instead if you want to force the branch to be deleted, even if it hasn't been pushed or merged yet.
* Delete branch remotely
	```
	git push origin --delete remoteBranchName
	```
	but there is a shorter command to remove the remote branch:
	```
	git push origin :branch_name
	```
