+++
title = "04. CRUD 👩‍🎓👨‍🎓"
weight = 4
tags = ["sql"] 
+++

# CRUD Database

In this activity, you and a partner will practice CRUD operations with a new SQLite database.

## Instructions

* Within a Python file, create a new SQLAlchemy class called `Travel` to hold the following values:

    * `__tablename__`: This should be "travel_destinations"

    * `id`: The primary key for the table, which is an integer and automatically increments

    * `city`: A string of the name of the city

    * `country`: A string of the name of the country

    * `distance`: A double that explains the distance between the city you live in and the city in this row

    * `budget`: A double that explains how much it would cost to travel to this destination

    * `visited`: A boolean that explains if you have been to this destination or not

    * Create a connection and a session before adding a few items into the SQLite database.

* Update the values within at least two of the rows added to the table.

* Delete the row with the shortest distance.

* Print out all of the data within the database.

## Bonus

Use a SQLAlchemy function to identify the item with the lowest id value, and change its budget to $2,500.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Import SQL Alchemy
from sqlalchemy import create_engine

# Import and establish Base for which classes will be constructed 
from sqlalchemy.ext.declarative import declarative_base
Base = declarative_base()

# Import modules to declare columns and column data types
from sqlalchemy import Column, Integer, String, Float, Boolean
# Create the Travel class
class Travel(Base):
    __tablename__ = 'travel_destinations'
    id = Column(Integer, primary_key=True)
    city = Column(String(255))
    country = Column(String(255))
    distance = Column(Float)
    budget = Column(Float)
    visited = Column(Boolean)
# Create a connection to a SQLite database
engine = create_engine('sqlite:///travel.db')
# Create the travel_destinations table within the database
Base.metadata.create_all(engine)
# To push the objects made and query the server we use a Session object
from sqlalchemy.orm import Session
session = Session(bind=engine)
# Create some instances of the Travel class
destination_one = Travel(city="Santa Fe", country="United States", distance=1134.3, budget=500, visited=False)
destination_two = Travel(city="Kyoto", country="Japan", distance=5341, budget=2000, visited=True)
destination_three = Travel(city="Accra", country="Ghana", distance=7670, budget=5000, visited=False)
# Add these objects to the session
session.add(destination_one)
session.add(destination_two)
session.add(destination_three)
# Commit the objects to the database
session.commit()
# Update two rows of data
update_one = session.query(Travel).filter(Travel.id == 1).first()
update_one.visited = True
update_two = session.query(Travel).filter(Travel.id == 2).first()
update_two.budget = 3000.25
# Commit the updates to the database
session.commit()
# Delete the row with the shortest distance
travel_short = session.query(Travel).order_by(Travel.distance).first()
session.delete(travel_short)
# Commit the delete to the database
session.commit()
# Collect all of the destinations and print their information
destinations = session.query(Travel)
for destination in destinations:
    print("-"*12)
    print(f"id: {destination.id}")
    print(f"city: {destination.city}")
    print(f"country: {destination.country}")
    print(f"distance: {destination.distance}")
    print(f"budget: {destination.budget}")
    print(f"visited: {destination.visited}")


# Close the session
session.close()
 
# BONUS
lowest_id = session.query(Travel).order_by(Travel.id).first()
print(lowest_id.id)

print(lowest_id.budget)

lowest_id.budget = 2500
print(lowest_id.budget)

session.commit()
destinations = session.query(Travel)
for destination in destinations:
    print("-"*12)
    print(f"id: {destination.id}")
    print(f"city: {destination.city}")
    print(f"country: {destination.country}")
    print(f"distance: {destination.distance}")
    print(f"budget: {destination.budget}")
    print(f"visited: {destination.visited}")

session.close()
 
```
{{% /expand%}}