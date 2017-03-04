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
* Merage two columns
  
