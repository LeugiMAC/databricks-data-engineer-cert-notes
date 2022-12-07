#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

### Delta Lake is not …

-   Proprietary technology
-   Storage format
-   Storage medium
-   Database service or data warehouse

### Delta Lake is …

-   Open Source
-   Builds upon standard data formats

-   Parquet is the most common

-   Optimised for cloud objects storage
-   Built for scalable metadata handling

### Delta Lake brings ACID to object storage

-   Atomicity. All transaction either succeed or fail
-   Consistency. Given state of data is consumed by others
-   Isolation. How simultaneous operations conflict with one another
-   Durability. Committed changes are permanent

### Considerations

-   Delta Lake allow us to time travel by accessing previous versions of the tables
	-   This also includes the RESTORE command to rollback
-   Delta Lake tables are the default type of tables created in Databricks
-   Delta Lake has a default retention period of 7 days. There are options to manipulate that parameters but, it is not recommended.
	-   The VACUUM command will delete files that were marked for deletion and commit a new version of the table
	-   There is an option to inspect the files before they are deleted. The command is DRY RUN

### Top 5 reason to move to Delta Lake

1. Prevent Data Corruption
2. Faster queries
3. Increase Data Freshness
4. Reproduce ML Models
5. Achieve Compliance
