# Software Engineering for Data Scientists in Python

## Introduction
* Three topics in particular that we'll cover are modularity, documentation, and testing.
* Modularity implies dividing code into shorter functional units, which are more readable, maintainable and portable
  * We can write modular code in python by leveraging packages, classes, and methods
* Documentation includes using comments, docstrings, and self-documenting code to document your Data Science python projects
* Testing can both be manual and automated:
  * It's definitely worthwhile to perform manual tests
  * But leveraging tools like the `pytest` package can automatically run and re-run your tests to ensure your code is working as intended even after adding new functionality
* 'Python Package Index' (PyPi) gives us an easy platform to leverage published packages
* Thanks to packages being modular, we can easily install them from PyPi using a tool called `pip`
* `pip` is a recursive acronym that stands for 'Pip Installs Packages', and it does just that
* To read documentation of packages/dtypes, use `help(object_name)`

#### Conventions and PEP 8
* PEP 8 is the defacto Style Guide for Python Code
* It lets us know how to format our code to be as readable as possible, and to quote PEP 8, 'code is read much more often than it is written'
* To ensure your code keeps up with PEP 8, you can use:
  * an IDE that flags violations of bad lines of code
  * `pycodestyle` package - checks code in multiple files at once and it outputs descriptions of the violations along with information to let you know exactly where you need to go to fix the issue
    * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/c105a37a-e528-45f9-9d59-9fab8b65b050)
* Using pycodestyle in editor:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/0f4ef34c-2fdc-42f0-841b-7770cb9fa355)

## Writing a Python Module
### Writing Python Packages
* A minimal python package consists of 2 elements: a directory and a python file
* The name of the directory will be the name of the package, but how should you name it?
  * PEP 8 states that packages should have short, all-lowercase names
  * The use of underscores in a package name is discouraged, but you can and should use them if it improves readability
  * It's ideal to pick a name that conveys the functionality of the package
* The file in our newly branded directory doesn't have any flexibility in naming
* We must name it underscore underscore init underscore underscore dot py (`__init__.py`)
* This file lets Python know that the directory we created is a package
* With this structure we've created a package that we can import just like we would import numpy or any other package
* To import a local package, we need to establish it's path:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/8a7efac2-ee8d-4d01-930d-4d619b693d12)
* To import (if package and your script are in same directory):
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/25cf50f6-3ce0-4cd3-8139-190bf6f46ec8)
* To add functionality to the package, we start by adding a .py file in package directory:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/2b3359c7-8c88-45ff-a1ee-79bac7ed2301)
* To add the functionality and access it:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/5d3ee36e-99a8-4d3b-9514-40508cc60781)
* Alternative to access the functionality:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/7a86df97-bd20-4e8b-a18c-79deb3163853)
* To extend package structure:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/0029ead8-0759-4ef9-9101-584234e6e8e6)
* You can also extend package structure by building packages inside your package (subpackages):
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/fc073917-6ad5-4f62-b327-73dcbadd97ee)

### Making your package portable
* Now that you have a functional package you might want to share it with your colleagues
* The two main steps to sharing a python package are creating `setup.py` and `requirements.txt`
* These two pieces provide information on how to install your package and recreate its required environment
* These files list information about what dependencies you've used as well as allowing you to describe your package with additional metadata
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/1762377f-6b87-4dba-9018-881ea7dd3218)
* The contents of `requirements.txt`:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/c98ebfe7-cfea-422c-8e96-df4914eba6bd)
* The contents of `setup.py`:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/5fb4ea45-fbcd-4055-9d87-9f42e5b1e2bd)


