Data Intensive App - Data management is one of the primary challenges in developing the application
Computer Intensive App - Challenge is parallelizing a very large computation

General things we need to do in applications:
1. Store data
2. Cache data
3. Allow users to search by keyword or filter (search indexes)
4. Stream processing - handle events and data changes as soon as they occur
5. Batch Processing - Periodically crunch a large amount of accumulated data

Operational Systems:
Consist of the backend services and data infra where data is created (eg by serving external users). App code can read and modify the data

Analytical Systems:
Serve the needs of business analysts and data scientists. They contain a read-only copy of the data from the operational systems, and they are optimized for the types of data processing that are needed for analytics

Data Warehouse:
A separate database that analysts can query, without affecting OLTP operations
Contains only read-only copy from all the various OLTP systems in the company. Data is extracted from OLTP databases, transformed into an analysis-friendly schema, cleaned up, and then loaded into the data warehouse. This process of getting data into the data warehouse is known as ETL. 
![[Pasted image 20261008154806.png]]


Data Lake:
A Centralized data repository that holds a copy of any data that might be useful for analysis, obtained from operational systems via ETL process.
It only contains files, without imposing any particular file format, data model, or schema

Cloud vs self-host:
1. Competitive advantage should be in-house
2. non-core, routine, or commonplace should be left to a vendor.
3. Middle-ground: off the shelf software that you self host, or deploy yourself.



