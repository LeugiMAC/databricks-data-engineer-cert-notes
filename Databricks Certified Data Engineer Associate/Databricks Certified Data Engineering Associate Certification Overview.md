git #databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

--- 
## Overview

### Audience
- Target Audience: Data Engineer
- About 6 months experience with Databricks

### Expectations

- Understand how to use and the benefits of using the Databricks Lakehouse Platform and its tools
- Built ETL pipelines using Apache Spark SQL and Python
- Incrementally process data
- Build production pipelines for data engineering applications and Databricks SQL queries and dashboards
- Understand and follow bet security practices

### Out of scope
- Apache Spark internals
- Databricks CLI
- Databricks REST API
- Change Data Capture
- Data modelling concepts
- Notebooks and Jobs permissions
- PII
- GDPR/CCPA
- Monitoring and logging production jobs
- Dependency management 
- Testing

### Certification updated details
[Certification details](https://databricks.com/learn/certification/data-engineer-associate)

### Platform
[Kryterion's Webassessor platform](https://webassessor.com/databricks)

### Proctored exam (virtually):
- Monitor you during the exam
- Provide technical support

### Exam grading:
- Certification exams are automatically graded
- You will receive your pass/fail grade immediately
- Topic-Level percentage scores to assist you in focusin any study efforts 
- Proctor can affect the qualification depending on your conduct

### Exam details
- 90 minutes
- 45 question
- At least 70% is required to pass the exam
- Fee = $200
- As many times ayou want, whenever you want

---
## Topics

### Lakehouse Platform (24%)

- Lake House Platform
	- **Lake House**: Description, benefits 
		- Components: Data Lake House vs Data Lakehouse vs Data Warehouse, Data Quality improvements 
		- Platform architecture: Core services, High level architecture and key components
		- Benefits to Data Teams: Data problems solved, benefits to different roles in a data team
	
	- **Data Science and Engineering Workspace**: Clusters, DBFS, Notebooks, Repos
		- Clusters: All purpose clusters vs Jobs clusters. Cluster instances and pools
		- Databricks File System (DBFS): Managing permissions on tables, Role permission and functions, Data Explorer
		- Notebooks: Features and limitations, Collaboration best practices
		- Repos: Supported features and git operations. Relevance in CI/CD workflows in Databricks
	
	- **Delta Lake**: General concepts, table management, table manipulation, optimisations
		- Common table operations: ACID transactions on a data lake. Features and benefits
		- Table management and manipulations
		- Optimisations: supported features and benefits. Table utilities

### ELT with Spark SQL and Python (29%)

- **Built ETL pipelines using Apache Spark SQL and Python**
	- **Relation entities** 
		- DBs: Specify location, Retrieve location, Modify and delete databases
		- Tables: Managed vs External 
		- Views: Regular, Temporary, Delta Lake Tables
	
	- **ELT**: Transforming data, UDF
		- Manipulating data with Spark SQL and Python
		- External Sources vs Delta Lake tables
		- Methods to create tables and use cases
		- Delta table configurations
		- Different file formats and data sources
		- Crete Table As Select Statements (CTE)
		- Methods to write to tables and use cases 
		- Efficiency for different operations
		- Resulting behaviours in target tables
		- Cleaning data with common SQL
		- Combining data: Joins and strategies
		- Reshaping data: Arrays, Array Functions and Higher Order Functions
		- Advanced Operations: Manipulating nested data fields, Applying SQL UDF for custom transformations
		
	- **Just Enough Python**
		- Spark SQL Queries:
		- Passing data to SQL: Converting from/to DataFrames
		- Python syntax: Functions, Variables, Control Flow, Error handling

### Incremental Data Processing (22%)

- Incremental Data Processing
	- Structured Streaming 
		- General concepts: Programming model, configuration for reads and writes, fault tolerance, streaming queries
		- Triggers: Set up streaming writes with different trigger behaviours
		- Watermarks: Unsupported operations on streaming data, Scenarios in which watermarking data would be necessary, managing state with watermarking
		
	- Auto Loader
		- Define streaming reads with Auto Loader and PySpark to load data into Delta
		- Define streaming reads on tables for SQL manipulation
		- Identifying source locations
		- Use cases for using Auto Loader
		
	- Multi-hop Architecture
		- Bronze tables
		- Silver & Gold tables
		- Streaming Applications in Multi-Hop
		
	- Delta Live Tables (Benefits and features)
		- Scenarios that benefit from DLT
		- UI: DLT Pipelines, Updates, Evaluate results from DLT pipelines
		- SQL Syntax: Converting regular SQL DDL to DLT

### Production Pipelines (16%)

- Pipelines in Production
	- Workflows 
		- Cluster Pools
		- Retry policies
		- Job Scheduling
		- Tasks orchestration
		- UI
	- Dashboards
		- SQL Warehouses
		- Scheduling 
		- Alerting (Queries, Failures)
		- Refreshing

### Data Governance (6%)

- Governance and Security
	- Unity Catalog
		- Benefits
		- Features
	- Entity Permissions
		- Granting different levels of permissions to for users and/or groups

---

## Type of questions

[Practice exam](https://databricks.com/learn/certification/data-engineer-associate)

1. Single answer from a multi-select option. 
2. Single answer from a multi-select options. Scenario with **SQL code block** 
3. Single answer from a multi-select options. Scenario with **Python code block**

---

## Exam Preparation
Data engineering pathway
	Self-paced E-Learning
	Instructor Led Training (ILT)
	Major events


--- 

### Practice Exam

#### Which of the following describes a benefit of a data lakehouse that is unavailable in a traditional data warehouse?
[[Databricks DE Module 02 . Delta Lake]]
				
- [ ] A data lakehouse provides a relational system of data management
- [ ] A data lakehouse enables both batch and streaming analytics
- [ ] A data lakehouse captures snapshots of data for version control purposes
- [ ] A data lakehouse utilises proprietary storage formats for data
- [o] A data lakehouse enables both batch and streaming analytics 



#### Which of the following locations hosts the driver and worker nodes of a Databricks-managed cluster? 
[[Databricks DE Module 01. Workspaces and Services]]
				
- [ ] Data plane
- [o] Control plane
- [ ] Databricks Filesystem
- [ ] JDBC data source
- [ ] Databricks web application



#### Two junior data engineers are authoring separate parts of a single data pipeline notebook. They are working on separate Git branches, so they can pair program on the same notebook simultaneously. A senior data engineer experienced in Databricks suggest there is a better alternative for type of collaboration. 
[[Databricks DE Module 01. Workspaces and Services]]

- [ ] Databricks Notebooks support automatic change-tracking and versioning
- [o] Databricks Notebooks support real-time co-authoring on a single notebook
- [ ] Databricks Notebooks support commenting and notification comments
- [ ] Databricks Notebooks support the use of multiple languages in the same notebook
- [ ] Databricks Notebooks support the creation of interactive data visualisations



#### Which of the following describes how Databricks Repos can help facilitate CI/CD workflows on the Databricks Lakehouse Platform?
[[Databricks DE Module 01. Workspaces and Services]]

- [ ] Databricks Repos can facilitate the pull request, review, and approval process before merging branches
- [ ] Databricks Repos can merge changes from a secondary Git branch into a main Git branch
- [ ] Databricks Repos can be used to design, develop, and trigger Git automation pipelines
- [ ] Databricks Repos can store the single-source-of-truth Git repository
- [o] Databricks Repos can commit or push code changes to trigger a CI/CD process



#### A data engineer needs to create a database called customer360 at the location '/customer/customer360'. The data engineer is unsure if one of their colleagues has already created the database. Which of the following commands should the data engineer run to complete this task?
[[Databricks DE Module 04. ETL with Spark SQL]]

- [ ] `CREATE DATABASE customer360 LOCATION '/customer/customer360';`
- [ ] `CREATE DATABASE IF NOT EXISTS customer360;`
- [ ] `CREATE DATABASE IF NOT EXISTS customer360 LOCATION '/customer/customer360';'
- [o] `CREATE DATABASE IF NOT EXISTS customer360 DELTA LOCATION '/customer/customer360';`
- [ ] `CREATE DATABASE customer360 DELTA LOCATION '/customer/customer360';`



#### A data engineering team has created a series of tables using Parquet data stored in an external system. The team is noticing that after appending new rows to the data in the external system, their queries within Databricks are not returning the new rows. They identity the caching of the previous data as the cause of this issue. Which of the following approaches will ensure that the data returned by queries is always up-to-date?
[[Databricks DE Module 08. Delta Live Tables]]

- [o] The tables should be converted to the Delta format
- [ ] The tables should be stored in a cloud-based external system
- [ ] The tables should be refreshed in the writing cluster before the next query is run
- [ ] The tables should be altered to include metadata to not cache
- [ ] The tables should be updated before the next query is run



#### A data engineer is overwriting data in a table by deleting the table and recreating the table. Another data engineer suggests that this is inefficient, and the table should simply be overwritten instead. Which of the following reason to overwrite the table instead of deleting and recreating the table is incorrect?
[[Databricks DE Module 04. ETL with Spark SQL]]

- [ ] Overwriting a table is efficient because no files need to be deleted
- [o] Overwriting a table results in a clean table history for logging and audit purposes
- [ ] Overwriting a table maintains the old version of the table for Time Travel
- [ ] Overwriting a table is an atomic operation and will not leave the table in an unfinished state
- [ ] overwriting a table allows for concurrent queries to be completed while in progress



#### What is true about ARRAY Function according to the below use case?
[[Databricks DE Module 04. ETL with Spark SQL]]

A junior data engineer has ingested a JSON file into a table 'raw_table' with the following schema: 

```sql
cart_id STRING
items ARRAY<item_id:STRING>
```

The junior data engineer would like to unnest the items' column in 'raw_table' to result in a new table with the following schema: 

```sql 
cart_id STRING, 
item_id STRING
```

Which of the following commands should the junior data engineer run to complete this task?

- [ ] `SELECT cart_id, filter(items) AS item_id FROM raw_table;`
- [ ] `SELECT cart_id, flatten(itmes) AS item_id FROM raw_table;`
- [ ] `SELECT cart_id, reduce(items) AS item_id FROM raw_table;`
- [o] `SELECT cart_id, explode(items) AS item_id FROM raw_table;`
- [ ] `SELECT cart_id, slice(items)  AS item_id FROM raw_tables;`



#### Which is true about the ARRAY functions according to the below use case?
[[Databricks DE Module 04. ETL with Spark SQL]]

A data engineer has ingested a JSON file into table 'raw_table' with the following schema:

```sql
trasaction_id STRING, 
payload ARRAY<customer_id:STRING, date:TIMESTAMP, store_id:STRING>
```

The data engineer wants to efficiently extract the date of each transaction into a table with the following schema:

```sql
transaction_id STRING, 
date TIMESTAMP
```

Which of the following commands should the data engineer run to complete this tasks?

- [ ] `SELECT transaction_id, explode(playload) FROM raw_table;`
- [o] `SELECT transaction_id, payload.date FROM raw_table;`
- [ ] `SELECT transaction_id, date FROM raw_table;`
- [ ] `SELECT transaction_id, payload[date] FROM raw_table;`
- [ ] SELECT transaction_id, date from payload FROM raw_table;



#### Which of the following data workloads will utilise a Bronze table as its source?
[[Databricks DE Module 07. Multi-Hop Architecture]]

- [ ] A job that aggregates cleaned data to created standard summary statistics
- [ ] A job that queries aggregated data to publish key insights into a dashboard
- [ ] A job that ingests raw data from a streaming source into the Lakehouse
- [ ] A job that develops a feature set for a machine learning application
- [o] A job that enriches data by parsing its timestamps into a human-readable format



### Which of the following data workloads will utilise a silver table as its source?
[[Databricks DE Module 07. Multi-Hop Architecture]]

- [ ] A job that enriches data by parsing its timestamps into a human-readable format
- [ ] A job that queries aggregated data that already feeds into a dashboard
- [ ] A job that ingests raw data from a streaming source into the Lakehouse
- [ ] A job that aggregates cleaned data to created standard summary statistics
- [ ] A job that cleans data by removing malformatted records



#### Which of the following Structured Streaming queries is performing a hop from a Bronze table to a Silver table?
[[Databricks DE Module 06. Incremental Data Processing]]

- [ ] A 
```python
-   (spark.table("sales")  
        .groupBy("store")  
        .agg(sum("sales"))                          
        .writeStream                                                  
        .option("checkpointLocation", checkpointPath)  
        .outputMode("complete")  
        .table("aggregatedSales")  
    )
```

- [ ] B 
```python
  (spark.table("sales")  
        .agg(sum("sales"),  
             sum("units"))                  
        .writeStream                                                  
        .option("checkpointLocation", checkpointPath)  
        .outputMode("complete")  
        .table("aggregatedSales")  
    )
```

- [o] C 
```python
  (spark.table("sales")  
        .withColumn("avgPrice", col("sales") / col("units"))                            
        .writeStream                                              
        .option("checkpointLocation", checkpointPath)  
        .outputMode("append")  
        .table("cleanedSales")  
    )
```

- [ ] D 
```python 
  (spark.readStream.load(rawSalesLocation)                
        .writeStream                                                  
        .option("checkpointLocation", checkpointPath)  
        .outputMode("append")  
        .table("uncleanedSales")  
    )
```

- [ ] E 
```python
   (spark.read.load(rawSalesLocation)                
        .writeStream                                                  
        .option("checkpointLocation", checkpointPath)  
        .outputMode("append")  
        .table("uncleanedSales")  
    )
```



#### A data engineer has three notebooks in an ELT pipeline. The notebooks need to be executed in a specific order for the pipeline to complete successfully. The data engineer would like to use Delta Live Tables to manage this process. Which of the following steps must the data engineer take as part of implementing this pipeline using Delta Live Tables?
[[Databricks DE Module 09. Task Orchestration with Databricks Jobs]]

- [ ] They need to create a Delta Live Tables pipeline from the Data page 
- [o] They need to create a Delta Live Tables pipeline from the Jobs page
- [ ] They need to create a Delta Live Tables pipeline from the Compute page
- [ ] They need to refactor their notebook to use Python and the DLT library
- [ ] They need to refactor their notebook to use SQL and CREATE LIVE TABLE keyword



#### A dataset has been defined using Delta Live Tables and includes an expectation clause. What is the expected behaviour when a batch of data containing data that violates these constraints is processed?
[[Databricks DE Module 08. Delta Live Tables]]

```sql 
CONSTRAINT valid_timestamp EXPECT (timestamp>'2020-01-01')
```

- [ ] Records that violate the expectation are added to the target dataset and recorded as invalid in the event log
- [o] Records that violate the expectation are dropped from the target dataset and recorded as invalid in the event log.
- [ ] Record that violate the expectation cause the job to fail
- [ ] Records that violate the expectation are added tot the target dataset and flagged as invalid in a field added to the target dataset
- [ ] Records that violate the expectation are dropped from the target dataset and loaded into quarantine table



### A Delta Live Table pipeline includes two datasets defined using STREAMING LIVE TABLE. Three datasets are defined against Delta Lake table sources using LIVE TABLE. The table is configured to run in Development mode using the Triggered Pipeline Mode Assuming previously unprocessed data exists, and all definitions are valid, what is the expected outcome after clicking Start to update the pipeline?
[[Databricks DE Module 08. Delta Live Tables]]

- [ ] All dataset will be updated once and the pipeline will shut down. The compute resources will be terminated
- [ ] All datasets will be updated at set intervals until the pipeline is shut down. The compute resources will be deployed for the update and terminated when the pipeline is stopped
- [ ] All datasets will be updated t set intervals until the pipeline is shut down. The compute resources will persist after the pipeline is stopped to allow for additional testing
- [o] All dataset will be updated once and the pipeline will shut down. The compute resources will persist to allow for additional testing. 
- [ ] All datasets will be updated continuously, and the pipeline will not shut down. The compute resources will persist with the pipeline



#### A data engineer has a job with multiple tasks that runs nightly. One of the tasks unexpectedly fails during 10 percent of the runs. Which of the following actions can the data engineer perform to ensure the job completes each night while minimising compute costs?

- [ ] They can institute a retry policy for the entire job
- [ ] They can observe the tasks as it runs to try and determine why it is failing
- [ ] They can set up the job to run multiple times, ensuring that at east one will complete
- [o] They can institute a retry policy for the task that periodically fails
- [ ] They can utilise a jobs cluster for each of the tasks in the job



A data engineering team has been using a Databricks SQL query to monitor the performance of an ELT job. The ELT job is triggered by a specific number of input records being ready to process. The Databricks SQL query returns the number of minutes since the job's most recent runtime. Which of the following approaches can enable the data engineering team to be notified if the ELT job has not been run in an hour?

- [ ] They can set up an Alert for the accompanying dashboard to notify them if the returned value is greater than 60
- [ ] They can set up an Alert for the query to notify when the ELT job fails
- [ ] They can set up an Alert for the accompanying dashboard to notify when it has not refreshed in 60 minutes
- [o] They can set up an Alert for the query to notify them if the returned value is greater than 60
- [ ] This type of alerting is not possible in Databricks


#### A data engineering manager has noticed that each of the queries in a Databricks SQL dashboard takes a few minutes to update when they manually click the "Refresh" button. They are curious why this might be occurring, so a team member provides a variety of reason on why the delay might be occurring. Which of the following reason fails to explain why the dashboard might be taking a few minutes to update?

- [ ] The SQL endpoint being used by each of the quires might need a few minutes to start up
- [ ] The queries attached to the dashboard might take a few minutes to run under normal circumstances
- [ ] The queries attached to the dashboard might first be checking to determine if new data in available
- [o] The job associated with updating the dashboard might be using a non-pooled endpoint.
- [ ] The queries attached to the dashboard might all be connected to their own, unstarted Databricks cluster.


# My Results

Databricks Certified Data Engineer Associate, earned on 28 November 2022.  
  
- Overall Score: 82.22%  
	- Topic Level Scoring:  
		- Databricks Lakehouse Platform: 81.81%  
		- ELT with Spark SQL and Python: 84.61%  
		- Incremental Data Processing: 91.66%  
		- **Production Pipelines: 57.14%**  
			- Scheduler
			- Pools
			- Consumption
			- Alerts
		- Data Governance: 100.00%

Journey: 
- ILT training - [Course Link](https://partner-academy.databricks.com/learn/course/809/session/1350/data-engineering-with-databricks-class-8481-accenture-australia)
- Self-pace Training - [Course Link](https://partner-academy.databricks.com/learn/course/62/data-engineering-with-databricks-v2;lp=10)
- Full dedication from the 17th Nov until the 28 November (about 6 days) 
