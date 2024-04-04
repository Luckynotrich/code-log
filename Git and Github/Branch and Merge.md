[Basic Branching and Merging](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging)
A download by the above name is in this directory
List all branches
```bash
git branch
```

Switch to a different branch
```bash
git checkout branch-name
```

Creating a new branch and switching to it.
```bash
$ git checkout -b iss53
Switched to a new branch "iss53"
```

This is shorthand for:

```bash
$ git branch iss53
$ git checkout iss53
```

```bash
git commit -a -m 'Finish the new footer [issue 53]
```
For now, let’s assume you’ve committed all your changes, so you can switch back to your `master` branch:

```bash
$ git checkout master
Switched to branch 'master'
```
Next, you have a hot fix to make. Let’s create a `hotfix` branch on which to work until it’s completed:

```bash
$ git checkout -b hotfix
Switched to a new branch 'hotfix'
$ vim index.html
$ git commit -a -m 'Fix broken email address'
[hotfix 1fb7853] Fix broken email address
 1 file changed, 2 insertions(+)
```
You can run your tests, make sure the hot fix is what you want, and finally merge the `hotfix` branch back into your `master` branch to deploy to production. You do this with the `git merge` command:

```bash
$ git checkout master
$ git merge hotfix
Updating f42c576..3a0874c
Fast-forward
 index.html | 2 ++
 1 file changed, 2 insertions(+)
```

After your super-important fix is deployed, you’re ready to switch back to the work you were doing before you were interrupted. However, first you’ll delete the `hotfix` branch, because you no longer need it — the `master` branch points at the same place. You can delete it with the `-d` option to `git branch`:

```bash
$ git branch -d hotfix
Deleted branch hotfix (3a0874c).
```

To switch back to your work-in-progress branch on issue #53 and continue working on it.

```bash
$ git checkout iss53
```
### Basic Merging

Suppose you’ve decided that your issue #53 work is complete and ready to be merged into your `master` branch. In order to do that, you’ll merge your `iss53` branch into `master`, much like you merged your `hotfix` branch earlier. All you have to do is check out the branch you wish to merge into and then run the `git merge` command:

```bash
$ git checkout master
Switched to branch 'master'
$ git merge iss53
Merge made by the 'recursive' strategy.
index.html |    1 +
1 file changed, 1 insertion(+)
```
Now that your work is merged in, you have no further need for the `iss53` branch. You can close the issue in your issue-tracking system, and delete the branch:

```bash
$ git branch -d iss53
```
