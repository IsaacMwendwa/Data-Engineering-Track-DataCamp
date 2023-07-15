## Database Design
* Schemas - how should data be logically organized (database blueprint)
* Normalization - should my data have minimal dependency and redundancy
* Views - wht joins will be done most often
* Access control - should all users oif dB have same level of access
* DBMS - how do I pick between SQL and NoSQL options

### Database Design Concepts
1. Approaches to Processing Data: OLTP vs OLAP
* OLTP data is stored in an Operational Database, which is pulled and cleaned to create an OLAP Data Warehouse
  
![OLTP vs OLAP](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/OLTP-vs-OLAP.PNG "OLTP vs OLAP")

2. Structure of Data
    * Structured Data - Follows a schema; with defined data types and relationships e.g SQL dB
    * Unstructured Data - Schemaless, and most common data of real world e.g media files - photos, chast logs, mp3
    * Semi-structured Data - does not follow larger schema, hence has a self-describing structure e.g NoSQL, XML, JSON

3. Storing Data
* Data Warehouses
    * Optimized for read-only analytics (OLAP)
    * Combine data from multiple sources and use massively parallel processing for faster queries (MPP)
    * In their dB design, they typically used dimensional modelling and a denormalized schema
    * DWh solutions include: Amazon Redshift, Google Big Query, and Azure SQL DWh
    * Data mart is a subset of DWh, dedicated to a specific topic for a department
* Data Lakes
    * Store all types of data (e.g raw, operational dBs, non-relational) at a lower cost, as it uses object storage as opposed to traditional block/file storage
    * Are massive (spanning petabytes), owing to the scalability of unstructured data
    * Data Lakes are schema-on-read, meaning the schema is created as data is read. Warehouses and traditional databases are classified as schema-on-write because the schema is predefined.
    * Data lakes have to be organized and cataloged well; otherwise, it becomes an aptly named "data swamp."
    * Not only used for storage, can also be used for big data analytics using tools e.g Apache Spark and Hadoop
* Data Pipelines: ETL vs ELT
    *  ETL is the more traditional approach for warehousing and smaller-scale analytics, conversely ELT has become common with big data projects
    *  In ETL, data is transformed before loading into storage - usually to follow the storage's schema, as is the case with warehouses
    *   In ELT, the data is stored in its native form in a storage solution like a data lake. Portions of data are transformed for different purposes, from building a data warehouse to doing deep learning

### Database Design
There are two important concepts to know when it comes to database design: Database models and schemas. 
* Database models are high-level specifications for database structure. The relational model is the most popular, used for creating relational dBs
* The relational model defines rows as records and columns as attributes
* A Schema is a database's blueprint (i.e an implementation of the dB model), which adds granularity to logical structure through tables, fields, relationships, views

### Data Modeling
Is the first step of dB design, which has three levels:
1. Conceptual Data Model -> describes what dB contains, e.g entities, relationships, attributes. Tools used: data structure diagrams e.g E-R & UML diagrams
2. Logical Data Model -> decides how these entities and relationships map to tables. Tools used: dB models and schemas e.g relational model and star schema
3. Physical Data Model -> looks at how data will be physically stored at the lowest level of abstraction. Tools used: partitions, CPUs, indexes, backup systems, tablespaces

### Beyond Relational Model
1. Star Schema
* Dimensional modeling is an adaptation of the relational model specifically for data warehouses.
* It's optimized for OLAP type of queries that aim to analyze rather than update. To do this, it uses the Star Schema
* The schema of a dimensional model tends to be easy to interpret and extend. This is a big plus for analysts working on the warehouse.
* Dimensional models are made up of two table types:
    * Fact Tables: holds records of a key metric, which changes often. Connections to dimensions via foreign keys
    * Dimension Tables: holds descriptions of specific attributes, which don't change as often

2. Snowflake Schema
* Is an extension of the star schema, hence it has more tables
* The fact table is the same, but the way the dimension tables are structured is different.
* The star schema extends one dimension, while the snowflake schema extends over more than one dimension
* This is because the dimension tables are normalized
* Normalization is a DB design technique that divides tables into smaller tables and connects them via relationships, hence reducing redunancy and increasing data integrity
* Normalization is achieved by identifying repeating groups of data and creating new tables for them
<br>Process:
    * ![Normalizing Star Schema To Snowflake](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Normalizing-Star-Schema-To-Snowflake.PNG "Normalizing Star Schema To Snowflake")
    * Adding foreign keys to fact table: `ALTER TABLE fact_booksales ADD CONSTRAINT sales_book FOREIGN KEY (book_id) REFERENCES dim_book_star (book_id);`
    * Extend book dimension from star to snowflake schema:
        * Create new table for dim_author_sf with column for author: `CREATE TABLE dim_author_sf (author varchar(256)  NOT NULL);`
        * Insert all distinct authors from dim_book_star into dim_author_sf: `INSERT INTO dim_author_sf SELECT DISTINCT author FROM dim_book_star;`
        * Add primary key to dim_athor_sf: `ALTER TABLE dim_author_sf ADD COLUMN author_id SERIAL PRIMARY KEY;`
        * View new table: `SELECT * FROM dim_author_sf;`

### Evaluation of Database Normalization
* Advantages
  * Normalization eliminates data redundancy, saving on storage
  * Better data integrity- accurate and consistent data due to easier updates

* Disadvantages
    * Complex queries due to more joins, which require more CPU
* N/B: OLTP (eg. operational dBs) are write-intensive, meaning that we prioritize quicker & safer insertion of data, hence we choose Normalization
* OLAP (eg. Data Warehouses) are read-intensive, meaning we prioritize quicker queries for analytics, hence we choose Denormalization

### Normal Forms
-> Are extents to which you can normalize
1. 1NF
* Each record must be unique, and each cell (column) must hold one value
  
2. 2NF
* Must satisfy 1NF, and:
    *  If primary key is 1 col --> automatically 2NF
    *  if there is a composite primary key --> then each non-key col must be dependent on all keys  
 
3. 3NF
* Must satisfy 2NF, and no transitive dependencies i.e non-key cols can't depend on other non-key cols

### Data Anomalies
* A database that isn't normalized enough is prone to three types of anomaly errors: update, insertion, and deletion
* To avoid these errors, it's best to normalize to 3NF

1. Update Anomaly
    * Is a data inconsistency that can arise when updating a database with redundancy.
    * Need to update more than one record, else there will be inconsistency. User updating needs to know about the redundancy
  
2. Insertion Anomaly
    * Is when you are unable to add a new record due to missing attributes.
    * Occurs due to dependencies between columns in the same table unintentionally restricting what can be inserted into the table

4. Deletion Anomaly
    * Happens when you delete a record and unintentionally delete other data

## Database Views

* A view is the result set of a stored query on database. It is a virtual table, hence not stored in physical memory
* Created as: `CREATE VIEW view_name AS you_query`
* Benefits:
    * Doesn't take up storage, except for query itself (which is minimal)
    * Form of access control - hide sensitive columns and restrict what user can see
    * Masks complexity of queries -- useful for highly normalized schemas

### Granting/Revoking Access to a View
* Syntax: `GRANT/REVOKE privilege(s) ON object TO/FROM role`
    * Where privileges --> SELECT, INSERT, UPDATE, DELETE; Objects --> table, view, schema; Roles --> dB user or group of dB users
* While you can update/insert records using views, it's best to leave them only for reads, not writes
* To drop a view: `DROP VIEW view_name CASCADE/RESTRICT`
    * Where RESTRICT returns an error when there are dependencies; and CASCADE drops views and dependent objects

### Types of Views
1. Non-materialized views -- referred to as views, which are virtual (only query stored, not results)
2. Materialized Views - store the query results on disk, not the query itself
* MVs are refreshed/rematerialized when prompted or scheduled
* MVs are used when queries have long execution time (hours), and in data which is not updated often
* They're also useful in data warehouses (OLAP), which are not write-intensive, hence less risk of outdated data
* Syntax for creating MVs: `CREATE MATERIALIZED VIEW my_mv AS my_query;`, and can be refreshed using `REFRESH MATERIALIZED VIEW my_mv;`
* You can also schedule MVs using cron - the UNIX based job scheduler
* Managing dependencies between multiple MVs is achieved using Directed Acyclic Graphs (DAGs), which keep track of views
* Pipeline scheduler tools e.g Airflow and Luigi, are used to schedule and run REFRESH statements
* A DAG is a finite directed graph with no cycles

## Database Partitioning
* When tables grow to 100s of gigabytes or even terabytes, queries tend to become slow
* Even when we've set indices correctly, these indices can become so large they don't fit into memory
* At a certain point, it can make sense to split a table up into multiple smaller parts. This is the process called 'partitioning'
* Partitioning fits into the physical data model, as we distribute the data over several physical entities
* Two types of partitioning:
    * Vertical Partitioning - splits up a table vertically by its columns, even when it's already fully normalized
    * Horizontal Partitioning - splits up tables over the rows, e.g by splitting data using timestamp. Can be partitioned by range, list etc
* Example query of H. partitioning in PostgreSQL by RANGE:
     ![Horizontal Partitioning](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/Horizontal-Partitioning.PNG "Horizontal Partitioning")

Advantages of H. Partitioning
* Can help by optimizing indices, increasing the chance that heavily-used parts of the index fit in memory
* You can move rarely accessed partitions to a slower medium, and vice versa
* Can benefit both OLAP and OLTP

Disadvantages of H. Partitioning
* Partitioning existing tables can be a hassle: you have to create a new table and copy over the data
* We can not always set the same type of constraints on a partitioned table, for example, the PRIMARY KEY constraint

#### Sharding
* We can take partitioning one step further and distribute the partitions over several machines
* When horizontal partitioning is applied to spread a table over several machines, it's called sharding
* This brings the concept of massively parallel processing (MPP) databases, where each node, or machine, can do calculations on specific shards

## Data Integration
* Data Integration is the process of combining data from different sources, formats, technologies to provide users with a translated and unified view of that data
* When building the unified data model, you need to enforce data governance
* Thus you need to consider lineage: for effective auditing, you should know where the data originated and where it is used at all times

## NoSQL DBMS
1. Key-Value Stores
* Stores combinations of keys and values
* The key serves as a unique identifier to retrieve an associated value. Values range from simple objects, like integers or strings, to more complex objects, like JSON structures
* They are most frequently used for managing session information in web applications e.g managing shopping carts for online buyers.
* An example DBMS is Redis

2. Document Stores
* Document stores are similar to key-value in that they consist of keys, each corresponding to a value
* The difference is that the stored values, referred to as documents, provide some structure and encoding of the managed data.
* That structure can be used to do more advanced queries on the data instead of just value retrieval.
* A document database is a great choice for content management applications such as blogs and video platforms. Each entity that the application tracks can be stored as a single document.
* An example of a document store DBMS is MongoDB

3. Columnar Databases
* Rather than grouping columns together into tables, columnar databases store each column in a separate file in the system’s storage
* This allows for databases that are more scalable, and faster at scale.
* Use a columnar database for big data analytics where speed is important
* An example is Cassandra
  
4. Graph Databases
* Here, the data is interconnected and best represented as a graph
* This method is capable of lots of complexity
* Graph databases are used by most social networks and pretty much any website that recommends anything based on your behavior
* An example of a graph DBMS is Neo4j.
