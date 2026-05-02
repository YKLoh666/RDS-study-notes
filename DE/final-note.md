# Data Engineering Final Note

- [Data Engineering Final Note](#data-engineering-final-note)
  - [Chapter 3: Apache Spark](#chapter-3-apache-spark)
    - [3.1 Introduction to Apache Spark](#31-introduction-to-apache-spark)
    - [3.2 Spark RDDs](#32-spark-rdds)
    - [3.3 Spark DataFrames](#33-spark-dataframes)
    - [3.4 User-Defined Functions (UDFs)](#34-user-defined-functions-udfs)
    - [3.5 Spark SQL](#35-spark-sql)
    - [3.6 Optimization Techniques](#36-optimization-techniques)
    - [3.7 Spark Architecture](#37-spark-architecture)
  - [Chapter 4: NoSQL Databases](#chapter-4-nosql-databases)
    - [4.1 Databases](#41-databases)
    - [4.2 Key-Value Stores](#42-key-value-stores)
    - [4.3 Document Stores](#43-document-stores)
    - [4.4 Graph Databases](#44-graph-databases)
    - [4.5 Column-Family Stores](#45-column-family-stores)
    - [4.6 NoSQL Database Strategies](#46-nosql-database-strategies)
  - [Chapter 5: Data Streaming](#chapter-5-data-streaming)
    - [5.1 Data Streaming](#51-data-streaming)
    - [5.2 Apache Kafka](#52-apache-kafka)
    - [5.3 Structured Streaming](#53-structured-streaming)
  - [Chapter 6: MapReduce](#chapter-6-mapreduce)
    - [6.1 MapReduce Overview](#61-mapreduce-overview)
    - [6.2 MapReduce Jobs](#62-mapreduce-jobs)
    - [6.3 Basic Types of MapReduce Jobs](#63-basic-types-of-mapreduce-jobs)
    - [6.4 MapReduce Patterns](#64-mapreduce-patterns)
  - [Chapter 7: Data Privacy and Security](#chapter-7-data-privacy-and-security)
    - [7.1 Data Privacy](#71-data-privacy)
    - [7.2 Security Design Principles](#72-security-design-principles)
    - [7.3 Primary Security Domains](#73-primary-security-domains)
    - [7.4 Best Practices for Data Security in Hadoop](#74-best-practices-for-data-security-in-hadoop)
      - [Passwords](#passwords)

## Chapter 3: Apache Spark

### 3.1 Introduction to Apache Spark

- Distributed computing framework for big data processing and analytics (Use multiple computers to process large datasets in parallel)
- Core Features:
  - **In-Memory Computing**: Store intermediate data in memory for faster processing
  - **Lazy Evaluation**: Delay execution until necessary, optimizing the execution plan
  - **Resilient Distributed Datasets (RDDs)**: Fault tolerant collections of objects that can be processed in parallel
  - **Multiple Language Support**: APIs for Java, Scala, Python and R
- Advantages:
  - **Speed**: Fast in-memory processing and lazy evaluation optimize execution
  - **Reusability**: Support both batch and stream data processing
  - **Unified Platform**: Enable data processing, machine learning and graph processing in a single framework
- Use Cases:
  - Big Data Processing
  - Machine Learning
  - Real-Time Stream Processing
  - Graph Analytics

### 3.2 Spark RDDs

- Immutable distributed collection, can be processed in parallel, fault-tolerant
- Characteristics:
  - Immutable, fault-tolerant, partitioned across cluster
  - Lazy evaluation (transformations are not executed until an action is called)
  - Keep track of lineage for fault tolerance (can recompute lost partitions)
- Types of Transformations:
  - **Narrow Transformations**: Each input partition contributes to only one output partition (e.g. `map`, `filter`)
    - Partition-level operations that do not require shuffling data across the cluster, allow parallel processing without data movement, resulting in faster execution.
  - **Wide Transformations**: Each input partition contributes to multiple output partitions (e.g. `join`, `groupBy`)
    - Dependency between partitions that requires shuffling data across the cluster, can lead to performance bottlenecks due to network I/O and disk I/O, especially with large datasets.
- Actions vs Transformations:
  - **Transformations**: Create new RDDs from existing ones, lazy evaluation (e.g. `map`, `filter`, `reduceByKey`)
  - **Actions**: Trigger execution of transformations and return results to the driver program (e.g. `collect`, `count`, `show`)

### 3.3 Spark DataFrames

- Abstract data structure built on top of RDDs, provides a higher-level API for structured data processing

### 3.4 User-Defined Functions (UDFs)

- Define column-based transformations in Spark DataFrames, allowing custom logic to be applied to DataFrame columns
- Example: `udf_upper = udf(lambda x: x.upper(), StringType())` to convert a string column to uppercase
- Able to leverage external libraries and complex logic

### 3.5 Spark SQL

- Module for structured data processing using SQL queries
- Example: `spark.sql("SELECT * FROM table WHERE age > 30")` to query a DataFrame registered as a temporary view

### 3.6 Optimization Techniques

- **Broadcast Variables**: Share read-only data across all nodes to avoid redundant data transfer
- **Accumulators**: Workers can update shared variables (e.g. counters) but not modify others' contributions
- **Caching**: When same RDD/DataFrame is reused, cache it in memory, avoid heavy recomputation such as `join` or `groupBy`
- **Checkpointing**: Save RDD/DataFrame to disk so it can be used in other spark sessions
- **Partitioning**: Split dataset into smaller chunks for parallel processing, optimize data shuffling and reduce network I/O

### 3.7 Spark Architecture

- Components
  - **Spark Driver**: Main program that allocates resources and distributes tasks to executors
  - **Spark Session**: Created inside the driver, entry point for Spark functionality, manages configuration and resources
  - **Cluster Manager**: Allocates resources across the cluster (e.g. YARN, Mesos, Kubernetes)
  - **Executors**: Worker nodes that execute tasks and store data in memory or disk
- Deployment Modes

  | Client Mode                                                                                                          | Cluster Mode                                                                                                |
  | -------------------------------------------------------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------- |
  | Driver runs on **client machine** where job is submitted                                                             | Driver runs on **one of the worker nodes** in the cluster                                                   |
  | **Driver is responsible** for coordinating execution                                                                 | **Cluster manager is responsible** for launching driver & allocate resources                                |
  | **Client machine interacts with cluster manager directly** to request resources and launch executors on worker nodes | **Driver program interacts with cluster manager** to request resources and launch executors on worker nodes |
  | **Not suitable for production**                                                                                      | **Suitable for production** as it allows better resource utilization, fault tolerance and scalability       |

- Execution Flow (Client Mode)
  1. **Job Submission**: User submits a job via spark-submit
  2. **Resource Allocation**: Driver requests resources from cluster manager
  3. **DAG Creation**: Driver creates a Directed Acyclic Graph (DAG) of stages and tasks based on the transformations and actions in the job. Tasks in same stage can be executed in parallel.
  4. **Task Execution**: Executors run tasks, result collected by the driver
- Executor Key Functions
  - Execute tasks
  - Resource allocation
- **Jobs**: A job is triggered by an action (e.g. `collect`, `count`) and consists of one or more stages.
- **Stages**: A stage is a set of tasks that can be executed in parallel, determined by shuffle boundaries (e.g. `join`, `groupBy`).
- **Tasks**: A task is the smallest unit of work, executed on a single partition of data. Tasks are scheduled and executed by executors based on the DAG created by the driver.
- **Partitioning**: Dividing data across multiple nodes, improves data locality and parallelism, reducing network I/O and improving performance.
  - **Static Partitioning**: Maximum resources are allocated to each application, can lead to resource contention and inefficient utilization
  - **Dynamic Partitioning**: Although each spark application gets fixed resources, inactive applications can release resources for active applications.
  - Significance
    - **Performance Optimization**: Parallelism through partitioning
    - **Adaptability & Flexibility**: Dynamic partitioning adapts to varying size
    - **Control & Predictability**: Static partitioning provides predictable resource allocation

## Chapter 4: NoSQL Databases

### 4.1 Databases

| RDBMS                            | NoSQL                                                                           |
| -------------------------------- | ------------------------------------------------------------------------------- |
| Structured                       | Unstructured/Semi-Structured                                                    |
| Rigid Schema                     | Flexible/Schema-less                                                            |
| Vertical Scaling                 | Horizontal Scaling                                                              |
| Strong Consistency (ACID)        | Eventual Consistency (BASE)                                                     |
| SQL                              | Various query languages                                                         |
| Financial, Transactional Systems | Real-time Analytics, Content Management Systems (CMS), Internet of Things (IoT) |

- **ACID**
  - **Atomicity**: All operations in a transaction must succeed or fail together
  - **Consistency**: All data integrity constraints must be maintained after a transaction
  - **Isolation**: A data item used in a transaction cannot be accessed by other transactions until the first transaction is completed
  - **Durability**: Once a transaction is committed, it will remain so, even in the event of system failure
- **BASE**
  - **Basically Available**: The system tolerates partial failures and remains available
  - **Soft state**: The state of the system may change over time, even without input, due to eventual consistency
  - **Eventual consistency**: The system will eventually become consistent, but not necessarily immediately after a transaction is committed

### 4.2 Key-Value Stores

- Key-value pairs
- No foreign keys, no relationships between data
- Redis, Amazon DynamoDB, Riak
- Use Cases: Word Maps (NLP), Session Management, Caching, Leaderboards, Real-Time Analytics
- Advantages:
  - Simple data model
  - Fast performance
  - Scalable
  - Flexible
- Disadvantages:
  - Limited querying capabilities
  - No consistency guarantees
  - Not suitable for complex data relationships

### 4.3 Document Stores

- Store data as documents (e.g. JSON, BSON)
  - JSON: JavaScript Object Notation, human-readable format for data interchange
  - BSON: Binary JSON, binary-encoded serialization of JSON-like documents, used by MongoDB for efficient storage and retrieval
- MongoDB, CouchDB, Amazon DocumentDB
- Use Cases: Content Management Systems (CMS), IoT Applications, Real-Time Analytics, User Profiles
- Advantages:
  - Flexible schema
  - Efficient querying
  - High performance read/write operations
  - Scalable
- Disadvantages:
  - Complex queries can be challenging to write
  - Harder to maintain data integrity and consistency

### 4.4 Graph Databases

- **Nodes**: Represent instances of entities (e.g. "Person", "Product"), can have multiple labels (e.g. "Person" and "Employee" for a node representing an employee who is also a person)
- **Edges**: Represent relationships between nodes (e.g. "FRIENDS_WITH", "PURCHASED")
- **Properties**: Both nodes and edges can have properties (e.g. "name", "age" for nodes; "since" for edges)
- **Traversal**: A query in a graph database often involves traversing the graph to find related nodes and edges
- Neo4j, Amazon Neptune
- Use Cases: Social Networks, Recommendation Systems, Fraud Detection, Knowledge Graphs
- Advantages:
  - Flexible schema
  - Efficient querying
  - Real-time analytics
  - Scalable
- Disadvantages:
  - Complex queries can be challenging to write
  - Harder to maintain data integrity and consistency
- Neo4j can support ACID transactions

### 4.5 Column-Family Stores

- Column-centric data model, data of same column stored in contiguous storage
- **Row**: Unique identifier for a record (e.g. "user123")
- **Column Family**: Group of related columns (e.g. "personal_info", "purchase_history")
- **Column**: Key-value pair within a column family (e.g. "name": "Alice")
- Apache HBase, Cassandra, Amazon Keyspaces
- Use Cases: Time-Series Data, Log Data, User Data, IoT Data
- Advantages:
  - Flexible schema
  - High performance
  - Cost-Effective
  - Scalable
- Disadvantages:
  - Complex data model
  - Limited querying capabilities

### 4.6 NoSQL Database Strategies

- Scaling Strategies:
  - **Scale-Up**: Vertical scaling by adding more resources to a single server (e.g. CPU, RAM), can lead to performance bottlenecks and single point of failure
  - **Scale-Out**: Horizontal scaling by adding more servers to the cluster, allows for better performance and fault tolerance, but requires more complex management and coordination
- Distribution Models:
  - **Replication**: Same data is copied across multiple nodes for fault tolerance and high availability, requires synchronization mechanisms to ensure consistency
    - **Master-Slave Replication**: Only one node (master) can accept write operations, and slave nodes replicate data from the master, support simultaneous read operations, but can lead to single point of failure and performance bottlenecks on the master node.
    - **Peer-to-Peer Replication**: All nodes can accept read and write operations, data is replicated across all nodes, provides better fault tolerance and load balancing, but requires more complex synchronization and conflict resolution mechanisms to ensure data consistency.
    - Advantages:
      - Fault Tolerance
      - Read Performance
      - Recovery
    - **Quorum** Mechanism
      - Minimum number of replicas must **acknowledge a write operation** before it is considered successful
      - Minimum number of replicas must be **available to respond to a read operation** before it is considered successful
      - Consistency & Fault Tolerance VS Availability trade-off
  - **Sharding**: Data rows are split across multiple nodes based on a shard key, allows for horizontal scaling and improved performance, but can lead to data skew (uneven distribution of data across nodes) and requires careful shard key selection
    - In Apache HBase, table is sharded into **regions**, managed by **region servers**. **HBase Master** assigns regions to region servers and monitors their health.
    - Depends on good row key design to ensure even distribution of data, avoid hotspots and improve performance.
    - Work together with HDFS redundancy to ensure region servers can recover data from other nodes in case of failure.
- Advantages of NoSQL Databases:
  - Flexible schema
  - High performance
  - Scalable
  - Cost-Effective
- Disadvantages of NoSQL Databases:
  - No standardisation
  - Eventual consistency is harder to manage

## Chapter 5: Data Streaming

### 5.1 Data Streaming

- **Data Streaming**: Continuous of data that can be processed as it arrives, important for application requires real-time immediate insights
- **Stream Processing**: Processing which continuously incorporates new data to compute results in real-time, data is unbounded (no predetermined end)
- **Batch Processing**: Bounded data processing, results only need to be computed once
- Use Cases: Notifications, Real-Time Analytics, Incremental ETL, Online Machine Learning, Fraud Detection
- Types of Streaming:
  
  | Types                                | Definition                                                                | Characteristics                                                            | Use Cases                                                          |
  | ------------------------------------ | ------------------------------------------------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------ |
  | **Real-Time Streaming**              | Process data with minimal delay (ms to seconds)                           | Low latency, high frequency & time-sensitive applications                  | Stock Trading, Fraud Detection, Emergency Response                 |
  | **Near Real-Time Streaming**         | Process data with acceptable delay (seconds to minutes)                   | Moderate latency, less time-sensitive applications                         | User Behavior Analysis for recommendation updates, Log Analysis    |
  | **Event Streaming**                  | Continuous flow of events, record state changes, actions or occurrences   | Event-driven, unbounded data                                               | Sensor events, user interactions, news feeds, social media updates |
  | **Batch Streaming (Micro-Batching)** | Process data in small batches at regular intervals (e.g. every 5 seconds) | Higher latency, suitable for applications not requiring immediate insights | ETL pipeline, intervallic analytics, data aggregation              |

### 5.2 Apache Kafka

- Distributed publish-subscribe messaging system designed for high-throughput, fault-tolerant, real-time data streaming
- **Producer**: Application that publishes messages to Kafka topics
- **Consumer**: Application that subscribes to Kafka topics and processes messages
- **Topic**: Logical channel to which producers publish messages and consumers subscribe
- **Broker**: Kafka server that stores messages and serves clients
- **Record**: A message in Kafka, consists of a key, value and timestamp
- **Offsets**: Position of a record within a topic partition, used by consumers to track their progress
- **Partitions**: Kafka topics are divided into partitions for scalability and parallelism, each partition is an ordered, immutable sequence of records
- Use Cases: Real-Time Monitoring, Event-Driven Applications

### 5.3 Structured Streaming

- Uses Spark SQL engine to process unbounded data streams as if they were static tables, allows for real-time stream processing with the same API as batch processing
- **Data Sources**: Kafka, file systems, socket streams, etc.
- **Transformations**: Similar to batch processing (e.g. `map`, `filter`, `groupBy`), but applied to streaming data
- **Sinks**: Output of streaming computations, can be written to file systems, databases, Kafka, etc.
- **Triggers**: Define when the streaming query should be executed (e.g. continuously, at a fixed interval, or once)
- **Watermarking**: Handle late data by defining a threshold for how long to wait for late data before considering it as late and dropping it from the results
- Use Cases: ETL pipelines, streaming analytics, integration with batch processing

## Chapter 6: MapReduce

### 6.1 MapReduce Overview

- Advantages
  - **Abstraction**: Abstract away the complexities of distributed computing
  - **Standardisation**: Consistent design pattern to build processing pipelines
  - **Reusability**: Library of pre-built functions for common data processing tasks
  - **Flexibility**: Allow custom logic to be applied to data processing tasks
- **Mapper**: Process input pairs into intermediate key-value pairs
- **Reducer**: Process intermediate key-value pairs and merge values with same key to produce final output using reducer function
- Workflow:
  - **Split**: Split input data into smaller chunks for parallel processing
  - **Map**: Mapper processes its own chunk of data and produces intermediate key-value pairs
  - **Combine**: *Optional* step to perform local reduction on mapper output to reduce data transfer during shuffle phase
  - **Partition**: Intermediate key-value pairs sharded, ensuring that all values with the same key will end up on the same reducer, also ensures load balancing across reducers, written to local disk of mapper nodes awaiting reducer nodes to pull them.
    - Partition Function determines the partition ID for each intermediate key-value pair, important for load balancing
    > [!NOTE]
    > Often combined with the shuffle phase when answering questions
    - **Shuffle**: Output of mappers is pulled by machines running reducers, network I/O intensive
  - **Sort**: Intermediate key-value pairs sorted by key for efficient merging (When keys are sorted, reducer can easily merge values with the same key by iterating through the sorted list)
  - **Reduce**: Reducer merges values with the same key using the reducer function to produce final output

### 6.2 MapReduce Jobs

- **Map Task**: Record Reader -> Mapper - > Combiner (optional) -> Partitioner
- **Reduce Task**: Shuffle -> Sort -> Reducer -> Record Writer

### 6.3 Basic Types of MapReduce Jobs

| Job Type                                | Description                                                            | Use Cases                                                                                                                                   |
| --------------------------------------- | ---------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------- |
| **Single Mapper Jobs**                  | Input -> Split -> Map -> Output                                        | Row-level transformations, filtering, data cleansing                                                                                        |
| **Single Mapper Reducer Jobs**          | Input -> Split -> Map -> Shuffle & Sort -> Reduce -> Output            | Aggregations, summarization, counting, grouping                                                                                             |
| **Multiple Mapper Reducer Jobs**        | Mutiple Input -> Multiple Map -> Shuffle & Sort -> Reduce -> Output    | Joining datasets                                                                                                                            |
| **Single Mapper Combiner Reducer Jobs** | Input -> Split -> Map -> Combine -> Shuffle & Sort -> Reduce -> Output | Optimises performance by reducing data transfer during shuffle phase, suitable for associative and commutative operations (e.g. sum, count) |

### 6.4 MapReduce Patterns

- **Aggregation**: Grouping data by a key and performing an aggregation function (e.g. statistics, counting, indexing)
- **Filtering**: Removing records that do not meet certain criteria (e.g. data cleansing, top-k, distinct, subset selection)
- **Joining**: Combining two datasets based on a common key
  - **Inner Join**: Get records that have matching keys in both datasets
  - **Left Anti Join**: Get records from the left dataset that *do not* have matching keys in the right dataset
  - **Left Outer Join**: Get all records from the left dataset and matching records from the right dataset
  - **Right Outer Join**: Get all records from the right dataset and matching records from the left dataset
  - **Full Outer Join**: Get all records from both datasets
  - **Left Semi Join**: Get records from the left dataset that have matching keys in the right dataset (Act as filter, only return columns from the left dataset)
  - **Cross Join**: Get the Cartesian product of both datasets (Combine every record from the left dataset with every record from the right dataset)
    - $\{a, b\} \times \{1, 2\} = \{(a, 1), (a, 2), (b, 1), (b, 2)\}$

## Chapter 7: Data Privacy and Security

### 7.1 Data Privacy

- **Data Anonymization**: Process of removing or masking personally identifiable information (PII) from datasets

| Technique                     | Description                                                                                                                                                                          |
| ----------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Data Masking**              | Replace direct identifiers (e.g. name, email) with fictitious values, symbols or placeholders                                                                                        |
| **Pseudonymization**          | Replace direct identifiers with pseudonyms, allowing for de-anonymization if necessary (e.g. replacing name with a unique ID)                                                        |
| **Generalization**            | Replace specific values with more general ones (e.g. replacing age with age range)                                                                                                   |
| **Suppression**               | Remove entire records or specific attributes that contain sensitive information (e.g. removing records with rare diseases)                                                           |
| **Synthetic Data Generation** | Create artificial datasets that mimic the statistical properties of the original data without containing real PII (e.g. using generative models to create synthetic patient records) |

### 7.2 Security Design Principles

- **Principle**: High level design goal
- **Rule**: Specific guideline to implement a principle
- Categories of Principles:
  - **Prevention**: Eliminate defects before they occur
  - **Mitigation**: Reduce the impact of exploits or unexpected defects
  - **Detection and Recovery**: Identify attacks and undo damage
- Security Design Principles:
  - **Least Privilege**: Individuals/services should be given minimum privileges for minimum duration necessary to perform their tasks, reduces attack surface and limits damage from compromised accounts
  - **Defense in Depth**: Multiple layers of defense to protect against different types of attacks, if one layer is breached, others still provide protection (e.g. firewalls, intrusion detection systems, encryption)
  - **Complete Mediation**: Every request must undergo valid and effective authorization procedures

### 7.3 Primary Security Domains

- **Authentication**: Mechanism to verify if the users/services are who they claim to be
  - Components of **Kerberos Authentication Protocol**:
    - **Principal**: Unique identity for users/services in Kerberos
    - **Realm**: Administrative domain in Kerberos, used to group principals and manage authentication policies
    - **UPN (User Principal Name)**: Unique identifier for a user in Kerberos, typically in the format `user@REALM`
    - **SPN (Service Principal Name)**: Unique identifier for a service in Kerberos, typically in the format `service/hostname@REALM`
    - **KDC (Key Distribution Center)**: Central authority that issues tickets for authentication in Kerberos, responsible for verifying identities and granting access to resources
    - **Kerberos Database**: Stores all principal information and realms
    - **AS (Authentication Server)**: Component in Kerberos that authenticates users and issues tickets
    - **TGT (Ticket Granting Ticket)**: A ticket issued by the AS after successful authentication, used to request service tickets from the TGS without re-authenticating
    - **TGS (Ticket Granting Server)**: Component in Kerberos that issues service tickets based on the initial ticket obtained from the AS, allows users to access specific services without re-authenticating
    - **ST (Service Ticket)**: A ticket issued by the TGS that allows a user to access a specific service, contains information about the user and the service being accessed
  - Workflow of Kerberos Authentication:
    1. **AS_REQ**: User `student` sends an authentication request to the AS at `kdc.example.com`, identifying themselves as `student@EXAMPLE.COM`
    2. **AS_REP**: AS issues a TGT encrypted with the password of `student@EXAMPLE.COM`
    3. **Password Verification**: `student@EXAMPLE.COM` prompted to enter password, if correct, TGT is decrypted.
    4. **TGS_REQ**: `student@EXAMPLE.COM` request an ST from TGS for a specific service (`hdfs/localhost@EXAMPLE.COM`) using the TGT
    5. **TGS_REP**: TGS issues `student@EXAMPLE.COM` an ST encrypted with the key of the SPN `hdfs/localhost@EXAMPLE.COM`
    6. **AP_REQ**: `student@EXAMPLE.COM` presents the ST to the service `HDFS`
    7. **AP_REP**: `HDFS` decrypts the ST using its key, verifies the ticket and grants access to `student@EXAMPLE.COM` to use the service
- **Authorization**: Mechanism to determine if an authenticated user/service has permission to access a resource or perform an action
  - ACL (Access Control List): Set of rules define permissions for users/services to access resources
  - POSIX Permissions: File system permissions based on user, group and others (e.g. read, write, execute)
  - Role-Based Access Control (RBAC): Group users into roles and assign permissions to roles, users inherit permissions from their roles
- **Auditing**: Recording events and transactions in Hadoop cluster for security monitoring, compliance and forensic analysis
- **Data Protection**: Ensure confidentiality, integrity and availability of data both in-transit and at-rest, encryption is a common method
  - Transparent Data Encryption (TDE) for data at rest
  - SSL/TLS for data in transit

### 7.4 Best Practices for Data Security in Hadoop

- **Regular Update**: Fix latest discovered vulnerabilities
- **Secure Configuration**: Disable unused services, configure firewalls, enforce encryption
- **Authentication and Authorization**: Implement Kerberos, manage permissions carefully using ACLs, POSIX permissions or RBAC, use Apache Ranger for fine-grained access control
- **Data Encryption**: Protect sensitive data using encryption both at rest and in transit, integrating enterprise key management systems (e.g. AWS KMS, HashiCorp Vault) for secure key management
- **Comprehensive Auditing**: Enable detailed logging, analyse access patterns to identify anomaly
- **Practicing Least Privilege**: Regularly review and update permissions
- **Continuous Security Monitoring & Incident Response**: Robust monitoring system to detect and respond to security incidents, predefined incident response plan to mitigate damage and recover quickly
- **Employee Training and Awareness**: Human error is a common cause, regular training on security best practices and awareness of potential threats can significantly reduce risk of breaches.

#### Passwords

- Complex password may be difficult to hack, but also hard to remember
- Complex password can be easy to hack too, because users may write them down or reuse them across multiple accounts, increasing the risk of compromise if one account is breached
- Usable passwords ideas: use passphrases that is easily remembered but still complex (e.g. "correct horse battery staple")
