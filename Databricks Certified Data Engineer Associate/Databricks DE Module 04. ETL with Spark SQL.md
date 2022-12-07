#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)

# Querying External Sources

We can use Spark SQL to directly query data files:

This includes:
- Self describing files like: Parquet, JSON, delta
- Not self-describing files like: CSV, TXT, TSV
- Databases: through JDBC driver

The workspace administrator will require to connect to the external file location.

Regular Format:
```sql
<Format>.<Location>

Example:

SELECT * FROM json.`${da.paths.datasets}/raw/evetns-kafka`
```


There are options to define extra declarations to read the file properly.

```sql 
CREATE TABLE table_identifier (col_name1 col_type1, ...)
USING data_source
OPTIONS (key1 = val1, key2 = val2, ...)
LOCATION = path

CREATE TABLE sales_csv
  (order_id LONG, email STRING, transactions_timestamp LONG, total_item_quantity INTEGER, purchase_revenue_in_usd DOUBLE, unique_items INTEGER, items STRING)
USING CSV
OPTIONS (
  header = "true",
  delimiter = "|"
)
LOCATION "${da.paths.working_dir}/sales-csv"
```

It is important to note that table definition will not move the data. It will create a reference to the data, storing information about how to read the data. This will not ensure that performance will reach the Delta Lake standards

# Creating Delta Tables

To create delta tables it is necessary to use CTAS statements

CREATE TABLE _ AS SELECT (CTAS)

## Generated Columns

```sql
CREATE OR REPLACE TABLE purchase_date(
	id STRING,
	Trasaction_timestamp STRING,
	Price STRING,
	date DATE GENERATED ALWAYS AS (
		cast(cast(transaction_timestamp/1e6 AS TIMESTAMP) AS DATE)
	)
)

```


## Constraints

Databricks currently supports two types of constrains
-   Not null
-   Check

```sql
Example: 
ALTER TABLE <table_name> ADD CONSTRAINT valid_date CHECK (date > '2020-01-01')
```

A more sophisticated table would be:

```sql
CREATE OR REPLACE TABLE users_pii
COMMENT "Contains PII"
LOCATION "${da.paths.working_dir}/tmp/users_pii"
PARTITIONED BY (first_touch_date)
AS
  SELECT *,
    cast(cast(user_first_touch_timestamp/1e6 AS TIMESTAMP) AS DATE) first_touch_date,
    current_timestamp() updated,
    input_file_name() source_file
  FROM parquet.`${da.paths.datasets}/raw/users-historical/`;
 
SELECT * FROM users_pii;
```


# Cloning Tables

- Deep clones: Fully copies the data and metadata
- Shallow clone: Just copies the Delta transaction logs, meaning that the data doesn’t move

# Writing to tables

## Complete overwrites

-   Overwriting a table is much faster because it doesn't need to list the directory recursively or delete any files
-   The old version of the table still exists; it can easily retrieve the old data using Time Travel
-   It's an atomic operation. Concurrent queries can still read the table while you are deleting the table
-   Due to ACID transactions guarantees, if overwriting the table fails, the table will be in its previous state

Spark SQL provides two easy methods to accomplish complete overwrites:

-   (CRAS) statements

```sql
CREATE OR REPLACE TABLE events AS
SELECT * FROM parquet.`path/raw/events-historical`
```
-
- INSERT OVERWRITE

INSERT OVERWRITE sales

```sql
SELECT * FROM parquet.`path/raw/sales-historical`
INSERT OVERWRITE and CREATE OR REPLACE TABLE (CRAS) are nearly identical
```

The main difference between the two is that the CRAS statement will allow us to completely redefine the contents of our target table. INSERT OVERWRITE will fail if we try to change our schema (unless we provide optional settings)

## Append rows

This allows for incremental updates to existing tables, which is much more efficient than overwriting each time

Note that INSERT INTO does not have any built-in guarantess to prevent inserting the same record multiple times.

## Merge Updates / Upsert

```sql 
MERGE INTO target a
	USING source b ON {merge_condition}
WHEN MATCHED THEN {matched_action}
WHEN NOT MATCHED THEN {not_matched_action}

MERGE INTO users a
USING users_update b ON a.user_id = b.user_id
WHEN MATCHED AND a.email IS NULL AND b.email IS NOT NULL THEN
	UPDATE SET email = b.email, updated = b.updated
WHEN NOT MATCHED THEN INSERT *
```

The biggest advantage of this approach is that all the operations INSERT/UPDATE/DELETE are executed in one transaction.

## Insert-Only Merge for de-duplication

```sql
MERGE INTO events a
USING events_update b
ON a.user_id = b.user_id AND a.event_timestamp = b.event_timestamp
WHEN NOT MATCHED AND b.traffic_source = 'email' THEN
  INSERT *
```

This approach adds validations to avoid duplicates

## Load Incrementally

```sql
COPY INTO sales
FROM "${da.paths.datasets}/raw/sales-30m"
FILEFORMAT = PARQUET
```

Note that this operation does have some expectations:
-   Data schema should be consistent
-   Duplicate records should try to be excluded or handled downstream

# Cleaning data nested data

-   Conditions
-   Regex

## JSON Files

Select value from events_strings where value:event_name = "finalize"

-   From_json function: Parse JSON object into struct. However, it requires a schema
-   Schema_of_json function:  Derive the JSON schema from an example.
-   To unpack Spark supports * (star) to flatten fields into columns

```sql
 SELECT json.* FROM PARSED_EVENTS;
```

## Data Structures

Struct data types

We interact with the subfields in this field using standard "." syntex similar to how we might traverse nested data in JSON

```sql
SELECT  ecomerce.parchase_revenue FROM EVENTS
```

### Arrays

-   The `explode` function lets us put each element in an array on its own row
```sql
SELECT user_id, event, EXPLODE(items) as item FROM EVENTS
```

-   The `collect_set` function: Can collect unique values for a field, including fields within arrays
-   The `flatten` function allows multiple arrays to be combined into a single array
-   The `array_distinct` function removes duplicate elements from an array

```sql 
SELECT user_id,
  collect_set(event_name) AS event_history,
  array_distinct(flatten(collect_set(items.item_id))) AS cart_history
FROM events
GROUP BY user_id
```


## Join Tables

- **INNER**
- OUTER
- LEFT
- RIGHT
- (LEFT) ANTI
	- Returns values from the left relation that has no match with the right
- CROSS
- (LEFT) SEMI
	- Returns values from the left side of the relation that has match with the right
- NATURAL
	- Specifies that the rows from the two relations will implicitly be matched on equality for all columns with matching names

## Set operations

-   Union: Collection of two queries
-   Minus: returns all the rows found in one dataset but not the other
-   Intersect: Returns all rows found in both relations

## Pivot Tables (Rows to Columns)

The PIVOT clause is used for data perspective. We can get the aggregated values based on specific column values, which will be turned to multiple columns used in SELECT clause

## Higher Order Functions (ARRAYS)

-   FILTER: Filters an array using the given lambda function
-   EXIST: Tests whether a statement is true for one or more elements in an array
-   TRANSFORM: Uses the given lambda function to transform all elements in an array
-   REDUCE: Takes two lambda functions to reduce the elements of an array to a single value by merging the elements into a buffer, and the apply a finishing function on the final buffer.

### UDF (User Defined Functions)


# Examine Table Details

- Describe Extended: Allows us to see datatype, table type, partitioning
- Describe Detail: Includes more comprehensive metadata, like: `format`, `location`, `createdAt`, `lastModified` 

```sql
DESCRIBE EXTENDED <TableName>;
DESCRIBE EXTENDED students;

-- Database
DESCRIBE DATABASE EXTENDED <DatabaseName>
```


# Explore Delta File

```python
display(dbutils.fs.ls(f"{DA.paths.user_db}/students"))

display(spark.sql(f"SELECT * FROM json.`{DA.paths.user_db}/students/_delta_log/00000000000000000007.json`"))
```


# Reviewing Delta Lake Transaction

```sql
DESCRIBE HISTORY students
```

# Optimisation

Files will be combined toward an optimal size (scaled based on the size of the table) by using the `OPTIMIZE` command. 

`OPTIMIZE` Will replace existing data files by combining records and rewriting the results.
When executing `OPTIMIZE`, users can optionally specify one or several fields for `ZORDER` indexing. This will speed up data retrieval when filtering on provided fields by colocating data with similar values within data files

```sql
OPTIMIZE students 
ZORDER by id
```

# Rollback versions

```sql
-- Restore the employee table to a specific timestamp
RESTORE TABLE employee TO TIMESTAMP AS OF '2022-08-02 00:00:00';
 
-- Restore the employee table to a specific version number retrieved from DESCRIBE HISTORY employee
RESTORE TABLE employee TO VERSION AS OF 1;

-- Restore the employee table to the state it was in an hour ago
RESTORE TABLE employee TO TIMESTAMP AS OF current_timestamp() - INTERVAL '1' HOUR;


```
