### Starter Template
```py
from pyspark.sql import SparkSession, Row, DataFrame, functions as F
from pyspark.errors import AnalysisException
spark = SparkSession.builder.appName("Name").getOrCreate()


DEBUG: bool = True
```

### Lakehouse Table
```py
def generate_lakehouse_path(table_name: str) -> str:
  return f"Tables/dbo/{table_name}"
```

### Table with Specific Columns
```py
column_mapping: dict[str, str] = {
  "SomeColumn": "SomeColumn",
  "SomeOther__c": "SomeOtherColumn",
}

df: DataFrame = (
  spark.read.format("delta")
  .load(generate_lakehouse_path("table_name"))
  .select(*column_mapping.keys())
  .select(*[F.col(old_name).alias(new_name) for old_name, new_name in column_mapping.items()])
)

if df.isEmpty():
  raise Exception("The table is being updated. Please try again later")

if DEBUG:
  display(df)
```

### Transform
```py
df: DataFrame = (
  df
  .filter((F.col("ColName") == "ValA") | (F.col("ColName") == "ValB"))
  .filter(F.col("BoolCol") == False)
  .drop("BoolCol", "Type")
  .withColumn("SomeCol", F.when(F.col("ColName").contains("Lock"), "Private").otherwise("Public"))
)
```

### Save
```py
output_path: str = generate_lakehouse_path("fabric_TableName")
aggregated_df.write.format("delta").mode("overwrite").save(output_path)
```
