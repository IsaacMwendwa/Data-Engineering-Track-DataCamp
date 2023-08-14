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
* Lists don't support broadcasting, hence operations on entire list require for loops/list comprehension
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

### Wrap it all
* ![Utilizing Range, Enumerate, Map](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Utilizing-range-enumerate-map.PNG "Utilizing Range, Enumerate, Map")

## Timing and Profiling Code
### Timeit
* `%timeit` is prefixed before single lines of code, and `%%timeit` is written in a new line before a block of code
* Timeit gives output based on the following metrics (listed from fastest to slowest):
   * ![Comparing runtime metrics](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/8a25d8bf-2a09-4b48-b0b3-e4a431820523 "Comparing runtime metrics")
* The number of runs represents how many iterations you'd like to use to estimate the runtime. The number of loops represents how many times you'd like the code to be executed per run
* To specify the arguments for 2 runs and 10 loops: `%timeit -r2 -n10 expression_to_time`
* A simple comparison of creating data structures using formal names and literal syntax shows that literal syntax is faster:
   * ![Formal names and literal syntax](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/50405132-8265-49dd-b2bd-4eb97902c2db "Formal names and literal syntax")

### Profiling Code
* %timeit works well with bite-sized code
* If we wanted to time a large code base or see the line-by-line runtimes within a function, we use code profiling
* Code profiling is a technique used to describe how long, and how often, various parts of a program are executed
* The beauty of a code profiler is its ability to gather summary statistics on individual pieces of our code without using magic commands like `%timeit`

#### Code profiling for runtime
* We will focus on the `line_profiler` package to profile a function's runtime line-by-line
* To install it: `pip install line_profiler`; and to use it, you load to environment as `%load_ext line_profiler`
* Syntax of usage: `%lprun -f name_of_function full_function_call(arg1, arg2)` # -f implies that we are profiling a function
    * ![lprun output](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/54c8849d-61a7-44e4-a45c-1de90e038609 "lprun output")
* Note that the total time reported when using %lprun and %timeit do not match. Remember, %timeit uses multiple loops in order to calculate an average and standard deviation of time, as compared to %lprun

#### Code profiling for memory usage
* Just like we've used code profiling to gather detailed stats on runtimes, we can also use code profiling to analyze the memory allocation for each line of code in our code base
* We'll use the `memory_profiler` package that is very similar to the `line_profiler` package
* To install: `pip install memory_profiler`
* Syntax of usage: `%mprun -f name_of_function full_function_call(arg1, arg2)
* One drawback to using %mprun is that any function profiled for memory consumption must be defined in a .py file and imported
* Steps:
    <br>`from filename.py import name_of_function`
    <br>`%load_ext memory_profiler`
    <br>`%mprun -f name_of_function full_function_call(arg1, arg2)`
