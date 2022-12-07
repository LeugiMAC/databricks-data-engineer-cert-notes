#databricks #dataengineering
# Course

[Course Link](https://partner-academy.databricks.com/learn/course/809/session/1350/data-engineering-with-databricks-class-8481-accenture-australia)
Instructor Led Training

## Content:


[Databricks DE Module 01. Workspaces and Services](Databricks%20DE%20Module%2001.%20Workspaces%20and%20Services.md)
[Databricks DE Module 02 . Delta Lake](Databricks%20DE%20Module%2002%20.%20Delta%20Lake.md)
[Databricks DE Module 03. Relational Objects](Databricks%20DE%20Module%2003.%20Relational%20Objects.md)
[Databricks DE Module 04. ETL with Spark SQL](Databricks%20DE%20Module%2004.%20ETL%20with%20Spark%20SQL.md)
[Databricks DE Module 05. Python for Spark](Databricks%20DE%20Module%2005.%20Python%20for%20Spark.md)
[Databricks DE Module 06. Incremental Data Processing](Databricks%20DE%20Module%2006.%20Incremental%20Data%20Processing.md)
[Databricks DE Module 07. Multi-Hop Architecture](Databricks%20DE%20Module%2007.%20Multi-Hop%20Architecture.md)
[Databricks DE Module 08. Delta Live Tables](Databricks%20DE%20Module%2008.%20Delta%20Live%20Tables.md)
[Databricks DE Module 09. Task Orchestration with Databricks Jobs](Databricks%20DE%20Module%2009.%20Task%20Orchestration%20with%20Databricks%20Jobs.md)
[Databricks DE Module 10. Databricks SQL Query](Databricks%20DE%20Module%2010.%20Databricks%20SQL%20Query.md)
[Databricks DE Module 11. Data Governance](Databricks%20DE%20Module%2011.%20Data%20Governance.md)
[Databricks DE Module 12. Last Mile ETL with DBSQL](Databricks%20DE%20Module%2012.%20Last%20Mile%20ETL%20with%20DBSQL.md)


# Exam

[Databricks Certified Data Engineering Associate Certification Overview](Databricks%20Certified%20Data%20Engineering%20Associate%20Certification%20Overview.md)

[Data Engineer Associate Exam](https://www.databricks.com/learn/certification/data-engineer-associate)

# Environment

- [Slack](https://dewddatabricks.slack.com/ssb/redirect?entry_point=workspace_signin)
- [https://bit.ly/3qqWFMX](https://bit.ly/3qqWFMX)

Code: ACTIVATE26051
	[Databricks Workspace URL](https://adb-1152812542371705.5.azuredatabricks.net)

Username: `odl_user_728203@databrickslabs.com`
Password: `owzs74VYK*Ui`

[GitHub Repo](https://github.com/databricks-academy/data-engineering-with-databricks-english)
[Slides](https://github.com/databricks-academy/data-engineering-with-databricks-english/releases)

# Additional documentation

## Delta Lake

-   [https://delta.io/](https://delta.io/)

## Spark

-   [General](https://spark.apache.org/docs/latest/)
-   [Components](%09https:/spark.apache.org/docs/3.3.0/cluster-overview.html#components)
-   [Transformation](https://spark.apache.org/docs/latest/rdd-programming-guide.html#transformations) and [actions](https://spark.apache.org/docs/latest/rdd-programming-guide.html#actions)
-   [Web UI](https://spark.apache.org/docs/latest/web-ui.html)
-   [A deep dive into structured streaming](https://www.youtube.com/watch?v=rl8dIzTpxrI)

## Databricks resources

-   [Data objects](https://docs.databricks.com/lakehouse/data-objects.html)
-   [Databricks DBFS](https://docs.databricks.com/dbfs/index.html)
-   [DBUtils](https://docs.databricks.com/dev-tools/databricks-utils.html)
-   [Operations and privileges](https://docs.databricks.com/security/access-control/table-acls/object-privileges.html#operations-and-privileges)
-   [Reading CSV files](https://docs.databricks.com/data/data-sources/read-csv.html)
-   [Delta Lake](https://docs.databricks.com/delta/quick-start.html)d
-   [Delta Lake definitive guide](https://www.databricks.com/p/ebook/delta-lake-the-definitive-guide-by-oreilly)
-   [Best practices for dropping a managed Delta Lake table](https://docs.microsoft.com/en-us/azure/databricks/kb/delta/drop-delta-table)
-   [Time travel](https://docs.databricks.com/delta/delta-batch.html#examples)
-   [Vacuum](https://docs.databricks.com/spark/latest/spark-sql/language-manual/delta-vacuum.html)
-   [Data profiles](https://www.databricks.com/blog/2021/12/07/introducing-data-profiles-in-the-databricks-notebook.html)
-   [Global vs Temp View](http://community.databricks.com/s/question/0D53f00001GHVPFCA5/whats-the-difference-between-a-global-view-and-a-temp-view)

-   Advanced SQL Transformations
	-   [Databricks Joins](https://docs.databricks.com/spark/latest/spark-sql/language-manual/sql-ref-syntax-qry-select-join.html)
	-   [Higher-order functions](https://docs.databricks.com/optimizations/higher-order-lambda-functions.html)
-   Streaming Data
	-   Auto Loader
	-   [Table Streaming Reads and Writes](https://docs.databricks.com/delta/delta-streaming.html)
	-   [Structured Streaming Programming Guide](https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html)
	-   [A Deep Dive into Structured Streaming](https://www.youtube.com/watch?v=rl8dIzTpxrI) by Tathagata Das. This is an excellent video describing how Structured Streaming works.
	-   [Lambda Architecture](https://databricks.com/glossary/lambda-architecture)
	-   [Data Warehouse Models](https://bennyaustin.wordpress.com/2010/05/02/kimball-and-inmon-dw-models/#)
	-   [Create a Kafka Source Stream](http://spark.apache.org/docs/latest/structured-streaming-kafka-integration.html)

-   Delta Live Tables

-   [Databricks introductions](https://docs.databricks.com/workflows/delta-live-tables/index.html)
-   [Cookbook by Azure](https://learn.microsoft.com/en-us/azure/databricks/workflows/delta-live-tables/delta-live-tables-cookbook)
-   [Photon Acceleration](https://www.databricks.com/product/photon)

## Others

-   [https://www.youtube.com/c/AdvancingAnalytics/playlists](https://www.youtube.com/c/AdvancingAnalytics/playlists)

# Notes

## Table Types
# ## Managed Tables

- **Data management**: Spark manages both the metadata and the data
- **Location**: Data is saved in the Spark SQL warehouse directory /user/hive/warehouse. Metadata is saved in a meta-store of relational entities.
- **Data deletion**: The metadata and the data will be deleted after deleting the table.

### Unmanaged/External Tables

-   Data management: Spark manages only the metadata, and the data itself is not controlled by spark.
-   Data location: Source data location is required to create a table.
-   Data deletion: Only the metadata will be deleted. The tables saved in the external location.

## Open Source Projects

- Spartk
- Delta Lake
- MlFlow
- Koalas
- Redash

## Data Teams

- Data Analyst
- Data Engineers
- Data Scientists
- To produce Models, Dashboards, Notebooks and Datasets
