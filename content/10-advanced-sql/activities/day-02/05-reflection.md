+++
title = "05. Reflection 👩‍🏫🧑‍🏫"
weight = 5
tags = ["sql"] 
+++

```python

# Python SQL toolkit and Object Relational Mapper
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine

# Create engine using the `demographics.sqlite` database file
engine = create_engine("sqlite:///./resources/dow.sqlite")
# Declare a Base using `automap_base()`
Base = automap_base()
# Use the Base class to reflect the database tables
Base.prepare(autoload_with=engine)
# Print all of the classes mapped to the Base
Base.classes.keys()

# Assign the dow class to a variable called `Dow`
Dow = Base.classes.dow
# Create a session
session = Session(engine)
# Display the row's columns and data in dictionary format
first_row = session.query(Dow).first()
first_row.__dict__


# Use the session to query Dow table and display the first 5 trade volumes
for row in session.query(Dow.stock, Dow.volume).limit(15).all():
    print(row)

```