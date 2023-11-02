+++
title = "09. Sort and Limit 👩‍🏫🧑‍🏫"
weight = 9
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
['admin', 'autosaurus', 'classDB', 'config', 'epa', 'local', 'petsitly_marketing']
# assign the database to a variable name
db = mongo['autosaurus']
# review the collections in our new database
print(db.list_collection_names())
['customers', 'mechanics']
# assign each collection to a variable
customers = db['customers']
mechanics = db['mechanics']
# Create a query that sorts in ascending order by last_service
query = {}
sort = [('last_service', 1)]

# Capture the results to a variable
results = customers.find(query).sort(sort)

# Pretty print the first five results
for i in range(5):
    pprint(results[i])


# Create a query that sorts in ascending order by last_service and limits the results to the first 5
query = {}
sort = [('last_service', 1)]
limit = 5

# Pretty print the results
pprint(list(customers.find(query).sort(sort).limit(limit)))

# Create a query that:
# finds customers with a "Nissan" or "Hyundai"
# sorts in descending order by car_year
# limits the results to the first 5
query = {'car_make': {'$in': ["Nissan", "Hyundai"]}}
sort = [('car_year', -1)]
limit = 5

# Pretty print the results
pprint(list(customers.find(query).sort(sort).limit(limit)))

# Create a query that:
# finds customers with a "Nissan" or "Hyundai"
# sorts in descending order by car_year, then ascending order by last_service
# limits the results to the first 5
query = {'car_make': {'$in': ["Nissan", "Hyundai"]}}
sort = [('car_year', -1), ('last_service', 1)]
limit = 5

# Pretty print the results
pprint(list(customers.find(query).sort(sort).limit(limit)))

 

```