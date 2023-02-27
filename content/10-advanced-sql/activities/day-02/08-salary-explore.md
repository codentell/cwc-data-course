+++
title = "08. Salary Explore 👩‍🎓👨‍🎓"
weight = 8
tags = ["sql"] 
+++

# Salary Exploration

For this activity, you will create an inspector and search through a SQLite database of San Francisco salaries.

## Instructions

Using the attached SQLite file, use an inspector to collect the following information:

* The names of all of the tables within the database

* The column names and data types for the `salaries` table

## References

DataSF. (2022). OpenData. Employee Compensation, City Management and Ethics. Data provided by SF Controller's Office. [https://data.sfgov.org](https://data.sfgov.org/City-Management-and-Ethics/Employee-Compensation/88g8-5mnd).

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Import SQLAlchemy `automap` and other dependencies
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine, inspect
# Create the connection engine
engine = create_engine("sqlite:///../Resources/employee_compensation.sqlite")
# Create the inspector and connect it to the engine
inspector = inspect(engine)
# Collect the names of tables within the database
inspector.get_table_names()

# Using the inspector to print the column names within the 'Salaries' table and its types
columns = inspector.get_columns('Salaries')
for column in columns:
    print(column["name"], column["type"])
```
{{% /expand%}}

