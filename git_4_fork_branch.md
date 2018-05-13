# Fork & Clone a repo; collaborate

### Go to repo on GitHub
Navigate to my Githib account and locate the repo to be cloned, called GEP662_repo

### Fork repo
Upper right of github page:  "Fork" the repo

Go to your forked repo, in my example it is: https://github.com/anastasiaclark/GEP662_repo
 
### Clone repo
Clone that forked repo (which is now under your name now)

In the right column, find the link to **HTTPS clone URL** and **copy** that URL to be cloned.  
(Windows users may need to use ssh url.)  

### Go to working directory on local computer

In terminal: 
* `cd` into directory where repo will be cloned
* clone repo:   `git clone <url goes here>`

>my example
 ```bash
 Anastasias-MBP:~ anastasiaclark$ git clone https://github.com/anastasiaclark/GEP662_repo.git
Cloning into 'GEP662_repo'...
remote: Counting objects: 3, done.
remote: Total 3 (delta 0), reused 0 (delta 0), pack-reused 0
Unpacking objects: 100% (3/3), done.
```
* `cd` into cloned repo and check it's content with `ls`

```bash
Anastasias-MBP:~ anastasiaclark$ cd GEP662_repo/
Anastasias-MBP:GEP662_repo anastasiaclark$ ls
README.md
Anastasias-MBP:GEP662_repo anastasiaclark$
```

#### List remotes
```bash
origin	https://github.com/anastasiaclark/GEP662_repo.git (fetch)
origin	https://github.com/anastasiaclark/GEP662_repo.git (push)
Anastasias-MBP:GEP662_repo anastasiaclark$
```
