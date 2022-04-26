---
title: "Simple things in Python that I always forget the syntax to"
description: "There is just soo much to do and soo much more to learn in the multiple programming languages I work in. In this post I go over some frequently used code snippets that have served me well"
# date: 2022-01-13T16:01:16+05:30
date: 2022-04-22T10:28
draft: true
weight: 1
# aliases: ["/first"]
tags: ["python", "guides"]
categories: ["Quick Guides"]
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

There is just soo much to do and soo much more to learn in the multiple programming languages I work in. Add to that all the rapid context switching and it makes for the recipe to forget minor details.
This is why This page exists. It is a (frequently updated) list of stupidly simple, infrequently used yet frivolously forgetful things. This particular post deals with such things in the Python language that I seem to use very often at work and for hobby too.

Bookmark this page if you're on the same boat as me. And perhaps add your on 'FUFF'  things to it 😄

#### Start a web server from a folder in python in the terminal
```shell
python -m http.server --directory .
```
![](static/images/Pasted%20image%2020220422110907.png)
This launches a web server in the current directory. I use it often to demo some HTML files or play with some webapps locally. 
The module is a part of the standard library so you don't need to install anything or bother with other apps/modules or external dependencies or even launch a code editor. 
It launches the server at the URL:  https://localhost:8000

#### Check how similar two words or sentences are
```python
from difflib import SequenceMatcher
s = SequenceMatcher(None, "barak", "baroque")
s.ratio()
#$ 0.5
```