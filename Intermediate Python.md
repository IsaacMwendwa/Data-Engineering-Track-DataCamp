### Logic, Control Flow and Filtering
* Comparison Operators --> greater than (>), less than (<), equal to (==), not equal to (!=), greater than or equal to (>=), less than or equal to (<=)
* Applying comparison operators to filter Numpy array: `arr2 = arr1[arr1 < 20]`
* Boolean Operators ---> and, or, not
* Boolean Operators for Numpy Arrays ---> logical_and(), logical_or(), logical_not().
<br>Syntax for array elements between 20 and 22: `np.logical_and(arr > 20, arr < 22)`
* Applying Comparison Operators to filter Pandas DataFrames
<br> Syntax: `df[df["col"] > 20]`
* Applying Boolean Operators for Numpy Arrays to filter Pandas DataFrames
<br> Syntax for df with column "col" with values betweem 20 and 22: `df[np.logical_and(df["col"] > 20, df["col"] < 22)]`
* Printing elements in a list with their indices using for loop:
<br>Syntax: `for index, elem in enumerate(list):`
<br> `print("index " + str(index) + ": " + str(elem))`

#### Looping Data Structures
1. Dictionary
<br> `for key, value in dict.items(): print(key + ":" + str(value))`
2. Numpy Arrays (especially 2D and above)
<br> `for val in np.nditer(my_array): print(val)`
3. Pandas DataFrame
* Printing labels and rows:
 <br>`for label, row in df.iterrows(): print(label + ": " + row)`
* Printing specific column from rows:<\br>
<br>`for label, row in df.iterrows(): print(label + ": " + row["column")`
* Adding a new column by applying a function on one of the columns:
<br>`df["new_column"] = df["existing_column"].apply(your_transform)`
* To ensure a variable x doesn't go below a threshold (e.g 10) in a loop:
<br>`x = max(10, x-1)`
