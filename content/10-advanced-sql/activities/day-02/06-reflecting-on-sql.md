+++
title = "06. Reflecting on SQL 👩‍🎓👨‍🎓"
weight = 6
tags = ["sql"] 
+++

# Reflecting on SQL

For this activity, you’ll test your ability to reflect existing databases using SQLAlchemy and a SQLite table focused on demographic data.

## Instructions

* Create an engine using the `demographics.sqlite` database file.

* Declare a `Base` using `automap_base()`, and use this new `Base` class to reflect the database's tables.

* Assign the demographics table/class to a variable called `Demographics`.

* Create a session, and use this session to query the `Demographics` table and display the first five locations.

## Bonus

Query and print the number of unique locations in the table.

## Hint

For the bonus, explore how to count and group operations in SQLAlchemy.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Python SQL toolkit and Object Relational Mapper
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine
# Create engine using the `demographics.sqlite` database file
engine = create_engine("sqlite:///../Resources/demographics.sqlite")
# Declare a Base using `automap_base()`
Base = automap_base()
# Use the Base class to reflect the database tables
Base.prepare(autoload_with=engine)
# Print all of the classes mapped to the Base
Base.classes.keys()

# Assign the demographics class to a variable called `Demographics`
Demographics = Base.classes.demographics
# Create a session
session = Session(engine)
# Use the session to query Demographics table and display the first 5 locations
for row in session.query(Demographics, Demographics.location).limit(5).all():
    print(row)

# BONUS: Query and print the number of unique Locations
# Hints: Look into counting and grouping operations in SQLAlchemy
locations = session.query(Demographics).group_by(Demographics.location).count()
print(locations)

```
{{% /expand%}}