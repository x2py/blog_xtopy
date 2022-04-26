---
title: ""
description: ""
# date: 2022-01-13T16:01:16+05:30
date: 2022-04-26T08:44

draft: true
weight: 1
# aliases: ["/first"]
tags: [""]
categories: [""]
author: "Allwyn"
showToc: true
# TocOpen: false
hidemeta: false
comments: false
# canonicalURL: "https://canonical.url/to/page"
disableShare: false
disableHLJS: false
hideSummary: false
searchHidden: false
ShowReadingTime: true
ShowBreadCrumbs: false
ShowPostNavLinks: true
cover:
 image: "" #
 # alt: ""
 # caption: "" # display caption under cover
 relative: false # when using page bundles set this to true
 hidden: false # only hide on current single page
# editPost:
#     URL: "https://github.com/<path_to_repo>/content"
#     Text: "Suggest Changes" # edit text
#     appendFilePath: true # to append file path to Edit link
---

Git is essentially used to track the state or version of (every file in) your project. 

## Creating Repo
### Case 1 : Repo on Github, Cloned to local

Create Repo
```bash
# clone a online repo, offline
git clone git@github.com:x2py/tpy.py # Clone my python project template

# track all files in current folder
git add .

# commit changes (confirm the changes)
git commit -m "final changes in version 2"

# push changes to remote (send the files to online storage)
git push origin main
# <origin> is the url to which you want to send your files
# <main> is the branch to which you want to save your files there 



```


### Case 2 : Folder on local, pushed to Github

```bash

git init

# > Create empty repo on github
# > grab its url

git remote add origin <url>

git remote -v # this shows any remote remote repo linked to this folder

git push -u origin main 
# the <-u> stands for upstream
# with it, the mentioned origin becomes your default branch
# so that you can type 'git push' intead of 'git push origin main'


```

## Updating Repo
### Branching
#### Flow
Create branch -> Make changes to files 
	-> commit and push changes to remote repo 
	-> create pull request (on GH)
	-> merge changes to main branch (on GH) 
	-> pull changes from remote to local
	-> delete local branch
	
#### Creating a branch
```bash
git checkout -b feature-bells
# > make some changes to your files
git status # to see which files have changed

# pushing the updates to a new branch on github
git push -u origin feature-bells 

# > Go on to github and approve the pull request
git diff # shows changes made to the same file in two different branches
git merge # splice together all existing branches

# Delete a branch after it is merged
git branch -d feature-bells

```


### Merge conflict
Delete the part you dont want and then commit again


#### Undo a commit
```bash
git reset HEAD # Takes us back to previous commit
git reset HEAD~1 # takes us back to previous commit -1
git log # see a list of all your commits

git reset --hard # unstages the changes from git AND removes them from the files too
```
