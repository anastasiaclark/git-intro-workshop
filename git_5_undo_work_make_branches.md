# Undo work (Checkout, Revert and Reset) and create branches

## Use cases

| Command        | Scope              | Common use cases |    
|----------------|--------------------|------------------|
| `git checkout` | Commit-level	      | Switch between branches or inspect old snapshots |
| `git checkout` | File-level	        | Discard changes in the working directory |
|                |                    |                |
| `git revert`	  | Commit-level	      | Undo commits in a public branch |
| `git revert`	  | File-level	        | (N/A) |
|                |                    |                |
| `git reset`  *  | Commit-level       | Discard commits in a private branch or throw away uncommited changes  |  
| `git reset`  *  | File-level	        | Unstage a file |
* use `git revert` over `git reset`; it is better practice


## Log of Commits
#### View log of Git
```console
git log

# view formatted log
git log --pretty=format:"%h : %an : %ar : %s" -3
```

#### View last 2 commits
```console
git log -2
```  

>my example  

```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git log
commit e0c2eb23f8fe760c7b1847df29f8b28d8ae22104
Author: anastasiaclark <anastasiapotupalova@gmail.com>
Date:   Sun May 13 12:46:03 2018 -0400

    created myfile.py

commit d71fc91471339fd5dd2d80e73d332cc9d3b3d93f
Author: Anastasia Clark <anastasiapotupalova@gmail.com>
Date:   Sun May 13 12:08:34 2018 -0400

    Initial commit
Anastasias-MBP:GEP662_repo anastasiaclark$
```  

## How to undo an add (undo a staged file)
```console
git reset HEAD <file>       
```

## How to undo a commit 
On the commit-level, resetting is a way to move the tip of a branch to a different commit. This can be used to remove commits from the current branch. For example, the following command moves the current branch backwards by two commits.

```console
git reset --soft HEAD^     # use --soft if you want to keep your changes
git reset --hard HEAD^     # use --hard if you don't care about keeping the changes you made
git reset --soft HEAD~1    # use --soft to preserve changes that were made and undo last commit (~1 = back 1 commit)
```

## Practice
### 1. Create a file called test.py with a single line 
```python
print('This is just a test')
```
### 2. add the file, but don't commit it yet. Check the status

> my example
```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   test.py

Anastasias-MBP:GEP662_repo anastasiaclark$
```
### 3. Now, let's unstage the file

>my example
```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git reset HEAD test.py  
```
### 4. Check the status again, notice that the test.py is now untracked

```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	test.py

nothing added to commit but untracked files present (use "git add" to track)
Anastasias-MBP:GEP662_repo anastasiaclark$
```
### 5. Let's add the test.py to staging again. Then let's open the test.py add a line to it, commit the changes and push it to our remote repo.

What if the last change we made turned out to be wrong?! We can look at the history of our commits, find the tag of the commit when everything was still alright and set our working directory back to that point in time.

 git log-- to check the history

### 6. Check the histoty (git log) and find a safe point (where we haven't added that wrong line)
>my example
```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git log
commit 10c4badaa054b6b22f09027335c3c128990a0d7b
Author: anastasiaclark <anastasiapotupalova@gmail.com>
Date:   Mon May 14 08:51:10 2018 -0400

    added line to test.py

commit 94f794c460e123f1d902e4b2b6382ae3d8f779e9
Author: anastasiaclark <anastasiapotupalova@gmail.com>
Date:   Mon May 14 08:49:36 2018 -0400

    added test.py

commit e0c2eb23f8fe760c7b1847df29f8b28d8ae22104
Author: anastasiaclark <anastasiapotupalova@gmail.com>
Date:   Sun May 13 12:46:03 2018 -0400

    created myfile.py

commit d71fc91471339fd5dd2d80e73d332cc9d3b3d93f
Author: Anastasia Clark <anastasiapotupalova@gmail.com>
Date:   Sun May 13 12:08:34 2018 -0400

    Initial commit
:...skipping...
commit 10c4badaa054b6b22f09027335c3c128990a0d7b
Author: anastasiaclark <anastasiapotupalova@gmail.com>
Date:   Mon May 14 08:51:10 2018 -0400

    added line to test.py

commit 94f794c460e123f1d902e4b2b6382ae3d8f779e9
Author: anastasiaclark <anastasiapotupalova@gmail.com>
Date:   Mon May 14 08:49:36 2018 -0400

    added test.py

commit e0c2eb23f8fe760c7b1847df29f8b28d8ae22104
Author: anastasiaclark <anastasiapotupalova@gmail.com>
Date:   Sun May 13 12:46:03 2018 -0400

    created myfile.py

commit d71fc91471339fd5dd2d80e73d332cc9d3b3d93f
Author: Anastasia Clark <anastasiapotupalova@gmail.com>
Date:   Sun May 13 12:08:34 2018 -0400

    Initial commit
~
```

The tag of the commit i want to come back to is `94f794c460e123f1d902e4b2b6382ae3d8f779e9`

### 7. Use git checkout to bring the snapshot from that commit

```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git checkout 94f794c460e123f1d902e4b2b6382ae3d8f779e9
Note: checking out '10c4badaa054b6b22f09027335c3c128990a0d7b'.

You are in 'detached HEAD' state. You can look around, make experimental
changes and commit them, and you can discard any commits you make in this
state without impacting any branches by performing another checkout.

If you want to create a new branch to retain commits you create, you may
do so (now or later) by using -b with the checkout command again. Example:

  git checkout -b <new-branch-name>

HEAD is now at 94f794c... added test.py
Anastasias-MBP:GEP662_repo anastasiaclark$ 
```

Open test.py and loock at it. The line is not there.

Now, we have an option to create a new branch here and keep on working on this script untill we fix the bugs.

### 8. Create a new branch

```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git checkout -b test_branch
Switched to a new branch 'test_branch'
```
The old state is still on master

```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git checkout master
Switched to branch 'master'
```
Open the test.py, and the line is there again

Ok, let's say we done working on the branch and we want to merge the work from that branch into the master

### 9. Merge the branches
```console
Anastasias-MBP:GEP662_repo anastasiaclark$ git merge master
Updating 94f794c..10c4bad
Fast-forward
 test.py | 4 ++++
 1 file changed, 4 insertions(+)
Anastasias-MBP:GEP662_repo anastasiaclark$
```




#### Syntax for Windows Users
Note:  use `~` instead of `^`  

---

### References
[Reset, Checkout and Revert](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/commit-level-operations)  
[Stack Overflow:  How do you undo the last commit](http://stackoverflow.com/questions/927358/how-do-you-undo-the-last-commit)  
[Stack Overflow:  Remove files from last commit](http://stackoverflow.com/questions/12481639/remove-files-from-git-commit)  


