<h1>mla-c01-notes</h1>
This repository contains notes for the AWS Certified Machine Learning Engineer - Associate Course MLA-C01.

<h1>Domains</h1>
<h2>Domain 1:</h2> Data Preparation for Machine Learning (ML) (28%)

<h3> Section 1: Data Ingestion and Storage</h3>

<b>Types of Data</b>
Structured - Data that is roganized in a defined manner or schema, typically found in relational databases.
- Easy to query
- Organized in rows and columns
- Has a consistent structure
- Example: SQL, CSV, Excel spreadsheets.

Unstructured Data - Data that does not have a predefined structured.
- Not easy querable.
- May come in various formats.
- Vides, audio files, text files.

Semi-structured Data - Data that is not organzied as structured data but has some level of structurte in the form of tags, hierarchies, or other patterns. Need a little more work to become structured.
- XML and JSON files.
- Log files.

<b> Properties of Data </b>

Volume - Amount of data or size of data organizations are dealing with at any given time.

Examples: social media platforms processing terabytes of datya daily from user posts, images, and videos.

Velocity - Refers to the speed at which a enw data is generated, collected, and processed. 

- Requires real-time or near-real-time processing capabilitites.
- Rapid ingestion and processing can be critical for certain applications.
    
Variety - Refers to the type of data.

<b>Data Warehouses</b>

A centralized repository optimized for analysis where data from different sources is stored in a structured format. 

- Designed for complex queries and analysis. 
- Data is cleaned, transforms, and loaded (ETL process- EXTRACT, TRANSFORM, LOAD).
- Schema-on-write (predefined schema before writing data).
- Primarily stores structured data.
- Less agile.
- More expensive.
- Example: Amazon Redshift. 

<b>Data Lake</b>

A storage repository that holds large amounts of raw data in its native format. 

- Schema-on-read (schema is defined at the time of reading data) <u>ELT - Extract, Load and Transform</u>.
- Can store structured and unstructured data.
- More agile.
- Cost effective storage solution.
- Example: Amazon S3.

<b>Data Lakehouse</b>

A hyrbrid data architecture that <u>combines the best features of data lakes and data warehouses</u>, aiming to provide the performance, reliability, and capabiliies of a data warehouse while maintaining the flexibility, scale, and low cost storage of data lakes.

-  Supports both structured and unstructured data.
- Allows for schema-on-write and schema-on-read.
- Provides capabilities for both detailed analytics and machine learning tasks.
- Typically built on top of cloud or distributed architectures. 
- Examples: AWS Lake Formation (with S3 and Redshift Spectrum).

<b>Data Mesh</b>

Data Mesh is a data architecture approach where data is owned and managed by the teams that use it, not a centralized IT department.

- It's more about governance and organization.
- aka "Domain-based data management"

<b>ETL Pipelines</b>

ETL is a process used to move data from source systems and into a data warehouse. 

Extract - Retrieve data from source systems such as: Databases, CRMs, flat files, APIs, or other data repositories. Ensure data integrity during the extraction phase. Can be done in real-time or in batches, depending on requirements.

Transform - Convert extracted data into a format suitable for the target data warehouse. 
- Datra cleansing (removing duplicates, fixing errors).
- Data enrichment (adding additional data from other sources).
- Format changes.
- Aggregation or computations.
- Encoding or decoding data.

Load - Move transformed data into the target data warehouse or another data repository. Ensure data mantains its integrity during the loading phase.

This pricess