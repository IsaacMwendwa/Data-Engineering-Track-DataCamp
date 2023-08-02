# Data Importation in Python

## Reading flat files
* Flat files are basic text files containing records, that is, table data, without structured relationships.
* This is in contrast to a relational database, in which columns of distinct tables can be related.
* Examples of flat files: .txt, .csv (Excel files are not flat files, as they can contain many sheets)
* To import:
<br> `file = open('filename.txt', mode='r')`
<br> `text=file.read()`
<br> `file.close`

* You can avoid having to close the file using a context manager, defined using with statement:
<br> `with open('filename.txt', 'r') as file:`
<br> `print(file.read())` # to display all text
<br> `print(file.readLine())` #to display one line

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

## Importing Other File Types
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
     <br> `print(np.array(data['group1']['column1']))`

* MATLAB (Matrix Laboratory) Files
   * Is a numerical computing environment, which is the industry standard in engineering and science
   * Data is saved as .mat files
   * Data is read and written using Scipy's methods: scipy.io.loadmat(), and scipy.io.savemat()
   * To import:
     <br> `import scipy.io`
     <br> `mat = scipy.io.loadmat('filename.mat')`
   * The variable mat is a dictionary, with keys corresponding to MATLAB variable names, and values corresponding to objects assigned to variables
   * To access the keys: `print(mat.keys())`
   * To access one value: `print(mat['key1'])`

## Working with Relational Databases in Python
* Create a SQLite database engine from sqlachemy:
  <br> `from sqlachemy import create_engine`
  <br> `engine=create_engine('sqlite:///DatabaseName.sqlite')`
* To get table names: `engine.table_names()`
* To run SQL queries:
  <br> `con = engine.connect()`
  <br> `results = con.execute('SQL Query')`
  <br> `df = pd.DataFrame(results.fetchall())`
  <br> `df.columns=results.keys()` # defines the column names in df
  <br> `con.close()`
* To save the hussle of closing the connection, you can use the context manager as:
  <br> `with engine.connect as con:`
  <br> `results = con.execute('SQL Query')`
  <br> `df = pd.DataFrame(results.fetchall())` # or .fetchmany(10) to import 10 rows instead of all
  <br> `df.columns=results.keys()`
* You can achieve running SQL queries in a single line of code using Pandas:
  <br> `df = pd.read_sql_query('SQL Query', engine)`

## Importing Data From the Web
### Reading Flat Files from the Web
* Syntax:
  <br> `from urllib.request import urlretrieve`
  <br> `urlretrieve(url, 'path_to_save.csv')` # Saving file locally
  <br> `df = pd.read_csv(url, sep=';')` # Reading directly without saving

### Reading Non-flat Files from the Web
* Syntax:
  <br> `xls = pd.read_excel(url, sheet_name = None)` #To import all sheets, sheetname should be None
  <br> for k, v in xls.items(): print(k)   # To display sheet names
  
### Performing HTTP Requests using urllib
* Syntax:
  <br> `from urllib.request import urlopen, Request`
  <br> `request = Request(url)` # Packages the request
  <br> `response = urlopen(request)` # Sends the request and catches the response
  <br> `html = response.read()` # Extract the response
  <br> `response.close()`
  
### Performing HTTP Requests using requests (High Level)
* Syntax:
  <br> `import requests`
  <br> `r = requests.get(url)`
  <br> `text = r.text`
  
### Scraping the web in Python: BeautifulSoup
* Syntax:
  <br> `from bs4 import BeautifulSoup`
  <br> `import requests`
  <br> `r = requests.get(url)`
  <br> `html_doc = r.text`
  <br> `soup = BeautifulSoup(html_doc)`
  <br> `print(soup.prettify())` #printing soup
  <br> `for link in soup.find_all('a'): print(link.get('href'))` #printing all links in page

## Interacting with APIs to import data from the web
* An API is a set of protocols and routines for building and interacting with software applications

### Loading data using JSON
* Was invented for real-time server-to-browser communication
* Syntax:
  <br> `import json`
  <br> `with open('file.json', 'r')` as json_file:
  <br> `json_data = json.load(json_file)` # Returns a dict
* To pull data from an API using requests:
  <br> `r = requests.get(url)`
  <br> `json_data = r.json()`
  <br> `for key, value in json_data.items(): print(key + ':', value)`

* To use Python lists as counter for many variables:
  <br> `[clinton, trump, sanders, cruz] = [0, 0, 0, 0]` #  Initialize list to store tweet counts
  <br> `for index, row in df.iterrows():`
    <br> `clinton += word_in_text('clinton', row['text'])`
    <br> `trump += word_in_text('trump', row['text'])`
    <br> `sanders += word_in_text('sanders',row['text'])`
    <br> `cruz += word_in_text('cruz', row['text'])`
  * To get the counter list:
    <br> `y = [clinton, trump, sanders, cruz]` # Counter List
