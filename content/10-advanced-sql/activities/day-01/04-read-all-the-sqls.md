+++
title = "04. Read All the SQLs 👩‍🎓👨‍🎓"
weight = 4
tags = ["advanced sql"] 
+++

In this activity, you will query an external server by using Pandas and SQLAlchemy to create new DataFrames on U.S. Census data.

## Instructions

* Create an engine to connect to the Census database.

* Query all the data from the `Census_Data` table, and load it into Pandas.

* Create an engine to connect to the zip database.

* Query all the data from the `Zip_Census` table, and load it in Pandas.

* Show the `.head()` of your newly imported data.

## Bonus

Use Pandas’s `merge` to combine the two DataFrames.

---

## Reference

[US Census Data](https://www.census.gov/developers/).

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Pandas
import pandas as pd

# SQL Alchemy
from sqlalchemy import create_engine

# Create Engine for census data
census_database_path = "./Resources/Census_Data.sqlite"
engine = create_engine(f"sqlite:///{census_database_path}")
conn = engine.connect()

# Query All Records in the the Census Table
census_data = pd.read_sql("SELECT * FROM Census_Data", conn)

# Create Engine for zip data
zip_database_path = "./Resources/zip_census.sqlite"
engine = create_engine(f"sqlite:///{zip_database_path}")
conn = engine.connect()

# Query All Records in the Zip Table
zip_data = pd.read_sql("SELECT * FROM Zip_Census", conn)
census_data.head()

# Merge the columns
combined_data = pd.merge(census_data, zip_data, on="CityState", how="inner")

# Combined Data
combined_data.head()
```
{{% /expand%}}