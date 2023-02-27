* diff: Show difference between files
```terminal
$ diff old_file new_file
$ diff -u old_file new_file
```
	- '-u' means unified

* patch: Apply diff to the file
```terminal
$ diff old_file new_file > changes.diff
$ patch old_file < changes.diff
```

* Shread: override a file such that the file becomes unrecoverable
```terminal
$ shread file
```

