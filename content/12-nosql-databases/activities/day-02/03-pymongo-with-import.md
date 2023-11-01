+++
title = "03.  Pymongo with Import 👩‍🏫🧑‍🏫"
weight = 3
tags = ["mongo"] 
+++

```python

# Introduction to Mongo
# Import the data first:

mongoimport --type csv -d petsitly_marketing -c customer_list --headerline --drop customer_database.csv

from pymongo import MongoClient
# Create an instance of MongoClient
mongo = MongoClient(port=27017)
# confirm that our new database was created
print(mongo.list_database_names())

# assign the database to a variable name
db = mongo['petsitly_marketing']
# review the collections in our new database
print(db.list_collection_names())

# review a document in the customer_list collection
print(db.customer_list.find_one())

# assign the collection to a variable
customer_list = db['customer_list']
# insert a new customer
new_customer = {'_id':3, 'Customer_First': 'Data', 'Customer_Last': 'Viz', 
                'Address': '55882 Valley Fields Dr', 'Email': 'dataviz@bootcamp.edu', 
                '2021_Visits': 75, '2021_Total_Spend': 2017.75, 'Pet_Type': 'cat'}
customer_list.insert_one(new_customer)

# Filter results by name
query = {'Customer_First': 'Data'}
results = customer_list.find(query)
for result in results:
    print(result)

# Find the number of customers with hamsters
query = {'Pet_Type': 'hamster'}
results = customer_list.find(query)
for result in results:
    print(result)


# Delete all the customers who have hamsters
customer_list.delete_many(query)
results = customer_list.find(query)
for result in results:
    print(result)
# Delete a collection
db.drop_collection('customer_list')
db.list_collection_names()

# Delete the database
mongo.drop_database('petsitly_marketing')
mongo.list_database_names()

 

```