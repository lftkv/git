Merge:

```
git checkout <mainbranch>
git merge <branch to merge the mainbranch in>
(build the branch)
git merge <mainbranch>
git push
```

Delete old branch:

```
remote:
git push origin --delete <branch to delete>

local:
git branch -D <branch to delete>
```
