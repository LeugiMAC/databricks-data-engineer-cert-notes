#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

## Recap

1. The Databricks workspace contains a suite of tool to simplify the data engineering development lifecycle
2. Databricks notebooks allow users to mix SQL with other programming languages to define ETL workloads
3. Delta Lake provide ACID compliant transactions and makes incremental data processing easy in the Lake House
4. Delta Live Tables extends the SQL syntax to support many design patterns in the Lake House, and simplifies infrastructure deployment
5. Multi-task jobs allow us for full task orchestration, adding dependencies while scheduling a mix of notebooks and DLT pipelines
6. Databricks SQL allows users to edit and execute SQL queries, build visualisation, and define dashboards
7. Data Explorer simplifies managing Table Permissions, making Lake House data available to SQL analysts 

### Last Mile

Databricks allow users to: 
- Create and schedule queries 
- Create and schedule dashboards
- Create and schedule alerts


### End-to-End ETL in the Lake House

Example:

- Using Databricks notebooks to write queries in SQL and Python
- Creating and modifying databases, tables, and views
- Using Auto Loader and Spark Structured streaming for incremental data processing in a multi-hop architecture
- Using Delta Live Table SQL Syntax 
- Configuring a Delta Live Table pipeline for continuous processing 
- Using Delta Live Table pipeline for continuous processing
- Using Databricks Jobs to orchestrate tasks from notebook stored in Repos
- Setting chronological scheduling for Databricks Jobs
- Defining queries in Databricks SQL
- Creating visualisations in Databricks SQL
- Defining Databricks SQL dashboards to review metrics and results