# Cleaning Data in Python

## Data Type Constraints
* Checking dtypes of columns:
    * `df.dtypes` # dytpes
    * `df.info()` # dtypes and missing values
* String to integers
    * `df['col'] = df['col'].str.strip('character e.g $')` # remove special characters
    * `df['col'] = df['col'].astype('int')` # convert col to int
    * `assert df['col'].dtype == 'int'`  # confirming col is now integer; returns nothing if true, and assertionerror otherwise
* Numerical variables to categorical e.g if Marriage col has values 0 for unmarried, 1 for married, and 2 for divorced
     * `df['col'] = df['col'].astype('category')`

#### Dealing with out of range values
* Outliers in categorical data can be seen when you plot a histogram, and there are connected bars
* Options to deal with out of range data:
   * Drop the data, but only drop data when a small proportion of your dataset is affected by out of range values
   * Setting custom minimums or maximums to your columns
   * Treat data as missing, and impute
   * Setting a custom value dependent on the business assumptions behind our data
