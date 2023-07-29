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
* Examples of flat files: .txt, .csv (Excel files are not flat files, as they can contain many sheets)

### Importing flat files using NumPy
* If you now want to import a flat file and assign it to a variable, and all the data is numerical, you can use the package numpy to import the data as a numpy array
* Numpy arrays are the Python standard for storing numerical data, and they can leverage other packages e.g. scikit-learn for ML

#### Importing using np.loadtxt()
* Syntax:
<br> `data = np.loadtxt(filename, delimiter=',', skiprows=1, usecols=[0, 2])`
* `skiprows` is used when there is a string header, and `usecols` defines the columns you want e.g. 1st and 3rd columns
* To read all data as strings: `data = np.loadtxt(filename.txt, delimiter=',', dtype=str)`
* np.loadtxt() performs well for basic cases, but tends to break when we have columns having mixed datatypes
* The best library for such situations is Pandas, the Python standard for importing flat files as dataframes

### Importing Other File Types
* Pickle files
   * Are Python objects (e.g. ML models, lists) which are serialized (converted to sequence of bytes, or bytestream)
   * To import:
   <br> `import pickle`
   <br> `with open('filename.pkl', 'rb') as file:`
   <br> `data=pickle.load(file)`
   <br> `print (data)`
    * `rb` specifies that the file is both read only (r) and binary(b)

* Excel Spreadsheets
   * Commonly used file type
   * To import:
   <br> `data = pd.ExcelFile(filename) ` # read Excel file to data variable
   <br> `print(data.sheet_names) ` # print sheets in file
   <br> `df1 = data.parse('sheet1') ` # create dataframe using sheet name
   <br> `df2 = data.parse(0) ` # create dataframe using sheet index

* SAS (Statistical Analysis System) Files
   * Mostly used in in business analytics and biostatistics
   * Most common SAS files have extensions .sas7bdat (dataset files) and .sas7bcat (catalog files)
   * To import the dataset files:
     <br> `from sas7bdat import SAS7BDAT`
     <br> `with SAS7BDAT('filename.sas7bdat') as file:`
     <br> `df_sas = file.to_data_frame()`

* Stata (Statistics + Data) Files
   * Mostly used in academic social sciences research, such as economics and epidemiology
   * Have extension .dta
   * To import:
     <br> `data = pd.read_stata('filename.dta')`

* HDF5 (Hierarchical Data Format version 5) Files
   * Used for storing large quantities of numerical data (100s of GBs/TBs).
   *  HDF5 itself can scale up to exabytes
   * To import:
     <br> `import h5py`
     <br> `data = h5py.File('filename.hdf5', 'r')`
   * To access the structure of the file, you use same method as that of a dictionary:
     <br> `for key in data.keys():`
     <br> `print(key)` # the results are HDF groups, which are analogous to directories
   * To find the data in one HDF group:
     <br> `for key in data['group1'].keys():`
     <br> `print(key)` # returns columns
   * To access the values as a numpy array:
     <br> `print(np.array(data['group1']['column1'])`

*  
