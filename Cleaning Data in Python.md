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
        <br> `df['col'] = df[df['col'] <= 5]` # Drop values using filtering
        <br> `df.drop(df[df['col'] <= 5].index, inplace = True)` # Drop using .drop()
   * Setting custom minimums or maximums to your columns
        <br> `df.loc[df['col'] > 5, 'col'] = 5`   # Set col > 5 to 5 
   * Treat data as missing, and impute
   * Setting a custom value dependent on the business assumptions behind our data

* Converting object to date type
  <br> `df['col'] = pd.to_datetime(df['col']).dt.date`  # converting object to date
  <br> `today_date = dt.date.today()`  # date today

#### Uniqueness Constraints
* To find duplicate rows:
  <br> `cols = ['col1', 'col2', 'col3']` # column names to check for duplication
  <br> `duplicates = df.duplicated(subset = 'cols', keep = 'first')` # keep can be first/last/False (False keeps all)
* To drop duplicates: `df.drop_duplicates(inplace = True)` # without subset defined, drops complete duplicates. Keep first is default behaviour
* Exercise:
   * Treat duplicated rows by first dropping complete duplicates.
   * Then merge the incomplete duplicate rows into one while keeping the average duration, and the minimum user_birth_year for each set of incomplete duplicate rows.
   * Use groupby and summary statistics for the exercise
    * ![Treating Complete and Incomplete Duplicates](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Treating-Complete-and-Incomplete-Duplicates.PNG "Treating Complete and Incomplete Duplicates")

* To sort dataframe: `df.sort_values(by= ['col1, col2'], ascending=False)[['col1, col2']]` #sorts in descending order

### Text and categorical data problems
* Categorical data represent variables that have predefined finite set of categories. Examples of this range from marriage status, household income categories, loan status and others
* Since categorical data represent a predefined set of categories, they can't have values that go beyond these predefined categories
* To deal with inconsistent categories, we use two main types of joins:
   * Anti joins, take in two DataFrames A and B, and return data from one DataFrame that is not contained in another
   * Inner joins, return only the data that is contained in both DataFrames
* 
