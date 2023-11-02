+++
title = "06. MongoDB Mini-Project Part 1: Import Data from an API 👩‍🎓👨‍🎓"
weight = 6
tags = ["mongo"] 
+++

# MongoDB Mini-Project Part 1: Import Data from an API

In this activity, you will collect additional data from the Metropolitan Museum of Art API and update the database with the new data.

## Instructions

### Part 1: Connect to the Database

* Import your dependencies: MongoClient from pymongo, pprint from pprint, json, and requests.

* Create an instance of MongoClient.

* Assign the met database to a variable called `db`.

* Assign the artifacts collection to a variable called `artifacts`.

### Part 2: Collect the Data

You have been supplied with a list of ObjectIDs from the Met's API where the departmentId is 5 and the query string is "cave" (https://collectionapi.metmuseum.org/public/collection/v1/search?departmentId=5&q=cave).

* Run the code provided to extract the data from the Met's API about each of the artifacts in the `cave_ids` list.

### Part 3: Update the Database

Some of the artifacts collected are already in your database! Starting with one result, you will write code to check the database to see if an artifact is already in the collection. If it's not, you will add it to the database. Then, you will combine your code to loop through your results and only add the artifacts that are not yet in the collection.

Use the following instructions as a guide:

* Choose just one item from the returned data and set it to a variable called `item_to_add`.

    **Hint:** Use the `returned_data_list` and square bracket notation to select a single item from the list.

* Pretty print `item_to_add`.

* Using the `objectID` from `item_to_add`, write a query to check if the item already exists in the artifacts collection.

* Using the above query, write an `if` statement that checks if the result equals `None`.

* Inside your `if` statement:

    * Use `insert_one` to add `item_to_add` to the artifacts collection.

    * Print out the `objectID` when it is added to the collection.

* Combine the above steps to loop through the whole list of data contained in `returned_data_list` only adding to the collection when the artifact does not yet exist in the database. Follow these steps:

    * Loop through `returned_data_list`.

    * Save the data from the list item to the `item_to_add` variable.

    * Check if the artifact already exists in the collection.

    * Inside your `if` statement:

        * Use `insert_one` to add `item_to_add` to the artifacts collection.

        * Print out the `objectID` when it is added to the collection.

## Reference

[The Metropolitan Museum of Art](https://www.metmuseum.org/) (2022). The Metropolitan Museum of Art Collection API https://metmuseum.github.io/. Licensed under the [Creative Commons 0 License](https://creativecommons.org/publicdomain/zero/1.0/)<br />
Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Part 1: Connect to the Database
# Import dependencies
from pymongo import MongoClient
import json
import requests 
from pprint import pprint
# Create an instance of MongoClient
mongo = MongoClient(port=27017)
# assign the met database to a variable name
db = mongo['met']
# assign the collection to a variable
artifacts = db['artifacts']
# Part 2: Collect the Data
# Artifacts from department 5 and search string "cave"
# https://collectionapi.metmuseum.org/public/collection/v1/search?departmentId=5&q=cave
cave_ids = [313726,313724,312602,310364,

# Print the number of IDs
print(f'Number of IDs: {len(cave_ids)}')

# Initialize a list to store the returned documents
returned_data_list = []

# Create a loop to make API calls about each artifact we're interested in
for i in range(len(cave_ids)):
    # API URL
    url = "https://collectionapi.metmuseum.org/public/collection/v1/objects/" + str(cave_ids[i])
    
    # Make the API request
    response = requests.get(url)
    
    # Extract the json result
    extract_json = response.json()
    
    # Add the returned json to the end of the list
    returned_data_list.append(extract_json)

# Print the length of the results to ensure it matches the cave_ids list length
print(f'Length of returned collection artifacts: {len(returned_data_list)}')
Number of IDs: 38
# Length of returned collection artifacts: 38
# Now we have our list of additional artifacts we want to add to our database, but we need to check that these artifacts are not already in our collection before we add them

# Part 3: Update the Database
# Choose just one item from our returned data and set it to a variable
item_to_add = returned_data_list[1]

# Pretty print item_to_add
pprint(item_to_add)

# Check if objectID is already in collection
pprint(artifacts.find_one({"objectID":item_to_add['objectID']}))
None
# Check if objectID not found
if artifacts.find_one({"objectID":item_to_add["objectID"]}) == None:
    # Insert the new data into the collection
    artifacts.insert_one(item_to_add)
    
    # Print objectID when inserted
    print(f'Adding object with objectID: {item_to_add["objectID"]}')
Adding object with objectID: 313724
# Check that the new artifact was inserted
pprint(artifacts.find_one({"objectID":item_to_add['objectID']}))

# Combine the above steps to loop through the whole list of data contained in returned_data_list
# only adding to the collection when the artifact does not yet exist in the database

# Loop through returned_data_list
for item_to_add in returned_data_list:
    # Check if the artifact already exists in the collection
    if artifacts.find_one({"objectID":item_to_add["objectID"]}) == None:
        # Insert the new data into the collection
        artifacts.insert_one(item_to_add)
        
        
        # Print objectID when inserted
        print(f'Adding object with objectID: {item_to_add["objectID"]}')
              
    # Optional: Print a statement if the object is in the database. 
    else: print(f'Object is already in the database.')
```
{{% /expand%}}