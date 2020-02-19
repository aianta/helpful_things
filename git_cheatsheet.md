# Git Cheat Sheet

**Command syntax/parameters in `[]` are optional**

## Finding information about the current situation

`git status`  
-   [Doc Ref](https://git-scm.com/docs/git-status)

Displays:
 1.  Paths that have differences between the index file and the current HEAD commit
 2.  Paths that have differences between the working tree and the index file
 3.  Paths in the working tree that are not tracked by Git (and are not ignored by gitignore[5]).
 
  The first are what you would commit by running git commit; the second and third are what you could commit by running git add before running git commit.

`git branch -v` 
- [Doc Ref](https://git-scm.com/docs/git-branch)

Lists the branches in the local repository alongside the sha1 hash (unique identifier given to each commit) and message of the latest commit on that branch.

`git branch -vv`
- [Doc Ref](https://git-scm.com/docs/git-branch)

Like `git branch -v` except it also lists what *remote* branch the local branches are tracking. 

Example
```
* Breezy-Server           bc36b63 reporting death for each run
  lua-interface-addon-api 712c9d2 [origin/lua-interface-addon-api: behind 8] basic wrapper working, though still some details to implement
  master                  c40b209 [origin/master] Deleted python_servers/embedded/.gitkeep, python_servers/standalone/.gitkeep, python_servers/.gitkeep files
  python-server           b8d4479 [origin/python-server: gone] update message
```
The `*` marks the branch we currently have checked out. From the above output we can tell that the local branch `lua-interface-addon-api` is 'tracking' the remote branch `origin/lua-interface-addon-api`. 

Note: Remote branches usually have the name of the remote in their name following this syntax `<remote>/<branch>`.

`git log` 
- [Doc Ref](https://git-scm.com/docs/git-log)

Prints a list of commits, their sha1 hash (unique identifier), author, date and message in reverse chronological order (latest commit is at the top). 

Example:
```
commit bc36b635942f1d7e9b79eb70b694d03ea9ae610a (HEAD -> Breezy-Server, origin/Breezy-Server)
Author: Alex Ianta <aianta@dal.ca>
Date:   Tue Feb 18 16:42:57 2020 -0400

    reporting death for each run

commit e6d7b2af90e0bac4430c385bd0f3749bbd9c87e4
Author: Alex Ianta <aianta@dal.ca>
Date:   Mon Feb 17 01:19:26 2020 -0400

    changed vertx-server to breezy server

commit 4ab5f7e385ad17572adcfb00b646fe665062d309
Author: Alex Ianta <aianta@dal.ca>
Date:   Mon Feb 17 01:14:59 2020 -0400

    added kill counts to run responses

...
```
`git diff [<path>]`
- [Doc Ref](https://git-scm.com/docs/git-diff)

Prints the differences within files since the last commit. If a path parameter is supplied, only prints the differences of the file on that path. 

Note: Can be used to comapre differences between 2 arbitrary files by doing `git diff --no-index <path to file1> <path to file2>`

`git remote -v` 
- [Doc Ref](https://git-scm.com/docs/git-remote)

Prints a list of remotes currently configured on to this repository including their urls.
