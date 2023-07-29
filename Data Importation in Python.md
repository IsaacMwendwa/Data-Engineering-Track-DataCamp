# Importation of Data from Flat Files

## Reading text files
* Syntax:
<br> `file = open('filename.txt', mode='r')`
<br> `text=file.read()`
<br> `file.close`

* You can avoid having to close the file using a context manager, defined using with statement:
<br> `with open('filename.txt', 'r') as file:`
<br> `print(file.read())` # to display all text
<br> `print(file.readLine())` #to display one line

* Flat files are basic text files containing records, that is, table data, without structured relationships.
* This is in contrast to a relational database, in which columns of distinct tables can be related.
* Examples of flat files: .txt, .csv

### Importing flat files using NumPy
* If you now want to import a flat file and assign it to a variable, and all the data is numerical, you can use the package numpy to import the data as a numpy array
* Numpy arrays are the Python standard for storing numerical data, and they can leverage other packages e.g. scikit-learn for ML

#### Importing using np.loadtxt()
* Syntax:
<br> `data = np.loadtxt('filename.txt', delimiter=',', skiprows=1, usecols=[0, 2])`
* `skiprows` is used when there is a string header, and `usecols` defines the columns you want e.g. 1st and 3rd columns
