---
title: "Selecting rows and columns in pandas"
description: ""
# date: 2022-01-13T16:01:16+05:30
date: 2022-04-20T10:48

draft: true
weight: 1
# aliases: ["/first"]
tags: [""]
categories: ["Allwyns Pandas Field Guide"]
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
# KW FOR BOT
forSkill: ["python"]
forLibrary: ["pandas"]
forRole: ["data analyst"]
uDate: {{date}}
---

## Why even bother?
When working with DataFrames in pandas, I have always missed the ease with which I could select rows and columns in Excel. Simple things like deleting a particular cell or arranging columns were soo incredibly easy and intuitive. Of course Google sheets take this one step further with its fancy editor. I am yet to find such ease of use within pandas.

In today's post I would like to share a couple of handy techniques I use every soo often to deal with the seemingly simple task of selecting and moving around rows and columns in Pandas. 
## Smart techniques 
### Setting up our base data
Here's the base code on top of which I will show all examples:
```python
import pandas as pd
import numpy as np
import re
df = pd.read_csv('https://people.sc.fsu.edu/~jburkardt/data/csv/zillow.csv')


```
### Selecting columns the obvious way
Doing so will create a new df wth 
```python

df = df[['Index', 'Beds', 'Baths']]

```

