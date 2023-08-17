# Software Engineering for Data Scientists: Part 2

## Utilizing Classes
* So far you've been able to create a fully portable Python package, and you've even added functionality to your package by utilizing functions
* We'll now look at how you can use classes to strengthen your package's functionality
* Object Oriented Programming, or OOP, is a great way to write modular code, and reap the benefits of modularity such as easily understood and extensible code
* Anatomy of a class is shown:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/e2e59f7f-b063-4db0-86e6-26ec404bf407)
* Similarly to your package's `__init__.py` file, this will initialize everything when a user wants to leverage your class
* Using a class in a package:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/241f7caf-771f-4aeb-8978-51bf028e4ba7)
* Note, nowhere in this script do we see the self-object that we used when defining our class
* To explain the self convention:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/5eb5e618-fd7a-4414-8236-b2baaf0894fa)
* Technically we can use a different word than self, but this a very strong PEP8 convention and not abiding by it will make your code very hard to read by your collaborators

 ### Adding Functionality to Class
* To make our class to be more useful, we can add more attributes & methods besides __init__
* For example, let's say that in our workflow we always want to tokenize our documents as a first step
* Tokenization is a common step in text analysis, it is the process of breaking up a document into individual words, also known as tokens
* __init__ is what's called when a user wants to create an instance of Document
* This would be a convenient location to put a tokenization step
* Placing the tokenization process inside of __init__ will ensure our Document is tokenized as soon as it is created, and this will save your user's the trouble of thinking about this step
* Example to add tokenization in Document class:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/42c6d07c-1b63-4925-bd87-a717dc0108aa)
* Adding _tokenize() method
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/6c590a02-1b7a-46c5-b68f-1f5eed456578)
* This brings the concept of Non-public methods:
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/3326328c-512d-41f4-8f22-40b2452876b8)
* The risks of using a non-public method in your own workflow include:
  * Little or no documentation
  * Unpredictability - function's input or output might change without warning when the developer updates their package

### Using inheritance to Create a Class
*The DRY Principle is a great rule for writing modular, readable code (Don't Repeat Yourself)
* In the case of extending the Document class to be a SocialMedia class, we can stay DRY by using the Object Oriented Programming concept of inheritance
* With inheritance, we start with a parent class and we pass on it's functionality to a child class
* The child class inherits all the methods and attributes of its parent, and we're able to add additional functionality without affecting the parent class
* Steps creating classes using inheritance:
  * First, we import the ParentClass for use in defining our ChildClass
  * To let Python know we're using inheritance, we pass the ParentClass as an argument in our class statement
  * ![image](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/assets/51324520/ee3483f7-b22d-483a-8151-030e03c72202)
