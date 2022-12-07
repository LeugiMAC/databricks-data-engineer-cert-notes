#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

- **Metastore**:  Contains all of the metadata that defines data objects in the Lakehouse.
	-   Unity Catalog: Share metadata across multiple Databricks workspaces. Managed at a account level.
	-   Hive Metastore: Stores all the metadata for the built-in Hive Metastore as a managed service.
	-   External Metastore: You can bring your own Metastore to Databricks
- **Catalog:** a grouping of databases
-  **Database:** or schema: A grouping of object in in a catalog. Databases contain tables, views, and functions.
- **Table**: A collection of rows and columns stored as data files in object storage.
	-   Managed: Both metadata and the data are managed by Databricks
	-   Unmanaged (external): Databricks only manages the metadata
- **View**: A saved query typically against one or more tables or data sources.
	-   Regular views
	-   Temporary views: Persist based on the scope or environment that is used
		-   Global. Scope is the Cluster. Can be used by other queries and notebooks
		-   Notebook Level
		-   Query Level
- **Function**: Saved logic that returns a scalar value or set of rows.