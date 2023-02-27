+++
title = "02. Sunny Hours  👩‍🎓👨‍🎓"
weight = 2
tags = ["sql"] 
+++

# Sunny Hours

For this activity, you will create a Python script that can search through the provided SQL file of hours of sunshine in various cities in the world.

## Instructions

* Use [sunshine.sqlite](Resources/sunshine.sqlite) as your data source.

* Within a Python script, create a `Sunshine` class to read in all of the columns of the database. Consult the SQL schema of the `sunshine` table when creating your class. Note that the REAL data type refers to floating point numbers (decimals).

```sql
CREATE TABLE sunshine (
    id INTEGER PRIMARY KEY,
    Country TEXT,
    City TEXT,
    Jan REAL,
    Apr REAL,
    Jul REAL,
    Oct REAL,
    Year REAL
);
```

* Using SQLAlchemy, perform the following queries:

  * Print all columns of each row.

  * Find the total number of cities in the database.

  * Find the total number of observed cities in Canada.

  * Find the number of cities whose yearly sunshine equals or exceeds 3700 hours.

  * Print the city name, country, and yearly sunny hours of all cities whose yearly sunshine equals or exceeds 3700 hours.

  * Find the number of cities whose January sunshine equals or exceeds 300 hours.

  * Print the city name, country, January sunny hours, and yearly sunny hours of all cities that have 300 or greater hours of sunshine in January.

  * Find the number of cities in the United States whose yearly hours of sunshine are 2500 or fewer.

  * Print the city name and yearly sunny hours of cities in the United States that receive 2500 or fewer hours of sunshine per year.

## References

Kaggle (2022). Sunshine Duration by City. Data provided by Kaggle. [https://www.kaggle.com/datasets/prasertk/sunshine-duration-by-city/metadata](https://www.kaggle.com/datasets/prasertk/sunshine-duration-by-city/metadata)

Wikipedia (2022). List of cities by sunshine duration. Data provided by Wikipedia. [https://en.wikipedia.org/wiki/List_of_cities_by_sunshine_duration](https://en.wikipedia.org/wiki/List_of_cities_by_sunshine_duration)

—


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
from sqlalchemy.ext.declarative import declarative_base
from sqlalchemy import Column, String, Float, Integer
from sqlalchemy import create_engine
from sqlalchemy.orm import Session
Base = declarative_base()
database_path = "../Resources/sunshine.sqlite"
engine = create_engine(f"sqlite:///{database_path}")
Base.metadata.create_all(engine)
session = Session(bind=engine)
session
<sqlalchemy.orm.session.Session at 0x7fc80079c790>
# Create your Sunshine class
class Sunshine(Base):
    __tablename__ = 'sunshine'
    id = Column(Integer, primary_key=True)
    Country = Column(String)
    City = Column(String)
    Jan = Column(Float)
    Apr = Column(Float)
    Jul = Column(Float)
    Oct = Column(Float)
    Year = Column(Float)
sunshine = session.query(Sunshine)
# Print all observations
for city in sunshine:
    print(f"{city.id}, {city.Country}, {city.City}, {city.Jan}, {city.Apr}, {city.Jul}, {city.Oct}, {city.Year}")


# Find the total number of cities in the database
total_count = session.query(Sunshine).distinct().count()
print(total_count)

# Find the total number of observed cities in Canada
canadian_cities = session.query(Sunshine).\
    filter_by(Country='Canada').count()
print(canadian_cities)

# Find the number of cities whose yearly sunshine equals or exceeds 3700 hours
over_3700_hours_count = session.query(Sunshine).\
    filter(Sunshine.Year >= 3700).count()
print(over_3700_hours_count)

# Print the cities that have a total yearly sunshine of 3700 hours or greater
over_3700_hours = session.query(Sunshine).\
    filter(Sunshine.Year >= 3700)
for city in over_3700_hours:
    print(city.Country, city.City, city.Year)


# Find the number of cities whose January sunshine equals or exceeds 300 hours
sunny_january_count = session.query(Sunshine).\
    filter(Sunshine.Jan >= 300).count()
print(sunny_january_count)

# Find cities whose January sunshine equals or exceeds 300 hours
sunny_january_cities = session.query(Sunshine).\
    filter(Sunshine.Jan >= 300)
for city in sunny_january_cities:
    print(city.Country, city.City, city.Jan, city.Year)

# Find cities in the United States whose yearly sunshine is 2500 or fewer

overcast_cities_count = session.query(Sunshine).\
    filter(Sunshine.Country == 'United States').\
    filter(Sunshine.Year <= 2500).count()

print(overcast_cities_count)

overcast_cities = session.query(Sunshine).\
    filter(Sunshine.Country == 'United States').\
    filter(Sunshine.Year <= 2500)
for city in overcast_cities:
    print(city.City, city.Year)

session.close()
```
{{% /expand%}}