#databricks #dataengineering 

[Databricks Certified Data Engineer Associate](Databricks%20Certified%20Data%20Engineer%20Associate.md)


AKA: Medallion Architecture, Delta Architecture 

Data is further validated and enriched as it is processed 

## Data Quality Medals

- **Bronze**: Raw. Little processing
	- Typically just a raw copy of ingested data
	- Replaces traditional data lake
	- Provides efficient storage and querying of full, unprocessed historical data
	
- **Silver**: More refined view. Filtered, cleansed, data types
	- Reduces data storage complexity, latency, and redundancy
	- Optimises ETL throughput and analytic query performance
	- Preserves grain of original data
	- Eliminates duplicate records
	- Production schema enforced
	- Data quality checks, corrupt data quarantined

- **Gold**: Ready for use/reporting. Aggregated
	- Powers ML applications, reporting, dashboards, ad hoc analytics
	- Refined views of data, typically with aggregations
	- Reduces strain on production systems
	- Optimises query performance for business-critical data


## Additional Topics & Resources

* [Table Streaming Reads and Writes](https://docs.databricks.com/delta/delta-streaming.html)
* [Structured Streaming Programming Guide](https://spark.apache.org/docs/latest/structured-streaming-programming-guide.html)
* [A Deep Dive into Structured Streaming](https://www.youtube.com/watch?v=rl8dIzTpxrI) by Tathagata Das. This is an excellent video describing how Structured Streaming works.
* [Lambda Architecture](https://databricks.com/glossary/lambda-architecture)
* [Data Warehouse Models](https://bennyaustin.wordpress.com/2010/05/02/kimball-and-inmon-dw-models)
* [Create a Kafka Source Stream](http://spark.apache.org/docs/latest/structured-streaming-kafka-integration.html)