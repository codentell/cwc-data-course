+++
title = "08. Find Pets 👩‍🎓👨‍🎓"
weight = 8
tags = ["mongo"] 
+++

# Find Pets

In this activity, you will revisit the data from Petsitly Marketing and practice using comparison operators in MongoDB with PyMongo.

## Instructions

* Navigate to your `Resources` folder in your Terminal and import the Petsitly data again using the following command:

    ```shell
    mongoimport --type json -d petsitly_marketing -c customer_list --drop --jsonArray customer_list.json
    ```

* Use [find_pets.ipynb](Unsolved/find_pets.ipynb) to complete this activity in Jupyter Notebook.

* Create a query that finds the customers who had over 50 visits in 2021 and pretty print the first two results.

* Create a query that finds the customers who spent $250 or less in 2021 and pretty print the first two results.

* Create a query that finds the customer(s) who live in an apartment with "Suite" in the address and pretty print the first three results.

* Create a query that finds the customers who have turtles or fish and pretty print the first three results.

## Hint

* The `$regex` operator is used to match partial strings.

* For the other comparison operators, consult the MongoDB documentation on [comparison operators](https://www.mongodb.com/docs/manual/reference/operator/query-comparison/).


---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Import dependencies
from pymongo import MongoClient
from pprint import pprint
# Create an instance of MongoClient
mongo = MongoClient(port=27017)
# confirm that the "petsitly_marketing" database is in MongoDB
print(mongo.list_database_names())

# assign the database to a variable name
db = mongo['petsitly_marketing']
# review the collections in our new database
print(db.list_collection_names())
['customer_list']
# assign the collection to a variable
customers = db['customer_list']
# Create a query that finds the customers who had over 50 visits in 2021
query = {'2021_Visits': {'$gt': 50}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the first two results
for i in range(2):
    pprint(results[i])

# Create a query that finds the customers who spent $250 or less in 2021
query = {'2021_Total_Spend': {'$lt': 250}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the first two results
for i in range(2):
    pprint(results[i])


# Create a query that finds the customer(s) who live in an apartment with "Suite" in the address
query = {'Address': {'$regex': "Suite"}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the first three results
for i in range(3):
    pprint(results[i])
 
# Create a query that finds the customers who have turtles or fish
query = {'Pet_Type': {'$in': ["turtle", "fish"]}}

# Capture the results to a variable
results = customers.find(query)

# Pretty print the first three results
for i in range(3):
    pprint(results[i])

 
```
{{% /expand%}}