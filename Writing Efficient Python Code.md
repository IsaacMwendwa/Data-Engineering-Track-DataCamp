# Writing Efficient Python Code

## Introduction
* Efficient code refers to code that satisfies two key concepts
* First, efficient code is fast and has a small latency between execution and returning a result
* Second, efficient code allocates resources skillfully and isn't subjected to unnecessary overhead
* Although your definition of fast runtime and small memory usage may depend on the task at hand, the goal of writing efficient code is still to reduce both latency and overhead
* Pythonic code is code that follows the best practices and guiding principles of Python. Pythonic code tends to be less verbose and easier to interpret
* The Zen of Python is a list of a 19 idioms and best practices that summarize Python's design philosophy
* It is one of Python Enhancement Proposals (PEP20), and can be accessed by running the `import this` command from the IPython console
  * ![Zen of Python](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/The-Zen-of-Python.PNG "Zen of Python")
* Writing efficient Python code employs among other techniques, list comprehension:
  * `newList = [ expression(element) for element in oldList if condition ]`
* Python List comprehension provides a much more short syntax for creating a new list based on the values of an existing list
* Advantages of List Comprehension
   * More time-efficient and space-efficient than loops.
   * Require fewer lines of code.
   * Transforms iterative statement into a formula.
* Example of finding names with 6 letters or more from a list 'names':
<br> `better_list = []`
<br> `for name in names:`
<br> `if len(name) >= 6:`
<br> `better_list.append(name)`
* Pythonic way using list comprehension:
<br> `best_list = [name for name in names if len(name) >= 6]`

### Reducing loops to built-in functions
#### 1. range()
* Create list of nums from 1-10:
<br> `num = range(0, 11)`
<br> `list_num = list(num)`
* Create list of even numbers: range(start, stop, step)
<br> `even_nums = range(2, 11, 2)`
<br> `even_nums_list = list(even_nums)`

#### 2. enumerate()
* enumerate creates an index item pair for each item in the object provided
  * ![Enumerate Function](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Enumerate-built-in-function.PNG "Enumerate Function")
* We can also specify the starting index of enumerate with the keyword argument start: `indexes = enumerate(list_a, start=5)`
* Example: for a list `names = ['Jerry', 'Kramer', 'Elaine', 'George', 'Newman']` ordered according to arrival, attach an index representing the arrival order:
  * ![Enumerate Example](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/map-with-lambda.PNG "Enumerate Example")
#### 3. map()
* map() can also be used with a lambda (an anonymous function)
* We can use map and a lambda expression to apply a function, which we've defined on the fly, to our original list
* The map function provides a quick and clean way to apply a function to an object iteratively without writing a for loop 
 ![Map with lambda](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/map-with-lambda.PNG "Map with lambda")
* Example to convert names to uppercase:
  *  ![Map Example](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Enumerate-example.PNG "Map Example")

### Power of Numpy Arrays
* NumPy arrays provide a fast and memory efficient alternative to Python lists
* To create: `nums_arr = np.array(range(5))`

#### 1. NumPy Array Homogeneity
* NumPy arrays are homogeneous, which means that they must contain elements of the same type
* Homogeneity allows NumPy arrays to be more memory efficient and faster than Python lists
* Requiring all elements be the same type eliminates the overhead needed for data type checking

#### 2. NumPy Array Broadcasting
* When analyzing data, you'll often want to perform operations over entire collections of values quickly
* Lists don't support broadcasting, hence operations on entire list require fro loops/list comprehension
* NP arrays are advantageous because of their broadcasting functionality
* NumPy arrays vectorize operations, so they are performed on all elements of an object at once. This allows us to efficiently perform calculations over entire arrays
* e.g to square all elements in array, we square the array itself: `np_arr ** 2`

#### 3. NumPy Array Indexing
* Another advantage of NumPy arrays is their indexing capabilities
* When comparing basic indexing between a one-dimensional array and list, the capabilities are identical
* When using two-dimensional arrays and lists, the advantages of arrays are clear, as lists present more verbose syntax
  *  ![List vs NP Array Indexing](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Array-indexing-capabilities.PNG "List vs NP Array Indexing")

#### 4. NumPy Array Boolean Indexing
*  ![NumPy Array Boolean Indexing](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Array-boolean-indexing.PNG "NumPy Array Boolean Indexing")
