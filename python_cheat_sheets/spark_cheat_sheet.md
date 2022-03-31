## PySpark cheat sheet**:<br>

**What is a Spark**:
- Cluster Computing platform where data is stored RDD format
    - RDD - Resilient Distributed Datasheet 
    - An Immutable distributed collection of data which is partitioned across machines in a cluster
 

**Why a SparkSession**:
- To create dataframes from csv, parquet files
- To execute table operations using SQL queries 

- How to initialize a SparkSession:
```python
from pypsark.sql import SparkSession

spark = SparkSession.builder\
      .appName("Python Spark SQL basic example")\
      .config("spark.some.config.option", "some-value")\
      .getOrCreate()
```

- Creating DataFrames
    - From RDDs
    
    ```python
    
    from pyspark.sql.types import Row
    
    # infer schema
    sc = spark.sparkContext
    lines = sc.textFile("sometextfile.txt")
    parts = lines.map(lambda l: l.split(","))
    people = parts.map(lambda r: Row(name=r[0], int(r[1])))
    peopledf = spark.createDataFrame(people)
    
    
    ```
    

Source: <br>
- [Datacamp](http://datacamp-community-prod.s3.amazonaws.com/02213cb4-b391-4516-adcd-57243ced8eed)
- [IntelliPaat](https://intellipaat.com/mediaFiles/2019/03/spark-and-rdd-cheat-sheet-1.png)
