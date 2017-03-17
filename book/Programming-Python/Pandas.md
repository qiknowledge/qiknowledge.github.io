## Knowledge base for Pandas library

* Concatenate dataframe
   ```python
   import pandas as pd
   # df and df2 are the dataframe
   df.append(df2, ignore_index = True) # the indexes must be disjoint but the column do not need to be
   frames =[df1, df2, df3]
   result = pd.concat(frames) # df1, df2, df3 have the same column names
   result.ix['y'] # get the second block of the dataframe
   ```
* Create dataframe
  ```python
  # from dictionary
  d = {'one': [1.,2.,3., 4.],
       'two': [4.,3.,2.,1.]}
  pd.DataFrame(d)
  ```
* Iterate through the row
  ```python
  for index, row in df.iterrows(): #slow, has to convert row to series
  for row in df.itertuples():
  #fast, Iterate over the rows of DataFrame as tuples, with index value as first element of the tuple.
  ```
* Concatenate data frame
  ```python
     # if df1, df2, df3 have the same column names, then
  d = [df1, df2, df3]
  out = pd.concat(d, ignore_index = True)
  out = df1.append(df2, ignore_index = True) # new df will have all columns from previous dataframe
  # Pandas series is like vector in R
  s1 = pd.Series(['x0','x1','x2','x3'], name ='X')
  result = pd.concat([df1, s1], axis = 1, ignore_index = True) # it will add a new column(s1) to the df1, and ig=Ture will 
                                                              # drop all name references
  pd.concat([s3,s4,s5], axis= 1, keys=['red','blue','yellow']) # s1, s2 and s2 are series    

  # concat a dictionary
  pieces = {'x': df1, 'y': df2,'z':df3}
  result = pd.concat(pieces) #x, y, z will be used for key arguments                                                      
  ```
* Joining/merging
  ```python
    pd.merge(left, right, how='inner', on = None, left_on= None, right_on = None, left_index = False, right_index = False, 
    sort=True, suffixes=('_x','_y'), copy = True, indicator = False)
  ```
  - `on`: Columns to join on , must be found in both the left and right DataFrame objects. 
  - `left_on`: Columns fom the left DataFrame to use as keys 
  - `right_on`: Columns from the right DataFrame to use as keys
  - `left_index`: 
  - `how`: `left, right, outer, inner`
  
* Convert data into same type, `series contains data, index, dtype and name`
  ```python
    #return types for dataframe
    df.dtypes
    # A basic element of pandas dataframe is called series
    # series contains data, index, dtype and name
    pd.DataFrame( {'name': pd.series, 'name2': pd.series} )
    del df['two']
    df2 = df.pop('three') # remove 'three' column
    
    pd.to_numeric(s, errors='coerce')
    0     1.0
    1     2.0
    2     4.7
    3     NaN
    4    10.0
    dtype: float64

    pd.to_numeric(s, errors='ignore')
    # the original Series is returned untouched

    df[['col2','col3']] = df[['col2','col3']].apply(pd.to_numeric) # apply to two columns

    df.apply(lambda x: pd.to_numeric(x, errors='ignore')) # apply to all columns

    df[['two', 'three']] = df[['two', 'three']].astype(float)

  ```
