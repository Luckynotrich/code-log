# [How to Undo a Git Add](https://www.freecodecamp.org/news/how-to-undo-a-git-add/)
To undo `git add` before a commit, run `git reset <file>` or `git reset` to unstage all changes.

In older versions of Git, the commands were `git reset HEAD <file>` and `git reset HEAD` respectively. This was changed in Git 1.8.2

this undoes the last commit
```
git reset --soft HEAD~1
```