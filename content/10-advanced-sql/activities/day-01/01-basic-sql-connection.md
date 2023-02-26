+++
title = "01. Basic SQL Connection 👩‍🏫🧑‍🏫"
weight = 1
tags = ["advanced sql"] 
+++

```python

# SQLAlchemy
from sqlalchemy import create_engine

# Path to sqlite
database_path = "./resources/Census_Data.sqlite"

# Create an engine that can talk to the database
engine = create_engine(f"sqlite:///{database_path}")

# Query All Records in the the Database
data = engine.execute("SELECT * FROM Census_Data")

for record in data:
    print(record)

```