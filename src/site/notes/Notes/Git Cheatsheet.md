---
{"dg-publish":true,"permalink":"/Notes/Git Cheatsheet/","noteIcon":""}
---


## Basic workflow

```bash
$ git config global your_setting your_values
$ git init (new_repo_name)
$ git status
$ git add file_name
$ git rm file_name 
$ git commit -m "commit_message"
$ git restore # discard changes

$ git clone clone_source name_of_replicates
$ git remote add remote_name remote_url/path   # the remote_name is created by you 
$ git remote add origin remote_git_repo # set remote git
$ git push -u origin master

$ git commit -m "This is a message"
$ git annotate file  # more info than git log; it shows who made the last change to each line of a file and when
$ git reset  # remove files from the staging area
```

## Git history

```bash
$ git log
$ git log -p # show the recent changes
$ git log --oneline
$ git log branch1..branch2 # show logs of branch2 relative to branch1
$ git log file_name # history for a specific file or directory
$ git diff commit_ID_1 commit_ID_2 (file_name)
$ git blame # to check most recently who wrote the lines; good for debugging
```

## Git branch & version control

```bash
$ git branch new_branch
$ git checkout branch_name  # switch to that branch
$ git checkout -b new_branch_name  # switch to the new branch
$ git checkout --.  # discard all the changes
$ git checkout master # back to the master branch
$ git diff sth1..sth2  # sth can be commits. branches, etc
$ git merge branch_1, branch_2
$ git pull remote-name branch-name
$ git push remote-name branch-name  # git push origin master
```