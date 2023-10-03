+++
title = "02. Dates 👩‍🏫🧑‍🏫"
weight = 2
tags = ["sql"] 
+++


```python
# Setup
# Python SQL toolkit and Object Relational Mapper
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine, text, inspect, func
engine = create_engine("sqlite:///../Resources/dow.sqlite", echo=False)

# Explore Database
inspector = inspect(engine)
inspector.get_table_names()

# Get a list of column names and types
columns = inspector.get_columns('dow')
for c in columns:
    print(c['name'], c["type"])
# columns

engine.execute(text('SELECT * FROM dow LIMIT 5')).fetchall()

# Reflect and query dates
# Reflect Database into ORM class
Base = automap_base()
Base.prepare(autoload_with=engine)
Dow = Base.classes.dow
session = Session(engine)
# Total dates
session.query(func.count(Dow.date)).all()

# Earliest Date
session.query(Dow.date).order_by(Dow.date).first()

# Latest Date
session.query(Dow.date).order_by(Dow.date.desc()).first()

# Find all of the dates great than `2011-03-01`
session.query(Dow.date).\
    filter(Dow.date > '2011-03-01').\
    order_by(Dow.date).all()

# Important Note! Sqlite does not support a date column type, but SQLAlchemy will allow you to work with dates in the iso format. sqlite dates
# Quick Review of DateTime
import datetime as dt
# Print a date object and a datetime object 
print(dt.date.today())
print(dt.date(2017, 1 ,31))

# Calculate a time difference 1 week ago from today
week_ago = dt.date.today() - dt.timedelta(days=7)
week_ago

# Query for the Dow closing price for `CSCO` 1 week before `2011-04-08` using the datetime library
query_date = dt.date(2011, 4, 8) - dt.timedelta(days=7)
print("Query Date: ", query_date)

session.query(Dow.date, Dow.close_price).\
    filter(Dow.stock == 'CSCO').\
    filter(Dow.date == query_date).all()

# Parse out just the day from the datetime object
dt.date.today().strftime("%d")

# Query for all dates matching the 
# following date string in the format `%d`
date_str = "14"
session.query(Dow.date).\
    filter(func.strftime("%d", Dow.date) == date_str).all()

```