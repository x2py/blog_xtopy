---
title: "Simple things in Pandas that I always forget the syntax to"
description: ""
# date: 2022-01-13T16:01:16+05:30
date: 2022-04-22T10:27
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

#### Combine multiple csv files into one file or excel or pandas df
This is great if you want to combine all files in a folder into a single csv file for upload to a service or run some analysis.
Here I will combine the files (vertically) one under another instead of side to side (horizontally).
Of course there are multiple ways to do this but given the ethos of Python, I like to use code that is a good balance of performance and readability.
Here's how to combine multiple csv files into a single data frame for analysis:
```python
df = pd.concat([pd.read_csv(file, low_memory=False) for file in glob.glob('ls/*.csv')])
```
**Here's what's happening:**
I have used a method called list comprehension which lets me do away with 'for loops' and makes the code more concise and readable.
I have made use of 2 modules that I use regularly.
When we read the code from right to left it makes more sense.
```Plain
- The glob part : Create a list of only .csv files
- The for part : For each of the items in the list do something
- The pd part : Create a data frame from the file path being provided
```
That's it.  you can even run this code from the terminal / cmd without opening up code editor.
```python
python -c "import pandas as pd; import glob; pd.concat([pd.read_csv(file, low_memory=False) for file in glob.glob('ls/*.csv')]).to_csv('full.csv')"
```
That last part is is the code to save the data as a csv file named 'full.csv' on our computer.


#### Convert a filed to datetime based on another field
```python
df['Month'] = pd.to_datetime(df['Calmon'].astype('str').str.zfill(7).apply(lambda x: str('01.')+x), format='%d.%m.%Y')
```
**Here's what's happening**
```
- Format :: Use the format 31-12-1995
- Apply :: We do this to add a 'day' at the begining since pandas cries otherwise
- zfill :: The base string has 1.2022 as well as 12.2022 so we standardize them to mm.yyyy
- astype :: we cant add text to a numeric column so we convert it to a text string
 
```
