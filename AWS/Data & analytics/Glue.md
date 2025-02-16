Glue is a serverless ETL service (extract transform load) - it prepares and transforms data for analytics - doesnt store it - it "glues" data services together.

One of the things you'd use it for is to transform data to the parquet format. This is a columnar data format in binary. Which looks like: 
```
data = {
	"id": [1, 2, 3],
	"name": ["Alice", "Bob", "Charlie"],
	"age": [25, 30, 35],
	"salary": [50000, 60000, 70000] 
}
```

**You can use Glue to create a catalog of datasets**
![[Glue.png]]

**5 concepts to know about**
- Glue job bookmarks: prevent reprocessing old data
- Glue Elastic views: combine and replicate data across many data stores using SQL
- Glue databrew - clean and normalize data with a prebuild transformation
- Glue Studio - GUI to create ETL jobs
- Glue streaming ETL