Self notes
- The analysis itself is secondary. The base data column, the key facts you collect are much more important.
- EG: While predicting the sales of a list of stores in a city-- Count of items, in store, sqft area of store, outlet type, city type in store

Preparations
- Deal with null values (Substitute them with mean)
- Convert catagorial columns into 1-hot
	- `from sklearn.preprocessing import LabelEncoder`


Definitions:
Target variable
- The varibale you want to successfully predict after your analysis
ID columns
- Remove 'ID' type columns from your DF as they do not add any value to the predictive model



Process
- PreProcess
	- Bring all columns to same same value count
- Explore
	- Displot Each column(see value distribution)






### Explore
#### Counts
In this phase, we want to make sure there is uniform distribution of values
Displot
- Here we want to see how the values in the column are distributed
- It's skew (Center, Left, Right)
- If Left / Right skew then apply log transformation
	- `np.log(1+df['sales'])`
Countplot
- `sns.countplot()`

#### Correlation
- `sns.heatmap(df.corr())`

