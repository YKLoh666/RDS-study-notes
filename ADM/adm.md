# Advanced Database Management

## Chapter 1: Information Models

### Data, Information, Knowledge

| Concept     | Description                                                                                 |
| ----------- | ------------------------------------------------------------------------------------------- |
| Data        | Raw, non-summarized, and unanalyzed facts and figures.                                      |
| Information | Data converted into meaningful and useful context. (Provide 'Who', 'What', 'Where', 'When') |
| Knowledge   | Gained from information to make decisions. (Provide 'How')                                  |

### Categorization of Information

> [!NOTE]
> Example below are in the context of a university.

- Source
  - **Primary**: Raw interview transcripts
  - **Secondary**: Journal articles
  - **Internal**: Official annual financial report
  - **External**: Online news articles on university rankings
- Nature
  - **Qualitative**: Written feedback from lecturer evaluation forms
  - **Quantitative**: Number of enrolled students in a course
- Level
  - **Strategic**: National employment trends in artificial intelligence field for planning new programs
  - **Tactical**: Number of qualified staff available for a new course
  - **Operational**: List of textbooks required for the planned subject of new course
- Time
  - **Historical**: 10 years student enrollment data
  - **Present**: Running class schedule of today
  - **Future**: Projected student enrollment for the next academic year

### Information Capturing and Representation

- OCR, Barcode
- RFID
- Document Scanning
- World Wide Web (Twitter, Blogs, Web Pages, etc.)

### Types of Queries

- **Procedural Queries** (cumbersome, requires technical knowledge)
- **Declarative Queries** (only state what is needed but not how to get it, easier to use)
- **Navigational Queries** (if searcher know path to the information, such as using website or file system)

### Information Security

- **Confidentiality** (Authentication in Database)
- **Integrity** (CONSTRAINTS in Database)
- **Availability** (Reliability and Timeliness of Database)

### Threats to Information Security

- **Accidental Loss** (e.g., Human, Software, Hardware Errors)
- **Theft and Fraud** (e.g., Hacking, Phishing, Identity Theft)
- **Loss of privacy or confidentiality** (privacy for personal data, confidentiality for corporate data)
- **Loss of data integrity** (e.g., Data corruption, Data tampering, Data loss)
- **Loss of availability** (e.g., Denial of Service, Natural Disasters, Power Outages)

### Countermeasures to Threats

- **Backup and Recovery**
- **Physical Security** (e.g., CCTV, Security Guards, Access Control)
- **Technical Security** (Software and Hardware Security, Firewalls, Intrusion Detection Systems, Audit Trails)

## Chapter 2: Database Systems

### Disadvantages of File Processing System

- **Program-Data Dependence**
  - Each application program maintain its own data file with different formats and structures, lack coordination between programs
- **Data Redundancy**
  - Duplicate data stored by different departments (Eg. Customer data stored in both accounting and marketing departments)
- **Limited Data Sharing**
  - Hard to share data between different applications due to different formats and structures
- **Lengthy Development Times**
  - New applications require new data files and programs, which takes time to develop
- **Excessive Program Maintenance**
  - Changes in data file structure require changes in all application programs that access the data file

### Functions of RDBMS

- **Store, Update and Retrieve Data**
- **Concurrency Control Services**
  - Locking mechanisms
  - Timestamping
  - Versioning
- **Backup and Recovery Services**
- **Security**
  - Encryption
  - Authentication
  - Authorization
  - Views
- **Integrity Services**
  - NOT NULL
  - UNIQUE
  - PRIMARY KEY
  - FOREIGN KEY
  - CHECK
- **Transaction Support**
  - Ensures sequential execution success, or rollback to initial state in case of failure

> [!NOTE]
> ACID Properties of Transaction: Atomicity, Consistency, Isolation, Durability

- **User-Accessible System Catalog**
  - Metadata about data in the database
    - Names, types, sizes, and constraints of data items
    - Name of authorized users and their privileges
    - Usage statistics of data items
  - Consulted by DBMS when performing operations on the database (check access rights, check constraints, etc.)

### Components of RDBMS

- **Query Processor**: Transform queries into low-level instructions directed to the database manager
- **Database Manager**: Responsible for managing the database and its operations
- **File Manager**: Responsible for the physical storage of data on disk
- **DML Preprocessor**: Translates DML statements into standard functions calls in the host programming language
- **DDL Compiler**: Converted into set of tables containing metadata, stored in the system catalog
- **Catalog Manager**: Manage access and maintenance of the system catalog
- **Authorization Control**
- **Command Processor**
- **Integrity Checker**
- **Query Optimizer**: Determines the most efficient way to execute a given query by considering possible query plans
- **Transaction Manager**: Ensure ACID properties of transactions
- **Scheduler**: Manage concurrency control
- **Recovery Manager**
- **Buffer Manager**: Manage transfer of data between main memory and secondary storage (disk)

### ANSI-SPARC Architecture

- Abstract Design Standard for Database Systems
- Levels
  
  | Level          | Description                                                                                                                 |
  | -------------- | --------------------------------------------------------------------------------------------------------------------------- |
  | **External**   | User view of the database, each user can have a different view of the database                                              |
  | **Conceptual** | Community view of the database, describe entities, attributes, relationships and integrity constraints                      |
  | **Internal**   | Physical representation of the database on the computer, describe definition of stored data, indexes and storage structures |

> [!NOTE]
> For example, a table of student information can be represented in different ways at each level:
>
> - **External Level**: View on the table, [Student Name, Student ID, Course Enrolled]
> - **Conceptual Level**: Full table with all attributes, [Student Name, Student ID, Course Enrolled, Date of Birth, Address, Phone Number]
> - **Internal Level**: Physical storage of the table in a database file, with indexes on Student ID and Phone Number for faster access
>
>   ```cpp
>   struct Student {
>       char name[50];
>       int id;
>       char course[50];
>       char dob[10];
>       char address[100];
>       char phone[15];
>   };
>   index id; index phone;
>   ```

- **Logical Data Independence**: Between external and conceptual levels, changes in the conceptual level do not affect the external level (e.g., adding a new attribute to the table does not affect the user view)
- **Physical Data Independence**: Between conceptual and internal levels, changes in the internal level do not affect the conceptual level (e.g., changing the storage structure of the table does not affect the logical representation of the data)

### Multi-User DBMS Architecture

- **Teleprocessing**
  - Traditional single-tier architecture
  - User connects to the central computer via a terminal
  - Multiple terminals can connect to the central computer at the same time
  - User terminals are "dumb" terminals, all processing is done on the central computer
- **File-Server**
  - File-server connected to several workstations in a network
  - Database in file-server
  - DBMS and application programs run on workstations
  - Significant network traffic
  - Copy of DBMS on each workstation
  - Much complex concurrency, recovery and integrity control
- **Client-Server**
  - 2-Tier
    - Architecture
      - Client: User interface and application logic
      - Server: Database and DBMS
    - Disadvantages
      - Significant client side administration overhead
  - 3-Tier
    - Architecture
      - Client: User interface
      - Application Server: Application logic
      - Database Server: Database and DBMS
    - Advantages
      - Thin client
      - Application maintenance centralized
      - Decouple eases modification and replacement of the tiers
      - Easier to scale with load balancing
  - N-Tier
    - Architecture
      - Client: User interface
      - Application Server: Application logic
      - Database Server: Database and DBMS
      - Additional tiers for other services (e.g., web server, caching, messaging, etc.)
    - Advantages
      - Further decoupling of services
      - Flexible and scalable

### Transaction Processing Monitor (TP Monitor)

- Program that controls data transfer between client and server
- Sits between the client and servers' services, handles the service calls from the client and forwards them to the appropriate server
- Functions
  - **Transaction Routing**: Directs the transaction to specific DBMS
  - **Managing distributed transactions**: Manage transactions that span multiple databases, ensuring ACID properties are maintained across all involved databases
  - **Load Balancing**: Balances the load across multiple servers to optimize resource utilization and response time
  - **Increase Reliability**: Resubmits failed transactions to other DBMS to ensure they are completed successfully or hold until the DBMS is available again
  - **Funneling**: Clients don't own the database connection, but the TP monitor does, so 10,000 clients won't open 10,000 connections to the database. TP monitor holds the requests, looks at the limited number of connections to the database, and sends the requests to the idle connections.

### Distributed Database Management System (DDBMS)

- Logically interrelated databases physically distributed over computer network.
- A given site may have a complete or partial copy of the database.

## Chapter 3: Data Modeling

- ERD
- Need explain relationship
  - E.g. One student must enroll in at least one course, and a course can have zero or many students enrolled.

## Chapter 4: Relation Model

### Relational Algebra Symbols

- **Projection $\pi_{col1, col2, ...}$**: Equivalent to `SELECT col1, col2, ...` in SQL
- **Selection $\sigma_{predicate}$**: Equivalent to `WHERE predicate` in SQL
- **Rename $\rho_R (\text{new\\_name})$**: Equivalent to `AS new_name` in SQL, commonly used for aggregated columns
<!-- markdownlint-disable MD033 -->
- **Aggregation** $_\text{grp\\_col1, grp\\_col2, ...}J\_\text{agg1 col1, agg2 col2}$: Equivalent to `SELECT agg1(col1), agg2(col2) ... GROUP BY grp_col1, grp_col2, ...` in SQL

> [!IMPORTANT]
> There is no parenthesis () in the aggregation operator like in SQL.
>
> Write J as in <img src="agg_symbol.png" width="14px" alt="agg_symbol"/>

- **Joins**
  - **Natural Join $\bowtie$**: Equivalent to `JOIN` in SQL
  - **Left Outer Join $\rtimes$**: Equivalent to `LEFT JOIN` in SQL, include all rows from the left table
  - **Right Outer Join $\ltimes$**: Equivalent to `RIGHT JOIN` in SQL, include all rows from the right table
  - **Left Semi Join $\triangleright$**: Equivalent to `LEFT SEMI JOIN` in SQL, like natural join but only return columns from the left table
  - **Right Semi Join $\triangleleft$**: Equivalent to `RIGHT SEMI JOIN` in SQL, like natural join but only return columns from the right table
  - **Division $\div$**: Equivalent to `DIVIDE` in SQL, used to find tuples in one relation that are related to all tuples in another relation
  - **Cartesian Product $\times$**: Equivalent to `CROSS JOIN` in SQL, returns all possible combinations of tuples from two relations

> [!NOTE]
> Example of Division:
>
> **Table R**
>
> | Student | Course    |
> | ------- | --------- |
> | Alice   | Math      |
> | Alice   | Physics   |
> | Bob     | Math      |
> | Bob     | Chemistry |
> | Charlie | Math      |
> | Charlie | Physics   |
>
> **Table S**
>
> | Course  |
> | ------- |
> | Math    |
> | Physics |
>
> **Result of R $\div$ S**
>
> | Student |
> | ------- |
> | Alice   |
> | Charlie |
>
> Only Alice and Charlie are enrolled in all courses in S (Math and Physics).

- **Set Operations**
  - **Union $\cup$**: Equivalent to `UNION` in SQL
  - **Intersection $\cap$**: Equivalent to `INTERSECT` in SQL
  - **Difference $-$**: Equivalent to `MINUS/EXCEPT` in SQL
- **Predicates**
  - **And $\wedge$**: Equivalent to `AND` in SQL
  - **Or $\vee$**: Equivalent to `OR` in SQL
  - **Not $\neg$**: Equivalent to `NOT` in SQL
  - **Equal $=$**: Equivalent to `=` in SQL
  - **Not Equal $\neq$**: Equivalent to `<>` in SQL
  - **Inequalities $<$, $>$, $\leq$, $\geq$**: Equivalent to `<`, `>`, `<=`, `>=` in SQL
  - **Like '%pattern%'**: Equivalent to `LIKE '%pattern%'` in SQL, used for pattern matching

### Relational Algebra Examples

(1) List all students

```sql
SELECT * FROM Students;
```

$Students$

(2) List name and age of students

```sql
SELECT Name, Age FROM Students;
```

$\pi_\text{Name, Age}(Students)$

(3) List name and age of students who are older than 20

```sql
SELECT Name, Age FROM Students WHERE Age > 20;
```

$\pi_\text{Name, Age}(\sigma_\text{Age > 20}(Students))$

(4) List name and age of male students who are older than 20

```sql
SELECT Name, Age FROM Students WHERE Age > 20 AND Gender = 'M';
```

$\pi_{Name, Age}(\sigma_{\text{Age > 20} \wedge \text{Gender = 'M'}}(Students))$

(5) List name of students who enrolled in both Math and Physics courses

```sql
SELECT Students.name
FROM Students
JOIN Enrollments ON Students.id = Enrollments.student_id
JOIN Courses ON Enrollments.course_id = Courses.id
WHERE Courses.name = 'Math' OR Courses.name = 'Physics';
```

$\pi_\text{name}(\text{Students}) \bowtie\_\text{Students.id = Enrollments.student\\_id} (\text{Enrollments}) \bowtie\_\text{Enrollments.course\\_id = Courses.id} (\sigma\_{\text{name = 'Math'} \vee \text{name = 'Physics'}}(\text{Courses}))$

(6) List total number of students enrolled in each course of KL branch

```sql
SELECT Courses.id, COUNT(Enrollments.student_id) AS total_students
FROM Courses
JOIN Enrollments ON Courses.id = Enrollments.course_id
WHERE Courses.branch = 'KL'
GROUP BY Courses.id;
```

<!-- markdownlint-disable MD033 -->
$\rho_{R(\text{Course\\_ID, TotalStudents})}\bowtie\_{\text{Course.id = COUNT(Enrollments.student\\_id)}}$
$(\pi\_{\text{Courses.id, Enrollments.student\\_id}}(\sigma\_{\text{branch = 'KL'}}(\text{Courses})$
$\bowtie\_\text{Courses.id = Enrollments.course\\_id}(\text{Enrollments})))$

## Chapter 5: Relational Database Design

### Update Anomalies

Example 1NF table of order information:

| OrderID | OrderDate  | CustomerID | CustomerName | CustomerAddress | ProductID | ProductName | ProductPrice | Quantity |
| ------- | ---------- | ---------- | ------------ | --------------- | --------- | ----------- | ------------ | -------- |
| 1       | 2023-01-01 | 1001       | John Doe     | 123 Main St     | 101       | Widget A    | 5.00         | 10       |
| 1       | 2023-01-01 | 1001       | John Doe     | 123 Main St     | 102       | Widget B    | 10.00        | 5        |
| 2       | 2023-01-02 | 1002       | Jane Smith   | 456 Oak Ave     | 101       | Widget A    | 5.00         | 20       |
| 2       | 2023-01-02 | 1002       | Jane Smith   | 456 Oak Ave     | 103       | Widget C    | 7.50         | 15       |

- **Insertion Anomaly**: Inability to add new records without adding redundant data

> It is not possible to add the new product unless that new product is ordered by a customer
> 
- **Modification Anomaly**: Inability to accurately maintain data due to redundancy. A change in one record may require changes to multiple records

> Modifying the name of ProductID 101 from "Widget A" to "Widget A+" in the first row must also be done to the similar product in other rows, otherwise the data will be inconsistent

- **Deletion Anomaly**: Inability to delete records without losing data that is needed to retain.

> All information about Widget B will be lost if the order with OrderID 1 is deleted

### Functional Dependencies

- **Functional Dependency**: A relationship that exists when one attribute uniquely determines another attribute. For example, in a table of students, the StudentID uniquely determines the StudentName.
- **Full Functional Dependency**: A functional dependency where an attribute is functionally dependent on a set of attributes, but not on any proper subset of that set. For example, in a order table, the combination of OrderID and ProductID uniquely determines the Quantity, but neither OrderID nor ProductID alone can determine Quantity.
- **Partial Functional Dependency**: A functional dependency where an attribute is functionally dependent on a part of a composite primary key. For example, in a table with a composite primary key of (OrderID, ProductID), if CustomerName is dependent only on OrderID, then CustomerName has a partial functional dependency on the primary key.
- **Transitive Dependency**: A functional dependency where one attribute is dependent on another attribute, which is in turn dependent on a third attribute. For example, if A → B and B → C, then A → C is a transitive dependency.

### Normal Forms

- **First Normal Form (1NF)**: A relation is in 1NF if it contains only atomic values, and has no repeating groups.

> The non-repeating part of the table is the OrderID, OrderDate, CustomerID, CustomerName, and CustomerAddress.
>
> ORDERLINE(<u>OrderID*</u>, <u>ProductID</u>, ProductName, ProductPrice, Quantity)
>
> ORDER(<u>OrderID</u>, OrderDate, CustomerID, CustomerName, CustomerAddress)

- **Second Normal Form (2NF)**: A relation is in 2NF if it is in 1NF and all non-key attributes are fully functionally dependent on the primary key.

> The non-key attributes that are partially dependent on the primary key are ProductName and ProductPrice, which are dependent on ProductID only but not on OrderID.
>
> ORDERLINE(<u>OrderID*</u>, <u>ProductID*</u>, Quantity)
>
> ORDER(<u>OrderID</u>, OrderDate, CustomerID, CustomerName, CustomerAddress)
>
> PRODUCT(<u>ProductID</u>, ProductName, ProductPrice)

- **Third Normal Form (3NF)**: A relation is in 3NF if it is in 2NF and all the transitive dependencies are removed.

> The transitive dependency is CustomerName and CustomerAddress, which are dependent on CustomerID that is dependent on OrderID.
>
> (OrderID → CustomerID → CustomerName, CustomerAddress)
>
> ORDERLINE(<u>OrderID*</u>, <u>ProductID*</u>, Quantity)
>
> PRODUCT(<u>ProductID</u>, ProductName, ProductPrice)
>
> ORDER(<u>OrderID</u>, OrderDate, CustomerID*)
>
> CUSTOMER(<u>CustomerID</u>, CustomerName, CustomerAddress)

## Chapter 6: Indexing

- Application

## Chapter 7: Physical Database Design

- B+ Tree, Hashing

## Chapter 8: Transaction Processing

- Concurrency Control
