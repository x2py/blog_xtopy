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
## The Basics 
### Setting up our base data
Here's the base code on top of which I will show all examples:
```python
import pandas as pd
import numpy as np
import re
df = pd.read_csv('https://people.sc.fsu.edu/~jburkardt/data/csv/zillow.csv')


```

## Vanilla ways of  selecting columns
### Using angle brackets
Doing so will create a new df with the columns Index, Beds and Baths
```python

df = df[['Index', 'Beds', 'Baths']]

```

### Using .get
If any column mentioned in the list does not exist, it will return a NONE.
This technique is useful for two reasons:
1. When you need to explicitly and in a human readable way mention which columns you need
2. When the each of the columns mentioned are absolutely necessary. 

If any one column could not be found in the source df, you get no df in the output. Instead you get a nice little 'None'
```python
df.get(['Index', 'Beds'])

df.get(['Index', 'Beds', 'Swimming Pools'])
#$ None

```

### Filter from existing columns
While '.get' returns a 'None' on a nonexistent column, we can still return whatever other columns were found in the source df, sans the one that wasn't
```python
df[df.columns[df.columns.isin(['Index', 'Beds', 'Swimming Pools'])]]


```

### Filter out unwanted columns
Select everything **EXCEPT** a particular column or a subset of columns.
The following code gives us all columns except "Beds" and "Sqft"
#### Using Difference
```python
df[df.columns.difference(['Beds', 'Sqft'])]


```
#### Using .isin()
```python
df[df.columns[~df.columns.isin(['Beds','Sqft'])]]


```


## Pro coder ways of  selecting columns
### Selecting based on data type
I recently had the good fortune of working with a huge dataset with a decade worth of transactions. One of the things I had to do was select all columns with some pricing information. This technique is a good candidate to show how we could use some better mindful ways to select data en mass.
Before you use this technique, I would also suggest getting to know what the data types of each column with:
```python
df.dtypes
```
then using another command to automatically converting types or doing it manually
```python
df = df.convert_dtypes()
```

Select all columns of type number (64 bit integers to be specific)
```python
df.loc[:,(df.dtypes=='int64').values]


```
Note: the required data was a 3 digit integer hence I choose 'int'64, else we would use more expansive types like float.

### Select a column based on column names
#### If column name contains a character or word
Here the code says: Give me all rows of `df` for which each column has the word `'al'` in it.
```python

df.loc[:,['price' in i.lower() for i in df.columns]]

```

#### If column name starts with a particular character or word (prefix)
```python

df.loc[:,[df.columns.str.startswith('S')]]

```
#### If column name ends with a particular character or word (suffix)
```python

df.loc[:,[df.columns.str.endswith('s')]]

```

## Exotic ways of  selecting columns