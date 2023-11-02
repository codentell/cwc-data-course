+++
title = "04. PyMongo with Imported JSON Data 👩‍🎓👨‍🎓"
weight = 4
tags = ["mongo"] 
+++

# PyMongo with Imported JSON Data

The PetSitly marketing team is trying to get more organized. They have customer information stored in a bunch of different files, and that's making everyone feel stressed!

In this activity, you’ll help calm them down by first creating a Mongo database for them and then moving their customer list, which is a JSON file, into a collection within that database.

## Instructions

1. If you haven’t already started Mongo, start it. To do so on Windows, run `mongod`. To do so on macOS, run `brew services start mongodb/brew/mongodb-community`.

2. In the terminal, use `cd` to navigate to the `Resources` folder that contains the `customer_list.json` file.

3. Use the following command to import this file into a Mongo database:

    ```shell
    mongoimport --type json -d petsitly_marketing -c customer_list --drop --jsonArray customer_list.json
    ```

    **Hint:** For more information about importing JSON files into Mongo, refer to [mongoimport](https://docs.mongodb.com/database-tools/mongoimport/#mongoimport) in the MongoDB documentation.

4. Create an instance of MongoClient by using Port Number 27017.

5. List the database names to confirm that the `petsitly_marketing` database was created.

6. Assign the `petsitly_marketing` database to a variable.

7. List the names of the collections in the database.

    **Hint:** Be sure to use the name of the variable that you assigned your database to.

8. Use the `find_one` function to review a document in the `customer_list` collection of your database.

9. Assign the `customer_list` collection to a variable of your choice.

10. Use the `insert_one` function to insert the new customer into the database, and then run the query in the following cell to review this customer.

11. Create a query that will find all the customers who have turtles as pets.

## Bonus (Optional)

Try running queries to practice deleting entities from a Mongo database. To do so, complete the following steps:

1. Use the `delete_many` function to delete the customers that have hamsters. Then query the database to confirm that this worked.

2. Use `drop_collection` to delete the collection, and then use `list_collection_names` to confirm that this worked.

3. Use `drop_database` to delete your database. Then use `list_database_names` to confirm that this worked.



---

```python

# Create a Mongo Database
from pymongo import MongoClient
# Create an instance of MongoClient
mongo = MongoClient(port=27017)
# confirm that our new database was created
print(mongo.list_database_names())

# assign the petsitly_marketing database to a variable name
db = mongo['petsitly_marketing']
# List the names of the collections in the database. 
# Be sure to use the variable name you assigned to your database to do this.
print(db.list_collection_names())

# review a document in the customer_list collection
print(db.customer_list.find_one())

# assign the collection to a variable
customer_list = db['customer_list']
# insert a new customer
new_customer = 
     
customer_list.insert_one(new_customer)

# Filter results by name (run this cell)
query = {'Customer_First': 'Data'}
results = customer_list.find(query)
for result in results:
    print(result)

# Find the number of customers with turtles
query = {'Pet_Type': 'turtle'}
results = customer_list.find(query)
for result in results:
    print(result)

Bonus: Try running queries to practice deleting entities from a Mongo database.
# Delete all the customers who have hamsters
query = {'Pet_Type': 'hamster'}
customer_list.delete_many(query)
results = customer_list.find(query)
for result in results:
    print(result)
# Delete a collection
db.drop_collection
db.list_collection_names()

# Delete the database
mongo.drop_database

mongo.list_database_names()

 
```
