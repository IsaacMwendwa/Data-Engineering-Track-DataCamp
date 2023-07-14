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
