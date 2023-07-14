## Database Design
* Schemas - how should data be logically organized
* Normalization - should my data have minimal dependency and redundancy
* Views - wht joins will be done most often
* Access control - should all users oif dB have same level of access
* DBMS - how do I pick between SQL and NoSQL options

### Approaches to Processing Data
1. OLTP vs OLAP
* OLTP data is stored in an Operational Database, which is pulled and cleaned to create an OLAP Data Warehouse
  
![OLTP vs OLAP](https://github.com/IsaacMwendwa/Data-Engineering-Track-DataCamp/blob/main/Images/OLTP-vs-OLAP.PNG "OLTP vs OLAP")

2. Structuring Data
    * Structured Data - Follows a schema; with defined data types and relationships e.g SQL dB
    * Unstructured Data - Schemaless, and most common data of real world e.g media files - photos, chast logs, mp3
    * Semi-structured Data - does not follow larger schema, hence has a self-describing structure e.g NoSQL, XML, JSON

4. Storing Data
* Data Warehouses
    * Optimized for read-only analytics (OLAP)
    * Combine data from multiple sources and use massively parallel processing for faster queries (MPP)
    * In their dB design, they typically used dimensional modelling and a denormalized schema
    * DWh solutions include: Amazon Redshift, Google Big Query, and Azure SQL DWh
    * Data mart is a subset of DWh, dedicated to a specific topic for a department
