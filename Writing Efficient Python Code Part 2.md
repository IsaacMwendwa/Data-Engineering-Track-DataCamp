# Writing Efficient Python Code Part 2

## Gaining Efficiencies using Combining, Counting, and Iterating
### Combining Objects
* Suppose we have two lists we want to combine in a k,v fashion:
#### 1. Combine using enumerate()
![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/ab7e9ef4-5734-49e0-98d5-0763f06c3b90)

#### 2. Combining with zip()
![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/8ef76690-a3b6-4559-8ade-2ac92cfa2613)

### Python Collections Module
* Python comes with a number of efficient built-in modules
* The collections module contains specialized datatypes that can be used as alternatives to standard dictionaries, lists, sets, and tuples
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/f5983e87-574b-4b68-8d02-584b1a8c7dff)
* To count items and assign counter counts as k,v pairs:
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/7ee247c8-e60b-4d05-bf34-ff1ab84dd5df)

### Python Itertools Module
* Another built-in module, itertools, contains functional tools for working with iterators
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/f2fb3ad6-9033-4350-91c1-606c1a39dd8f)
* A more efficient solution to create combinations is:
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/ead87aa8-4675-43b9-9e37-32a78c1f34b8)

## Set Theory
* Often, we'd like to compare two objects to observe similarities and differences between their contents
* When doing this type of comparison, it's best to leverage a branch of mathematics called set theory
*  A set is defined as a collection of distinct elements
*  Thus, we can use a set to collect unique items from an existing object e.g. `unique_set = set(list_a)`
* Python comes with a built-in set data type. Sets come with some handy methods we can use for comparing
     * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/efc461da-ef22-4e35-9c36-9c382b3d1c8a)
     * Note that `set_a.union(set_b)` collects unique items that appear in the sets
     * Symmetric difference collects items that exist in exactly one of the sets (but not both)
* Example: Get items which appear in both lists without using for loops:
     * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/0d79662e-82da-445a-a27b-43936b176eed)

 ## Eliminating Loops
 * Although using loops when writing Python code isn't necessarily a bad design pattern, using extraneous loops can be inefficient and costly
 * Benefits of eliminating loops:
      * Fewer lines of code
      * Better code readability (Zen - Flat is better than nested)
      * Efficiency gains
* Example of finding sum of rows in a list of lists: (eliminating loops using built-ins)
     * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/6a67203b-f278-48b0-a11c-e243aa9b9802)
* Example of eliminating loops using Numpy in a np array:
     * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/cf37d41e-1034-40e3-a5a6-c17771c82a4c)
* Exercise to eliminate loops: Pokemon game:
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/13e6897b-db18-413c-b900-9249cc5a750d)

## Writing Better Loops
* The best way to make a loop more efficient is to analyze what's being done within the loop. We want to make sure that we aren't doing unnecessary work in each iteration
* If a calculation is performed for each iteration of a loop, but its value doesn't change with each iteration, it's best to move this calculation outside (or above) the loop
* If a loop is converting data types with each iteration, it's possible that this conversion can be done outside (or below) the loop using a map function (Holistic conversions)
* Anything that can be done once should be moved outside of a loop
* Example of holistic conversions:
   * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/5ab8ddc3-941f-45a3-b8b1-507dafae016c)
 
# Pandas Optimizations
* Pandas is a library used for data analysis
* The main data strucuture of pandas is the DataFrame, a tabular data structure with labeled rows and columns (built on top of Numpy Array structure

### Iterating Pandas DF with .iterrows()
* .iterrows() returns each DataFrame row as a tuple of (index, pandas Series) pairs
* This means each object returned from .iterrows() contains the index of each row as the first element and the data in each row as a pandas Series as the second element
* Example: calculate a new column for storing a team's win percentage = Wins ('W') / Games ('G'):
      * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/571faf9b-d3e6-4a3b-aab6-37de8f44bab4)

### Iterating with .itertuples()
* We can use .itertuples() to loop over our DataFrame rows instead, which is a faster method
      * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/d4bd2ad5-f57a-4b6e-bccc-6bb4f010b8c9)

### Pandas alternative to looping
* You can loop over DataFrames row-by-row with ease using .iterrows() and .itertuples()
* However, in order to write efficient code, we want to avoid looping when possible
* Thus we use .apply() acts like the map function
* It takes a function as an input and applies this function to an entire DataFrame
* Since we are working with tabular data, we must specify an axis that we'd like our function to act on
* Must specify an axis to apply (0 for columns; 1 for rows)
* Just like the map function, pandas' .apply() method can be used with anonymous functions or lambdas
* Example 1:
      * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/cb69422b-cfd9-4a7b-b21a-252c05ef39ed)
* Example 2:
      * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/76aa6810-c8c4-4519-afbe-2c81aace7fc3)
  
