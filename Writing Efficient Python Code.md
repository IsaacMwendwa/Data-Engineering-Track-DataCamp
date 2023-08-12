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
