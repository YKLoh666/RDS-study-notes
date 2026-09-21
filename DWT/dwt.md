# BMIT3003 Data Warehouse Technology

## Why OLTP is not best solution for business intelligence reporting

| Aspect                | OLTP System                                                             | Data Warehouse                                                 |
| --------------------- | ----------------------------------------------------------------------- | -------------------------------------------------------------- |
| **Workload**          | Supports only predefined operations                                     | Supports ad-hoc queries and analysis                           |
| **Data Modification** | Updated by end users manually by issuing statements                     | Automatically updated on a regular basis by ETL processes      |
| **Schema Design**     | Uses fully denormalized schema to ensure data integrity and consistency | Uses partially denormalized schema to optimize performance     |
| **Data Scanning**     | Access only a handful of records at a time                              | Encompasses thousands or millions of records in a single query |
| **Historical Data**   | Store data of only weeks or months                                      | Store data of years or decades                                 |

## Bottom-Up vs Top-Down Approach

- Use bottom-up if:
  - **Need low cost and fast**: Can build local data marts first and build a data warehouse later when the business is stable.
  - **High flexibility**: Adapt to evolving business needs and requirements, as data marts can be built independently.
  - **Faster Reporting**: Quicker insights and reporting for specific departments or business units, as data marts can be tailored to their needs.
- Use top-down if:
  - **Need organisation-wide data**: Consistent and integrated data across the organization.
  - **Need data consistency**: Single source of truth for the entire organization.
  - **Simplified maintenance**: Maintenance in data warehouse reflects in all data marts, easier to maintain and manage.
- Draw:
  - Bottom-Up Approach: Data Marts are built first, then integrated into a Data Warehouse.
  
  ```mermaid
  graph LR
    A[Source 1] --> D[ETL<br>Extract - Data extracted from various sources<br>Transform - Transform data to clean and standardize format. E.g. standardize date formats, capitalize names<br>Load - Load cleaned and transformed data into the staging area]
    B[Source 2] --> D
    C[Source 3] --> D
    D --> E[Data Mart 1]
    D --> F[Data Mart 2]
    D --> G[Data Mart 3]
    E --> H[Data Warehouse]
    F --> H
    G --> H
    H --> I[Data Mining/BI Reporting]
  ```

  - Top-Down Approach: Data Warehouse is built first, then data marts are created from it.
  
  ```mermaid
  graph LR
    A[Source 1] --> D[ETL<br><br>Extract - Data extracted from various sources<br><br>Transform - Transform data to clean and standardize format. E.g. standardize date formats, capitalize names<br><br>Load - Load cleaned and transformed data into the staging area]
    B[Source 2] --> D
    C[Source 3] --> D
    D --> H[Data Warehouse]
    H --> I[Data Mining/BI Reporting]
    H --> E[Data Mart 1]
    H --> F[Data Mart 2]
    H --> G[Data Mart 3]
  ```

## Why DWH should ideally by 3-tier architecture

> Context to help understand the architecture to answer the question:
>
> - **Bottom Tier**: Containing data source, ETL pipeline, and data storage (including data warehouse and data marts)
> - **Middle Tier**: Containing OLAP server, which preaggregates data and provides multidimensional views of data, so that users can perform complex queries and analysis efficiently without repeatedly scanning data from the bottom tier.
> - **Top Tier**: Containing business intelligence tools and techniques designed to help users easily access and manipulate data for reporting and analysis.

- **Scalability**: The 3-tier architecture allows for better scalability as each tier can be scaled independently based on the workload and requirements. For example, if the business expands and data volume increases, the bottom tier can be scaled up without affecting the middle and top tiers.
- **Performance**: The 3-tier architecture allows for better performance as each tier can be optimized for its specific function. For example, the bottom tier can be optimized for data storage and retrieval, while the middle tier can be optimized for query processing and analysis.
- **Security**: The 3-tier architecture allows for better security as each tier can be secured independently. For example, the bottom tier can be secured to prevent unauthorized access to the data, while the middle tier can be secured to prevent unauthorized access to the OLAP server.
- **Why not 1-tier**: Data Ingestion and Data Analysis are tightly coupled, which can lead to performance issues and difficulty in scaling the system.
- **Why not 2-tier**: No OLAP server, lead to performance issues when performing complex queries and analysis

## Is centralised architecture suitable?

> Context to help understand the architecture to answer the question:
>
> - No data marts, all data is stored in a single data warehouse
> - Provide timely and holistic view of the enterprise data to whomever, whenever, and wherever they need it

- **Yes** if
  - **Single source of truth**
  - **All historical data**
  - **Multidimensional analysis from all branches**
  - **Data quality, access, and security are managed centrally**
- **No** if
  - **Flexibility issues**
  - **Costly to develop and maintain**
  - **Single point of failure**
  - **Performance issues**: As the number of users and queries increases, the centralized architecture may become a bottleneck, leading to slower response times and decreased performance.
  - **Choose independent data marts if**: single source of truth is not required
  - **Choose hub-and-spoke if**: optimal local performance is required, but still need a single source of truth, but lack holistic view of the enterprise data, may has latency issues

## Centralised data warehouse major components

- **Data Sources**: Sources of data of the organisation that are integrated into the data warehouse.
- **Data Staging Area**: A temporary storage area where data are cleaned and transformed before being loaded into the data warehouse. ETL pipeline clean and transform data to ensure data quality and consistency.
- **Data Warehouse**: The central repository of integrated data that is used for reporting and analysis. Is partially denormalized to optimize performance.
- **Business Intelligence Delivery**: Multidimensional Database, OLAP server, Business Intelligence tools and techniques that allow users to access and manipulate data for reporting and analysis.

## Star Schema

- Use line to connect the dimension and fact tables is fine
- No need to indicate primary, foreign key, and composite key
- Sales fact no need key, must have unit price, quantity, amount and other dimension foreign keys
- Date dim must have key, year, quarter, month, week, calendar date
- Other dim must have key and id, ensure no dynamic attributes like age

## SCD Type 2

- Draw tables with single example of before and after update
- eff_start_date, eff_end_date, and current_flag are required
- explain how to handle the update
- **SCD Type 1**: not suitable as no historical data is kept due to being overwritten by new data
- **SCD Type 3**: not suitable as only the immediate previous value is kept, and historical data beyond that is lost

## How data warehouse maximise the information potential to assist decision making

- **Planning**: Analyse historical data relevant to the business objectives and goals to identify trends, patterns, and opportunities for growth. This can help in developing effective strategies and plans for the future.
- **Execution**: During execution, ingest the real-time data from various sources into the data warehouse to monitor the progress of the business operations for later analysis.
- **Assessment**: Use the data warehouse to assess the performance of the business operations against the set KPI, and target outcome. Use this outcome to plan future campaigns and strategies to improve the business operations.
- This loop will be repeated to ensure that the business operations are continuously improved and optimized for better performance and competitive advantage.

## How dashboard uses multidimensional data model

- **Drill down**: Allows users to navigate from summary data to more detailed data by clicking on a specific data point or dimension. For example, a user can drill down from total sales to sales by region, then to sales by product category, and finally to sales by individual products. This is useful for identifying trends and patterns in the data, as well as for identifying areas of improvement or concern.
- **Roll up**: Allows users to navigate from detailed data to summary data by aggregating data along a specific dimension. For example, a user can roll up sales data from individual products to product categories, then to regions, and finally to total sales. This is useful for getting a high-level overview of the data and for identifying trends and patterns at a broader level.
- **Cubes**: A cube is a multidimensional data structure that allows users to view and analyze data from multiple perspectives. Each dimension represents a different aspect of the data, such as time, geography, or product category. For example, a sales cube may have dimensions for time (e.g., year, quarter, month), geography (e.g., region, country, city), and product category (e.g., electronics, clothing, home goods). Users can slice and dice the data in the cube to view it from different angles and gain insights into the business operations.
- **Rotate**: Allows users to change the orientation of the data in the cube by swapping dimensions. For example, a user can rotate a sales cube to view sales data by product category instead of by geography. This is useful for exploring different perspectives of the data and for identifying trends and patterns that may not be apparent from a single perspective.
- Dashboard turn these information into visualisation such as heatmaps, line charts, bar charts, and pie charts to help users quickly understand the data and make informed decisions.
