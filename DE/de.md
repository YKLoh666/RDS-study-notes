# Data Engineering

## Chapter 1: Introduction to Data Engineering

### 1.1 Data Engineering Overview

#### Roles of Data Engineering in Organizations

- **Data Preparation and Integration**: Process large amount of data from various sources into useful formats.
- **Foundation for Analytics and AI**: Provide scalable data infrastructure.
- **Data-Driven Insights**: Predictive decision-making

#### Concepts

- **Data Modelling**: Structure relationships of data for efficient storage and retrieval.
- **Data Integration**: Different types of data from various sources into a standard format.
- **Data Transformation**: Cleaning, Enrichment, Aggregation and Normalization.
- **Data Pipeline**: Ingestion, Transformation, Loading; Data flow from source to destination, i.e. batch or real time streaming.
- **Data Governance**: Manage and control data assets, including usage, access and security compliance.
- **Data Preparation**: Refine dataset through aggregation for analysis
- **Data Quality Assurance**: Validate data for accuracy, consistency and reliability.
- **Data Accessibility**: Prepare raw/curated data stores (i.e. data platforms, data lakes, warehouses)
  - Data Platform: Integrated environment for data storage, processing and analysis
  - Data Lake: Raw data
  - Data Warehouse: Structured data for analysis and reporting

#### Lifecycle

- **Data Ingestion**: Collecting data from various sources.
- **Data Storage**: Storing data in data stores (i.e. data lakes, warehouses).
- **Data Processing**: Transforming and preparing data for analysis.
- **Data Integration**: Combining data from different sources into a unified view.
- **Data Quality Assurance**: Ensuring data is accurate, consistent and reliable.

#### ETL vs ELT

| Feature             | ETL (Extract, Transform, Load)           | ELT (Extract, Load, Transform)                          |
| ------------------- | ---------------------------------------- | ------------------------------------------------------- |
| Data Transformation | Before loading                           | After loading                                           |
| Flexibility         | Less flexible                            | More flexible                                           |
| Scalability         | Less scalable                            | More scalable                                           |
| Complexity          | More complex                             | Less complex                                            |
| Use Cases           | Smaller datasets, highly structured data | Larger volume of unstructured data, real-time streaming |

#### Technologies

- **Ingestion**: Apache Kafka
- **Storage**: Hive, PostgreSQL, MongoDB, Neo4j
- **Processing**: Apache Spark
- **ETL/ELT**: Apache Airflow

#### Challenges

- **Data Quality**: Inconsistency, missing values
- **Scalability**
- **Performance**
- **Security and Privacy**: Data breaches, PDPA compliance

### 1.2 Data Engineering in Organizations

- Data engineering provides competitive advantage by
  - adapting to market changes,
  - identifying emerging trends,
  - data-driven decision making

#### Data Engineering in Analytics and ML

- **Data Wrangling**: Data cleaning, integration, transformation for analysis and ML.
- **Data Preparation**: Optimizing data for ML models, including feature engineering and selection.
- **Data Pipeline Development**: Enable seamless flow of large amounts of data that is scalable, fault-tolerant and robust, ensuring timely delivery of accurate data for analytics and ML.
- **Scalability and Performance**: Optimizing performance and scalability to process massive datasets efficiently.
- **Data Governance**: Establishing data governance practices, implement access controls, encryption and anonymization techniques to protect sensitive data and ensure compliance with regulations.

#### Data Engineering for Decision-Making

- **Data Integration**: Combine data from various sources for comprehensive insights.
- **Data Transformation & Aggregation**: Consolidated view of complex data to derive insights.
- **Data Quality Assurance**: Ensure data is accurate, consistent and reliable to instill confidence in decision-making.
- **Data Accessibility**: Provide timely access to data for informed decision-making.
- **Scalability and Performance**: Ensure timely delivery of data even as data volume grows.
- **Data Governance & Compliance**: Ensure data is used responsibly and in compliance with regulations, fostering trust in data-driven decisions.

#### Impacts of Data-Driven Products and Services

| Industry           | Personalization                      | Predictive Analytics            | Real-Time Insights                 |
| ------------------ | ------------------------------------ | ------------------------------- | ---------------------------------- |
| **Healthcare**     | Personalized treatment plans         | Early disease detection         | Real-time patient monitoring       |
| **Finance**        | Personalized financial advice        | Fraud detection                 | Real-time market analysis          |
| **Retail**         | Personalized product recommendations | Demand forecasting              | Real-time inventory management     |
| **Transportation** | Personalized route optimization      | Predictive maintenance          | Real-time traffic monitoring       |
| **Education**      | Personalized learning paths          | Student performance prediction  | Real-time feedback and support     |
| **Environment**    | Personalized energy management       | Climate change prediction       | Real-time environmental monitoring |
| **Public Safety**  | Crime prediction and prevention      | Emergency response optimization | Real-time crime monitoring         |

#### Roles of Human in Dataset Creation

- **Data Annotation**: Tagging images, annotating text, transcribing audio or timestamps for video.
  - **Gold Standard Datasets**: High-quality datasets labeled by domain experts through rigorous validation processes.
- **Data Cleaning**: Resolve inconsistencies, handle missing values or outliers manually.
- **Dataset Design and Validation**: Determine distribution of classes, ensure skewness is addressed, validate against benchmarks or real-world scenarios.
- **Quality Assurance**: Resolve disagreements or ambiguities among annotators, spot check labels for accuracy and consistency.
- **Bias Mitigation**: Ensure diversity in data sampling, review labels for stereotypes or biases.
- **Evaluation and Benchmarking**: Manually review model predictions, conduct user studies or experiments to assess real-world performance.

### 1.3 Ethics

| Category | Explanation                                                               |
| -------- | ------------------------------------------------------------------------- |
| Law      | Legally required standards of behavior                                    |
| Morals   | Beliefs shaped by culture, religion, upbringing                           |
| Ethics   | Reasoned judgments about right and wrong, often based on moral principles |

#### Importance of Ethics

- Building Trust and Credibility
- Guides Behavior under Pressure

#### Core Ethical Values

- Integrity
- Honesty
- Responsibility
- Respect
- Fairness
- Empathy

### 1.4 Professionalism

- Responsible and Ethical Behavior
- Respectfuul Interactions
- Reliability and Accountability
- Adherence to Standards and Expectations

#### Importance of Professionalism

- Builds Trust and Credibility
- Enhances Teamwork and Collaboration
- Protects personal and organizational reputation
- Supports Career Growth

#### Elements of Professionalism

- Punctuality and Time Management
- Responsibility
- Respect
- Appropriate Communication
  - Clear and concise language
  - Respectful tone
  - Awareness of audience and context
  - Timely Responses
  - Email Etiquette, Meeting Etiquette etc.
- Ethical Decision-Making

## Chapter 2: Hadoop Ecosystem

### 2.1 Motivation

- To cope with 4V
  - **Volume**: Distributed data storage with parallel reading and writing
  - **Variety**: Flexibility to work with any data format
  - **Velocity**: Event processing and real-time streaming
  - **Veracity**: Replication and fault tolerance
- As well as
  - **Cost-Effectiveness**: Commodity hardware and open-source software
  - **Scalability**: Handles increasing workloads by adding more nodes
  - **Availability**: High availability through replication and fault tolerance
  - **Reliability**: Data integrity and fault tolerance through replication and checksums

### 2.3 HDFS

- Distributed file system designed to run on commodity hardware
- Break down large files into blocks and distribute across multiple nodes to optimise storage and processing
- Virtual layer that abstracts away physical storage details, providing a unified view of the data

#### HDFS File Blocks

- In 128MB or 256MB blocks
- Replicated usually 3 times across different nodes for redundancy and fault tolerance.
  - Allow node failures without data loss

#### Write Operation

1. Data write to NameNode
2. NameNode splits data into blocks and assigns DataNodes for storage
3. DataNodes store the assigned blocks
4. DataNodes replicate blocks to other DataNodes for redundancy

#### Read Operation

1. Client requests from NameNode
2. NameNode locates DataNodes storing the requested blocks
3. DataNodes transfer blocks **directly** to client

#### Advantages

- **Scalability**: Horizontal scaling by adding more nodes
- **Reliability**: Data replication, self-healing capabilities (such as re-replication of lost blocks)
- **Cost-Effectiveness**: Runs on commodity hardware, open-source software
- **Efficiency**: Data locality principle (processing data where it resides), reducing network congestion; Optimised for large data transfers and parallel processing

#### HDFS CLI Commands

- `cat <file>`: Display contents of a file
- `chmod <flag> <mode> <file>`: Change permissions of a file or directory (`-R` for recursive)
- `chown <flag> <owner>:<group> <file>`: Change ownership of a file or directory to a user or group (`-R` for recursive)
- `count <flag> <path>`: Count the number of directories, files and bytes under the given path (`-q` for quota, `-h` for human-readable format)
- `put <local_file> <hdfs_file>`: Upload a local file to HDFS
- `get <hdfs_file> <local_file>`: Download a file from HDFS to local filesystem
- `cp <flag> <source> <destination>`: Copy files within HDFS
- `df <flag>`: Display HDFS disk usage (`-h` for human-readable format)
- `mkdir <flag> <directory>`: Create a new directory in HDFS
- `mv <flag> <source> <destination>`: Move or rename files within HDFS
- `rm <flag> <file>`: Remove files or directories from HDFS (`-R` for recursive)

## Chapter 3: Apache Spark

### 3.1 Introduction to Apache Spark

- Distributed computing framework for big data processing and analytics (Use multiple computers to process large datasets in parallel)
- Core Features:
  - **In-Memory Computing**: Store intermediate data in memory for faster processing
  - **Lazy Evaluation**: Delay execution until necessary, optimizing the execution plan
  - **Resilient Distributed Datasets (RDDs)**: Fault tolerant collections of objects that can be processed in parallel
  - **Multiple Language Support**: APIs for Java, Scala, Python and R
- 