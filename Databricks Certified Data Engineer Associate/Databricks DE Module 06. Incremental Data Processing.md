#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)


## Using Auto Loader

PySpark API

Note that when using Auto Loader with automatic schema inference and evolution, the 4 arguments shown here should allow ingestion of most datasets. These arguments are explained below.

-   data_source: The directory of the source data
-   source_format: The format of the source data (cloudFiles.format)
-   table_name: The name of the target table
-   checkpoint_directory: The location for storing metadata about the stream


```python
def autoload_to_table(data_source, source_format, table_name, checkpoint_directory):

    query = (spark.readStream
                  .format("cloudFiles")
                  .option("cloudFiles.format", source_format)
                  .option("cloudFiles.schemaLocation", checkpoint_directory)
                  .load(data_source)
                  .writeStream
                  .option("checkpointLocation", checkpoint_directory)
                  .option("mergeSchema", "true")
                  .table(table_name))
    return query
```

Example
```python
query = autoload_to_table(data_source = f"{DA.paths.working_dir}/tracker",
                          source_format = "json",
                          table_name = "target_table",
                          checkpoint_directory = f"{DA.paths.checkpoints}/target_table")
```

Becasue Auto Loader uses Spark Structured Streaming to load data incrementally,  the code above doesn't appear to finish executing. It is a **continuosly active query**. This mean that as soon as new data arrives in our data source, it will be processed through our logic and loaded into our target table

We can use DESCRIBE HISTORY to evaluate when the data was ingested:

```sql 
%sql
DESCRIBE HISTORY target_table
```

## Reasoning about incremental data

Incremental data allows users to interact with ever-growing data sources as if they were just a static table

### Basic concepts

- The developer defines an input table by configuring a streaming read against a **source** 
- A **query** is defined against the input table. Both the DataFrames API and Spark SQL can be used to easily define **transformations** and actions against the input table
- This logical query on the input table generates the **results table**. The results table contains the incremental state information of the stream.
- The **output** of a streaming pipeline will persist updates to the results table by writing to an external **sink**. Generally, a sink will be a durable system such as files or a pub/sub messaging bus.
- New rows are appended to the input table for each **trigger interval**.  These new rows are essentially analogous to micro-batch transactions and will be automatically propagated through the results table to the sink

For more information: [Structured Streaming Programming Guide](http://spark.apache.org/docs/latest/structured-streaming-programming-guide.html#basic-concepts)


### End-to-end Fault Tolerance

Structured Streaming source, sinks, and the underlying execution engine work together to track the progress of stream processing. If a failure occurs, the streaming engine attempts to restart and/or reprocess the data. For best practices on recovering from a failed streaming query, see:
[Recover from query failure documentation](https://docs.databricks.com/spark/latest/structured-streaming/production.html#recover-from-query-failures)

### Reading Stream

The spark.readStream() method retuns a DataSreamReader used to configure and query the stream.

```sql 
(spark.readStream
    .table("bronze")
    .createOrReplaceTempView("streaming_tmp_vw"))
```

**Note**: Generally speaking, Reading Streams are used for development of live dashboarding. 

### Unsupported Operations

Sorting is one of a handful of operations that either too complex or logically not possible to do when working with streaming data. Windowing and watermarking can be used to add additional functionality to incremental workloads


### Writing a Stream

If we create another temp view from the results of a query against a streaming temp view, we'll again have a streaming temp view. 

To persist the results of a streaming query, we must write them out to durable storage. The **`DataFrame.WriteStream`** used to configure the output. 

#### Checkpoints
Combines with write ahead logs to allow a terminated stream to be restarted and continue from where it left off.

#### Output Modes 
Streaming jobs have output modes similar to static/batch workloads. 

- Append (Default): Only newly appended rows are incrementally appended to the target table 
- Complete: The results table is recalculated each time a "write" is triggered (Overwrite)

#### Trigger Interval 
Specifies when the system should process the next set of data

- Unspecified (Default): `ProccesingTime = "500ms"`
- Fixed interval micro-batches: User specififed intervals
- Triggered micro-batch: Single micro-batch to process all the available data and then stop on its own
- Triggered micro-batches: Multiple micro-batches to process all the available data and then stop on its own

**Example:**
```python
(spark.table("device_counts_tmp_vw")  # Temp Streaming View                             
    .writeStream                                                
    .option("checkpointLocation", f"{DA.paths.checkpoints}/silver")
    .outputMode("complete")
    .trigger(availableNow=True)
    .table("device_counts")
    .awaitTermination() # This optional method blocks execution of the next cell until the incremental batch write has succeeded
)
```

## Loading Patterns and Best Practices
https://docs.databricks.com/ingestion/auto-loader/patterns.html
