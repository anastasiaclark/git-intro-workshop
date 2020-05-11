# Fork & Clone a repo; collaborate

### Go to repo on GitHub
Navigate to my Githib account and locate the repo to be cloned, called GEP662_Spring2020_collab_repo

### Fork repo
Upper right of github page:  "Fork" the repo

Go to your forked repo, in my example it is: https://github.com/anastasiaclark/GEP662_Spring2020_collab_repo
 
### Clone repo
Clone that forked repo (which is now under your name now)

In the right column, find the link to **HTTPS clone URL** and **copy** that URL to be cloned.  
(Windows users may need to use ssh url.)  

### Go to working directory on local computer

In terminal: 
* `cd` into directory where repo will be cloned
* clone repo:   `git clone <url goes here>`

>my example
 ```console
 Anastasias-MBP:~ anastasiaclark$ git clone https://github.com/anastasiaclark/GEP662_Spring2020_collab_repo
Cloning into 'GEP662_Spring2020_collab_repo'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```
* `cd` into cloned repo and check it's content with `ls`

```console
Anastasias-MBP:~ anastasiaclark$ cd GEP662_Spring2020_collab_repo/
Anastasias-MBP:GEP662_repo anastasiaclark$ ls
README.md	myfile.py
```

#### List remotes
```console
origin	https://github.com/anastasiaclark/GEP662_repo.git (fetch)
origin	https://github.com/anastasiaclark/GEP662_repo.git (push)
Anastasias-MBP:GEP662_repo anastasiaclark$
```

## Let's collaborate!
Open myfile.py, add few lines of code and save it. 
Do `git add`, `git commit`, `git push`, and the the rest of us will `git pull` to get changes you made syncronized with our local copies. 
