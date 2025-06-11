<h1>mla-c01-notes</h1>
This repository contains notes for the AWS Certified Machine Learning Engineer - Associate Course MLA-C01.

<h1>Domains</h1>
<h2>Domain 1:</h2> Data Preparation for Machine Learning (ML) (28%)

<h3> Section 1: Data Ingestion and Storage</h3>

<h4>Types of Data</h4>
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

<h4> Properties of Data </h4>

Volume - Amount of data or size of data organizations are dealing with at any given time.

Examples: social media platforms processing terabytes of datya daily from user posts, images, and videos.

Velocity - Refers to the speed at which a enw data is generated, collected, and processed. 

- Requires real-time or near-real-time processing capabilitites.
- Rapid ingestion and processing can be critical for certain applications.
    
Variety - Refers to the type of data.

<h4>Data Warehouses</h4>

A centralized repository optimized for analysis where data from different sources is stored in a structured format. 

- Designed for complex queries and analysis. 
- Data is cleaned, transforms, and loaded (ETL process- EXTRACT, TRANSFORM, LOAD).
- Schema-on-write (predefined schema before writing data).
- Primarily stores structured data.
- Less agile.
- More expensive.
- Example: Amazon Redshift. 

<h4>Data Lake</h4>

A storage repository that holds large amounts of raw data in its native format. 

- Schema-on-read (schema is defined at the time of reading data) <u>ELT - Extract, Load and Transform</u>.
- Can store structured and unstructured data.
- More agile.
- Cost effective storage solution.
- Example: Amazon S3.

<h4>Data Lakehouse</h4>

A hyrbrid data architecture that <u>combines the best features of data lakes and data warehouses</u>, aiming to provide the performance, reliability, and capabiliies of a data warehouse while maintaining the flexibility, scale, and low cost storage of data lakes.

-  Supports both structured and unstructured data.
- Allows for schema-on-write and schema-on-read.
- Provides capabilities for both detailed analytics and machine learning tasks.
- Typically built on top of cloud or distributed architectures. 
- Examples: AWS Lake Formation (with S3 and Redshift Spectrum).

<h4>Data Mesh</h4>

Data Mesh is a data architecture approach where data is owned and managed by the teams that use it, not a centralized IT department.

- It's more about governance and organization.
- aka "Domain-based data management"

<h4>ETL Pipelines</h4>

ETL is a process used to move data from source systems and into a data warehouse. 

Extract - Retrieve data from source systems such as: Databases, CRMs, flat files, APIs, or other data repositories. Ensure data integrity during the extraction phase. Can be done in real-time or in batches, depending on requirements.

Transform - Convert extracted data into a format suitable for the target data warehouse. 
- Datra cleansing (removing duplicates, fixing errors).
- Data enrichment (adding additional data from other sources).
- Format changes.
- Aggregation or computations.
- Encoding or decoding data.

Load - Move transformed data into the target data warehouse or another data repository. Ensure data mantains its integrity during the loading phase.

This process must be automated in some reliable way. <b>AWS Glue</b> is a serverless data integration service that allows you to discover, prepare, and load data for various analytics, machine learning, and application development needs.

<h4>Amazon S3</h4>

Types of PutObjects events

- <b>Multi-Part upload:</b>
    - recommended for files > 100MB and Required for files over 5 GB.
    - Can help parallelize uploads (speed up transfers).

- <b>S3 Transfer Acceleration</b>
    - Increase transfer speed by transfering files to an AWS edge location which will forward the data to the S3 bucket in the target region.
    - Compatible with multi-part upload. 
    - File is publicly uploeaded to the edge location. From Edge Location to S3 uses private AWS network.

Types of Get or read objects

- <b>S3 Byte-Range Fetches</b>
    - Parallelize GETs by requesting specific byte ranges.
    - Better resilience in case of failures.
    - Can be used to speed up downloads. 

<h5>S3 Encryption</h5>