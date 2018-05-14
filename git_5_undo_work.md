# Undo work (Checkout, Revert and Reset)

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
```bash
git log

# view formatted log
git log --pretty=format:"%h : %an : %ar : %s" -3
```

#### View last 2 commits
```bash
git log -2
```  

>my example  

```git
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
```git
git reset HEAD <file>       
```

Create a file called test.py with a single line 
```python
print('This is just a test')
```
add the file, but don't commit it yet. Check the status

> my example
```git
Anastasias-MBP:GEP662_repo anastasiaclark$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Changes to be committed:
  (use "git reset HEAD <file>..." to unstage)

	new file:   test.py

Anastasias-MBP:GEP662_repo anastasiaclark$
```
Now, let's unstage the file

>my example
```git
Anastasias-MBP:GEP662_repo anastasiaclark$ git reset HEAD test.py  
```
Check the status again

```Anastasias-MBP:GEP662_repo anastasiaclark$ git status
On branch master
Your branch is up-to-date with 'origin/master'.
Untracked files:
  (use "git add <file>..." to include in what will be committed)

	test.py

nothing added to commit but untracked files present (use "git add" to track)
Anastasias-MBP:GEP662_repo anastasiaclark$
```


## How to undo a commit
On the commit-level, resetting is a way to move the tip of a branch to a different commit. This can be used to remove commits from the current branch. For example, the following command moves the current branch backwards by two commits.

```console
git reset --soft HEAD^     # use --soft if you want to keep your changes
git reset --hard HEAD^     # use --hard if you don't care about keeping the changes you made
```

```
git reset --soft HEAD~1    # use --soft to preserve changes that were made and undo last commit (~1 = back 1 commit)
```

#### Syntax for Windows Users
Note:  use `~` instead of `^`  

---

### References
[Reset, Checkout and Revert](https://www.atlassian.com/git/tutorials/resetting-checking-out-and-reverting/commit-level-operations)  
[Stack Overflow:  How do you undo the last commit](http://stackoverflow.com/questions/927358/how-do-you-undo-the-last-commit)  
[Stack Overflow:  Remove files from last commit](http://stackoverflow.com/questions/12481639/remove-files-from-git-commit)  


