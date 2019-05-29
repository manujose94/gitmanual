# Control de Versiones

## .git Folder

![Screenshots](https://github.com/manujose94/gitmanual/blob/master/img/carpeta_git.PNG?raw=true)
        
The folder heads -> contain a local branches (name branch and the last commit rerefenced). The branch its a referece to a commit

![Screenshots](https://github.com/manujose94/gitmanual/blob/master/img/carpeta_git2.PNG?raw=true)

File HEAD -> Refenrence to a branch tag or actual commit of workspace.
(Cada vez que hacemos "git checkout" y cambiamos de rama, ese archivo se va actualizando.)

## The Default State
![Screenshots](https://github.com/manujose94/gitmanual/blob/master/img/commit_branches.PNG?raw=true)

    Where refence in file HEAD, point to a master. master with last commit.

![Screenshots](https://github.com/manujose94/gitmanual/blob/master/img/commit_branches2.PNG?raw=true)

    With "git checkout" file HEAD reference a new branch.

Now, wether performed the command "**git commit**", this is result:

![Screenshots](https://github.com/manujose94/gitmanual/blob/master/img/commit_branches3.PNG?raw=true)



## Git – File states

**Tracked files**

These are files that were in the last snapshot (aka); they can be in one of the following sub states:

-  unmodified

        These are any files that haven't been modified since the last commit. 
        They will still be included in the next commit, but remain as is.

-  modified

        These are files that have been modified since the last commit (we probably modified these as part of bug fixes). 
        These files will be included in the next commit, but will be included in thier respective new form.

-  staged

        These are files that are either not present in the last commit (e.g. newly created files) or are "modified" files that we tell git to include in the next commit. 
        Files are added to the staging using git's "add" command.

-  untracked file

        These are any files that are not being tracked, i.e. git isn't of the existance of these files. 
        You can change the state of these files to "tracked - staged" by using git's "add" command


![Screenshots](https://github.com/manujose94/gitmanual/blob/master/img/changes_in_files.PNG?raw=true)


**Staged** -> Untracked: 
``git reset HEAD a.html
``

**Modified** -> Unmodified:
``
git checkout -- a.html
``

## Command line git

Start command "git" in project path (example: C:\Users\Manu\ITBA\paw-2019a-6)


### Add new Branch 

``
 PS C:\Users\Manu\ITBA\paw-2019a-6> git checkout -b mi-rama-manu
``    
Output:
``    
 Switched to a new branch 'mi-rama-manu'
``    

If we want to add the changes of the branch to the remote branch

    git checkout mi-rama-manu
    git add .
    git commit -m "message"
    git push -u origin mi-rama-manu

 Then, the master branch to get changes from branch *mi-rama-manu*, must perform a "Pull".

###  List my remote branches

``
git branch -a
``
###  List all commits abaout my git
 ``
        PS C:\Users\Manu\ITBA\paw-2019a-6> git log  --oneline        
``
        
        39895b5 (HEAD -> mi-rama-manu) fixed estado and datapicker edititem
        f9b465a (origin/mi-rama-manu, origin/master, master) User Deploy    

### How **Push Firts time** to github account

    git init

    git add .

    git commit -m -"First Commit"

    git remote add origin https://github.com/manujose94/discomcloud-ionic.git

    git push origin master --force

###  **After firts time**, online command:

    git commit -am 'API send email'

    git push origin master --force 

###  In my actual **local branch**, to update from the last commit of the remote master

        1. git fetch origin (update master local)
        2. git merge origin/master mi-rama-manu
        3. git push 

**git merge output error**  (*Delete all changes, since the last commit where the pull was made*): 

``
git reset --hard
``


# Updating a feature branch

First we'll update your local master branch. Go to your local project and check out the branch you want to merge into (your local master branch)
```bash
$ git checkout master
```

Fetch the remote, bringing the branches and their commits from the remote repository.
You can use the -p, --prune option to delete any remote-tracking references that no longer exist in the remote. Commits to master will be stored in a local branch, remotes/origin/master
```bash
$ git fetch -p origin
```

Merge the changes from origin/master into your local master branch. This brings your master branch in sync with the remote repository, without losing your local changes. If your local branch didn't have any unique commits, Git will instead perform a "fast-forward".
```bash
$ git merge origin/master
```

Check out the branch you want to merge into
```bash
$ git checkout <feature-branch>
```

Merge your (now updated) master branch into your feature branch to update it with the latest changes from your team.
```bash
$ git merge master
```

Depending on your git configuration this may open vim. Enter a commit message, save, and quit vim e.g. press "a" to enter insert mode and append text following current cursor position, press Esc key to enter command mode, press :wq to write the file to disk and quit.

This only updates your local feature branch. To update it on GitHub, push your changes.
```bash
$ git push origin <feature-branch>
```
       
