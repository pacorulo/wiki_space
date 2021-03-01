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
