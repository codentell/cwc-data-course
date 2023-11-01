+++
title = "07.  👩‍🏫🧑‍🏫"
weight = 7
tags = ["mongo"] 
+++

```python

# Import dependencies
from pymongo import MongoClient
from pprint import pprint
# Create an instance of MongoClient
mongo = MongoClient(port=27017)
# confirm that the "autosaurus" database is in MongoDB
print(mongo.list_database_names())

# assign the database to a variable name
db = mongo['autosaurus']
# review the collections in our new database
print(db.list_collection_names())
['customers', 'mechanics']
# assign each collection to a variable
customers = db['customers']
mechanics = db['mechanics']
# Create a query that finds the customers who have cars from 2010 or later
query = {'car_year': {'$gte': 2010}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the first two results
for i in range(2):
    pprint(results[i])


# Create a query that finds the customers who have cars that were manufactured before 1990
query = {'car_year': {'$lt': 1990}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the first two results
for i in range(2):
    pprint(results[i])


# Create a query that finds the customer(s) who have "Nye" in their name
query = {'full_name': {'$regex': "Nye"}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the results
for result in results:
    pprint(result)

# To create a query that finds the customers who have cars that the mechanic "Dacey Cocom" can work on,
# first we must find the types of cars Dacey specializes in.
query = {'mechanic_name': "Dacey Cocom"}
fields = {'mechanic_name': 1, 'car_specialties': 1}

# Capture the results to a variable
results = list(mechanics.find(query, fields))

# Pretty print the results
for result in results:
    pprint(result)


# Save the 'car_specialties' to a variable
dacey_cars = results[0]

dacey_cars

# Create a query that finds the customers who have cars that the mechanic "Dacey Cocom" can work on
query = {'car_make': {'$in': dacey_cars}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the first two results
for i in range(2):
    pprint(results[i])

 

```