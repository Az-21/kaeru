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
df_path: str = generate_lakehouse_path("sf_Opportunity")
column_mapping: dict[str, str] = {
  "SomeColumn": "SomeColumn",
  "SomeOther__c": "SomeOtherColumn",
}

df: DataFrame = (
  spark.read.format("delta")
  .load(df_path)
  .select(*column_mapping.keys())
  .select(*[F.col(old_name).alias(new_name) for old_name, new_name in column_mapping.items()])
)
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
