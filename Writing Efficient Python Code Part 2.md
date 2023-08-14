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
