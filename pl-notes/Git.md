* Check configurations
```
$ git config -l
```

- Git log patch: show all the patch
```
$ git log -p
```
- Git get exaclty 3 commit logs
```
$ git log -3
```
- Git show info about an id
```
$ git show [id]
```
- Git show stat 
```
$ git log --stat
```
- Git check the changes done unstaged
```
$ git diff
```
- Git check the changes done staged
```
$ git diff --staged
```
- Git remove files
```
$ git rm [filename]
```
- Git move files
```
$ git mv [filename] [newfilename]
```

- Git unstage file mistakenly staged
```
$ git reset HEAD file_name
```
- Git ammend i.e. overwrite previous commit
```
$ git commit --ammend
```
> NOTE: stage the changes first

- Git revert: Creates the new commit which undo the recent commit. Inverse of commit tho the history remains.
```
$ git revert HEAD
```
- Git revert: Revert to pervious commit
```
$ git revert [id]
```

- Git list branch
```
$ git branch
```
- Git create branch
```
$ git branch [branch_name]
$ git checkout -b [branch_name]
```
- Git delete branch
```
$ git branch -d [branch_name]
```

>Git uses two algorithm to merge:
>- fast-forward
>- Three-way

- Git merge
```
$ git merge [branch_name]
```
- Git check log | graph form after merge
```
$ git log --graph --oneline
```
- Git abort merge
```
$ git merger --abort
```

#### Git remote
- Git remote verbose: shows all the git remote links
```
$ git remote -v
```
- Git remote show origin: get info about remotes
```
$ git remote show origin
```