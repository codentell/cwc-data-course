+++
title = "01. Joins 👩‍🏫🧑‍🏫"
weight = 1
tags = ["sql"] 
+++

```python
# Python SQL toolkit and Object Relational Mapper
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine, inspect

# Create Database Connection
engine = create_engine("sqlite:///../Resources/mammal_masses.sqlite", echo=False)

# Reflect Database into ORM classes
Base = automap_base()
Base.prepare(autoload_with=engine)
Base.classes.keys()

# Map Europe class
EA = Base.classes.ea

# Map North American class
NA = Base.classes.na

# create a session
session = Session(engine)

# Filtering Review
# Filters are the "WHERE" clause for your select statement.

# Filter North American mammals whose genus is "Antilocapra"
# Query, loop over and print out animals.
mammals = session.query(NA).filter(NA.genus == 'Antilocapra').all()
for mammal in mammals:
    print(f"Family: {mammal.family}, Genus: {mammal.genus}")

# Joins
# A SQL join combines columns from one or more tables in a relational database.

# It creates a set that can be saved as a table or used as it is.

# A JOIN is a means for combining columns from one (self-table) or more tables by using values common to each.

# Get the table names using `inspect()`.
inspector = inspect(engine)
inspector.get_table_names()

# Get a list of column names and types
columns = inspector.get_columns('ea')
for c in columns:
    print(c['name'], c["type"])

# Join all the order names for the EA and NA classes. 
# This returns a warning so the query should be filtered on a common order name.
session.query(EA.order, NA.order).limit(200).all()


# Filter the the join query. 
same_order = session.query(EA, NA).filter(EA.order == NA.order).limit(10).all()

for record in same_order:
    (ea, na) = record
    print(ea.order, ea.family, ea.genus, ea.species)
    print()
    print(na.order, na.family, na.genus, na.species)


# Return all animals from EA and NA belonging to the same order.
# This JOINs the data in the two tables together into a single dataset (here in the form of a tuple).
# Note: We are going to limit the results to 10 for printing
sel = [EA.family, EA.genus, EA.species, NA.family, NA.genus, NA.species]
same_order = session.query(*sel).filter(EA.order == NA.order).limit(10).all()

for record in same_order:
    (ea_fam, ea_gen, ea_spec, na_fam, na_gen, na_spec) = record
    print(
        f"The European animal '{ea_fam} {ea_gen} {ea_spec}'"
        f"belongs to the same order as the North American animal '{na_fam} {na_gen} {na_spec}'.")
```