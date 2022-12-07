#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

## Workflows

Workflows allows users to build ETL pipelines that are automatically managed, including ingestion, and lineage, using Delta Live Tables. You can also orchestrate any combination of Notebooks, SQL, Spark, ML Models, and dbt as a Job Workflow, including calls to other systems. 


### Jobs
A job is a way to run non-interactive code in a Databricks cluster. 

A job can consist of a single task or can be a large, multitask workflow with complex dependencies. Databricks manages the task orchestration, cluster management, monitoring, and error reporting for all of your jobs. You can run your jobs immediately or periodically through an easy-to-use scheduling system.

#### Tasks Types
- Notebook
- JAR: Main class
	- Example `org.apache.spark.examples.SparkPi`
- Spark Submit
- Python script
	-  Example: `dbfs:/FileStore/myscript.py`
- Python Wheel
- SQL
	- Query
	- Dashboard
	- Alert
- dbt jobs
- Delta Live Table Pipelines

We can edit: 
- Notifications
- Parameters
- Dependencies
- Retry Policies
- Timeouts
- Permissions
- Maximum concurrent runs

Tags