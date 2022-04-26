---
title: "Pandas basics"
description: "Performing fundamental tasks in Python Pandas"
# date: 2022-01-13T16:01:16+05:30
date: 2022-04-25T16:24

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


####  Creating Data frames from within Pandas
```python

# Single column multiple rows
pd.DataFrame(['new', 'old', 'erma'], columns=['ne'], )

# Single row multiple column
pd.DataFrame([['new', 'old', 'erma']], columns=['ne', 'eer', 'ere'], )

# Multiple row, multiple columns
pd.DataFrame([['new', 'old', 'erma'], 
			  ['new', 'old', 'erma']], columns=['ne', 'eer', 'ere'], )


```

#### Appending data
```python
# Add new rows to existing data frame
df_credit = df_credit.append({'First Name': 'John', 'Last Name': 'Abuli','Credit Score':785}, ignore_index=True)
# This will create a new df where columns with no data will have a NaN value
# This is due to the ignore_index=True
							  
```


#### Update Data
```python
# Use .ix for row index, column name
df_credit.ix[4,'Approval Date']
# Use .iat for row index, column index


```

#### Drop Data
```python
# Drop columns by name
df_credit.drop(['Credit Approval', 'Card Name'], axis = 1)
df_credit['First_Find Ja'] = df_credit['First Name'].str.find('Ja')

```


## Functions and Built in techniques
### Strings
Regex match text
```python

df_credit['First_Match Ja'] = df_credit['First Name'].str.match('Ja')
```





## Rough points
Get columns where rows meet a certain condition
```python
df_credit.loc[df_credit['Card Name']=='Golden', ['First Name','Last Name']]
```

Sort on multiple columns
```python
df_credit.sort_values(['Credit Score', 'Income'] ,ascending = [True, False])
```

Set column value as per condition on row, Else keep original
```python
# df['base_column'].mask(condition to test, value to assing)
df_credit['Income'] = df_credit['Income'].mask( df_credit['Income'] > 100000,  
100000)
```