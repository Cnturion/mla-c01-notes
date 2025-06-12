<h1>mla-c01-notes</h1>
This repository contains notes for the AWS Certified Machine Learning Engineer - Associate Course MLA-C01.

<h1>Domains</h1>
<h2>Domain 1: Data Preparation for Machine Learning (ML)</h2>

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

<b>Storage Classes Comparison</b>

![image alt](https://github.com/Cnturion/mla-c01-notes/blob/67880fe7e4a05f0a039f0e95a9b258ce7f2d9495/Images/S3StorageClasses.png)

<h5>S3 Encryption</h5>

Four methods of object encryption:

- <b>Server-Side Encryption with Amazon S3-Managed Keys (SSE-S3)</b>
    - enabled by default. 
    - key managed by AWS
    - Encryption type AES-256.
- <b>Server-Side Encryption with KMS key stored in AWS KMS (SSE-KMS)</b>
    - leverages AWS KMS to manage encryption keys.
- <b>Server-Side Encryption with Customer-Provided Keys (SSE-C)</b>
    - customer manages their own encryption keys. 
    - amazazon does not store the customer encryption key.
    - HTTPS must be used.
- <b>Server-Side Encryption - Client Side Encryption</b>
    - clients must encrypt data themselves before sending to Amazon S3.
    - clients must decrypt data themselves when retrieving from Amazon S3.
    - customer manages encryption keys and cycle. it's their keys. 

<h5>S3 Access Points</h5>

![image alt](https://github.com/Cnturion/mla-c01-notes/blob/main/Images/s3-access-point.png?raw=true)

![image alt](https://github.com/Cnturion/mla-c01-notes/blob/main/Images/s3-access-point-2.png?raw=true)

<h4>Elastic Block Storage (EBS) Volumes</h4>

- Netwrok drive that can be attached to instances while they run.
- Can only be mounted to 1 instance at a time.
- Bound to a specific AZ.
- "Network USB Stick"
- Uses the netowkr to communicate the instance, which means there may be latency.
- Has a "delete on termination" option. Deletes the EBS when an instance is terminated. Disabled by default.

<h4>EBS Elastic Volumes</h4>

- You don't have to detach a volume or restart your instance to change it.
- Just go to action / modify volume from the console.
- Volume size can be increased but not decreased.
- Supports changing volume tupes  such as gp2 to gp3, specify desired IOPS. 

<h4>Elastic File System (EFS)</h4>

- Managed NFS that can be mounted on many EC2s.
- It's multi-AZ.'
- Highly available, scalable, expensive.
- Use cases: content management, web serving, data sharing, Wordpress.
- Uses NFSv4.1 protocol.
- Uses SG to control access to EFS.
- Compatible with Linux AMIs, not windows. 
- Supports KMS encryption/ 
- Scalable. billed by Gbs used. 

<h4>FSx</h4>

- Allows you to launch third party high-performance file systems on AWS as a fully managed service.

<h5>Amazon Fsx for Windows (File Server)</h5>

- Support SMB protocol & Windows NTFS.
- Integrates with Windows AD.
- Can be mounted on Linux EC2s.
- Can be accessed from on-prem via VPC or Direct connect. 

<h5>Amazon FSx for Lustre</h5>

- Lustre is a type of parallel distributed file system, for large-scale computing.
- Used for machine learning, HPC, video processing, financial modeling, etc..
- Scales up to 100 GB/s, millions of IOPS, sub-ms latencies.
- seamless integration with S3. can read s3 as a file system through FSx. 
- Can be accessed from on-prem via VPC or Direct connect.

<h5>FSx Deployment Options</h5>

<b>Scratch File System</b>

- Temporary storage.
- Data is not replicated (does not persist if file server fails).
- Used for short-term processing, optimizes costs.

<b>Persistent file System</b>

- Long term storage
- Data is replicated within same AZ.
- Replace failed files within minutes.
- Usage: long terma processing, sensitive data.

<h5>Amazon FSx for NetApp ONTAP</h5>

- File system compatible with NFS, SMB, iSCSI protocol.
- Move workloads running on ONTAP or NAS to AWS.
- Works with many OSs (Linux, macOS, Windows, VMWare Cloud, ECS, EKS, etc).
- Storage scales up and down automatically. 
- supports point-in-time instantaneous cloning- helpful for testing. 

<h5>Amazon FSx for OpenZFS</h5>

- Move workloads running on ZFS to AWS.
- supports point-in-time instantaneous cloning- helpful for testing. 

<h4>Amazon Kinesis Data Streams</h4>

- Collects and stores streaming data in real-time.
- real-time data = click streams, IoT devices, Metrics & logs from servers, etc.
- Uses producers. This can be application that push data from point a to Amazon Kinesis Data Streams. 
- Data is retained between up to 365.
- Data can't be deleted from Kinesis -- until it expires.
- Supports at-rest KMS encryption, in flight HTTPS encryption. 
- <b> 1 MB message size limit.</b>

![image alt](https://github.com/Cnturion/mla-c01-notes/blob/main/Images/amazon-kinesis-data-streams.png?raw=true)

<h4>Amazon Data Firehose</h4>

- A service used to send data from sources to target destinations.
- Gets data from applications, clients, SDKs, Kinesis Agents, Kinesis data streams, Amazon cloudwatch logs and events, AWS IoTs, etc. 
- For data transformation, it can use lambda functions (ex convert CSV to JSON).
- Fully managed service.
- Nearl-real-time service with buffering capability based on size / time.
- Support data from CSV, JSON, parquet, Raw Text, binary data.

![image alt](https://github.com/Cnturion/mla-c01-notes/blob/main/Images/data-firehose.png?raw=true)

![image alt](https://github.com/Cnturion/mla-c01-notes/blob/main/Images/kinesis-data-stream-vs-data-firehose.png?raw=true)

<h4>Amazon Managed Streaming for Apache Kafka (Amazon KMS)</h4>

- MSK is a fully managed service for Apache Kafka on AWS.
    - allows to create, update, delete clusters.
    - MSK creates and manages kafka brokers nodes and zookeper nodes.
    - Deploy the MSK cluster in VPC, multi-AZ (up to 3 AZs)
- Custom configurations can be created for clusters.
- alternative to Kinesis.
- Supports TLS between brokers. Can be disabled.
- CloudWatch Metrics monitoring:
    - Basic monitoring
    - Enhanced monitoring
    - Topic-level monitoring
- <b> 1 MB message size by default, can be configured to higher.</b>

<h5>MSK Features</h5>

<b>MSK Connect</b> is a framework to take data from Kafka and move it somewhere else and vice versa. It is a managed service that provides managed workers on AWS with auto-scaling capabilities.
Can be configured ar MSK Connect connectors to S3, Redshift, Opensearch, etc...

<b>MSK Serverless</b> Run Apache kafka on MSK without managing the capacity. Fully managed service.


<h2>Domain 2: Data Transformation, Integrity, and Feature Engineering</h2> 

<h4> What is EMR?</h4>

- Elastic MapReduce- manages hadoop framework on EC2 instances.
- Includes Spark, HBase, Presto, Flink, Hive & more.
- EMR Notebooks
- Has several integration points with AWS.

<b>EMR Cluster</b> is a collection of EC2 instances. Each instance is called a "node", and each node has a role within the cluster which is called a "node type".

![image alt](https://github.com/Cnturion/mla-c01-notes/blob/main/Images/EMR-cluster.png?raw=true)