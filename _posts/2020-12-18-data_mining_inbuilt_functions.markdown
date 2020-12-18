---
layout: post
title:      "Data Mining Inbuilt Functions"
date:       2020-12-18 17:56:11 +0000
permalink:  data_mining_inbuilt_functions
---


There are many methods that you can use to mine a pandas data-frames. This blog with discuss a few of the main methods to use how they can be utilized to better understand the data.

.shape

This method returns a tuple of the rows and columns of a data-frame.

df = pd.DataFrame({'column1': [1, 2, 3], 'column2': [4, 5, 6]})
df.shape

returns

(3, 2)

three rows and two columns.

.info(verbose=True)

This method returns a summary of the data including the data-type for each column, non-null values, and the data memory usage.

returns

<class 'pandas.core.frame.DataFrame'>
RangeIndex: 3 entries, 0 to 2
Data columns (total 2 columns):
 #Column   Non-Null Count  Dtype
---  ------   --------------  -----
 0   column1  3 non-null      int64
 1   column2  3 non-null      int64
dtypes: int64(2)
memory usage: 176.0 bytes

a data-type of int64, 3 non-null values for each column, and 176 bytes of memory usage.

.unique()

This method returns all the unique values of each column.

for column in df:
    print(column,df[column].unique())
		
returns

column1 [1 2 3] 
column2 [4 5 6]

three unique characters for each column.

.isnull()

This method returns whether there are any null values in the data-frame.

df.isnull().any()

returns

column1    False 
column2    False 
dtype: bool

both columns do not have null values and have a data-type of bool.

.isna()

This method also returns whether there are na values in the data-frame and summing the values can be done with the sum method.

df.isna().sum()

returns

column1    0 
column2    0 
dtype: int64

both columns do not have na values and the data-type of the columns.

.dtypes

This method returns the data-type of the columns.

df.dtypes

returns

column1    int64 
column2    int64 
dtype: object

each column data-type is int64 and they are objects.


