+++
title = "02. Ice Cream Connection 👩‍🎓👨‍🎓"
weight = 2
tags = ["advanced sql"] 
+++

# Ice Cream Connection

In this activity, you will create, connect to, and insert data into a new database by using SQLAlchemy.

## Instructions

* Use the database path to create a SQLite engine.

* Use the engine to select all of the rows and columns from the table `icecreamstore`.

* Create a new query that finds the ice cream flavors that cost more than `2.0`.

---

## Reference

Mockaroo, LLC. (2021). Realistic Data Generator. [https://www.mockaroo.com/](https://www.mockaroo.com/)

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# SQL Alchemy
from sqlalchemy import create_engine

database_path = "./Resources/icecreamstore.sqlite"
# Create Engine
engine = create_engine(f"sqlite:///{database_path}")
# Query All Records in the the Database
data = engine.execute("SELECT * FROM icecreamstore;")
for record in data:
    print(record)

# Query Using a Filter
data = engine.execute("SELECT * FROM icecreamstore WHERE Price > 2.0;")
for record in data:
    print(record)
```
{{% /expand%}}