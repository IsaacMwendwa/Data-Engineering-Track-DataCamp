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
