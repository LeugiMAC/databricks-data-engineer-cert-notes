#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

Delta Live Tables is a framework for building reliable, maintainable, and testable data processing pipelines. You define the transformations to perform on your data, and Delta Live Tables manages task orchestration, cluster management, monitoring, data quality, and error handling.

Instead of defining your data pipelines using a series of separate Apache Spark tasks, Delta Live Tables manages how your data is transformed based on a target schema you define for each processing step. You can also enforce data quality with Delta Live Tables _expectations_. Expectations allow you to define expected data quality and specify how to handle records that fail those expectations.

### Benefits:
- **Operate with agility**: Declarative tools to build batch and streaming data pipelines
- **Trust your data**: DLT has built-in declarative quality controls
- **Scale with reliability**: Easily scale infrastructure alongside your data

### Concepts:
The main unit of execution in Delta Live Tables is a pipeline. A pipeline is a DAG linking data sources to target datasets. 

DAG ⇾ Directed Acyclic Graph

#### Expectations
You use expectation to specify data quality controls on the contents of a dataset. Unlike `CHECK` constraint in a traditional database which prevents adding any records that fail the constraint, expectations provide flexibility when processing data that fails data quality requirements.

You can define expectations to retain records that fail validation, drop records, or halt the pipeline

#### Datasets

There are two types of datasets in a Delta Live Tables pipeline: _views_ and _tables_.

-   **Views** are similar to a temporary view in SQL and are an alias for some computation. A view allows you to break a complicated query into smaller or easier-to-understand queries. Views also allow you to reuse a given transformation as a source for more than one table. Views are available within a pipeline only and cannot be queried interactively.
    
-   **Tables** are similar to traditional materialised views. The Delta Live Tables runtime automatically creates tables in the [Delta](https://docs.databricks.com/delta/tutorial.html#create) format and ensures those tables are updated with the latest result of the query that creates the table.
    
You can define a _live_ or _streaming live_ view or table:

A **live table or view** always reflects the results of the query that defines it, including when the query defining the table or view is updated, or an input data source is updated. Like a traditional materialised view, a live table or view may be entirely computed when possible to optimise computation resources and time.

A **streaming live table** or view processes data that has been added only since the last pipeline update. Streaming tables and views are stateful; if the defining query changes, new data will be processed based on the new query and existing data is not recomputed.

Streaming live tables are valuable for a number of use cases, including:

-   Data retention: a streaming live table can preserve data indefinitely, even when an input data source has low retention, for example, a streaming data source such as Apache Kafka or Amazon Kinesis.
    
-   Data source evolution: data can be retained even if the data source changes, for example, moving from Kafka to Kinesis.
    
You can [publish](https://docs.databricks.com/workflows/delta-live-tables/delta-live-tables-publish.html) your tables to make them available for discovery and querying by downstream consumers.

### SQL Pipeline to Delta Live Tables

Example:


#### 1. Declare Bronze Tables
```sql 
CREATE OR REFRESH STREAMING LIVE TABLE recordings_bronze
AS SELECT current_timestamp() receipt_time, input_file_name() source_file, *
  FROM cloud_files("${source}", "json", map("cloudFiles.schemaHints", "time DOUBLE"))
```

```sql 
CREATE OR REFRESH STREAMING LIVE TABLE pii
AS SELECT *
  FROM cloud_files("/mnt/training/healthcare/patient", "csv", map("header", "true", "cloudFiles.inferColumnTypes", "true"))
```

#### 2. Declare Silver Tables

```sql 
CREATE OR REFRESH STREAMING LIVE TABLE recordings_enriched
  (CONSTRAINT positive_heartrate EXPECT (heartrate > 0) ON VIOLATION DROP ROW)
AS SELECT
  CAST(a.device_id AS INTEGER) device_id,
  CAST(a.mrn AS LONG) mrn,
  CAST(a.heartrate AS DOUBLE) heartrate,
  CAST(from_unixtime(a.time, 'yyyy-MM-dd HH:mm:ss') AS TIMESTAMP) time,
  b.name
  FROM STREAM(live.recordings_bronze) a
  INNER JOIN STREAM(live.pii) b
  ON a.mrn = b.mrn
```

#### 3. Define Gold Table

```sql
CREATE OR REFRESH STREAMING LIVE TABLE daily_patient_avg
  COMMENT "Daily mean heartrates by patient"
  AS SELECT mrn, name, MEAN(heartrate) avg_heartrate, DATE(time) `date`
    FROM STREAM(live.recordings_enriched)
    GROUP BY mrn, name, DATE(time)
```

#### 4. Display results

```sql 
SELECT * FROM ${da.db_name}.daily_patient_avg
```

Re-run the pipeline to get the most up-to-date results
