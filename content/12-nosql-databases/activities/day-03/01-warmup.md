+++
title = "01. Warmup 👩‍🎓👨‍🎓"
weight = 1
tags = ["mongo"] 
+++

# Warm-Up Activity

In this activity, you will import the data you will be using for the remainder of this class, and run a few searches to explore the collection.

## Instructions

* In your Terminal, navigate to the folder where your [artifacts.json](Resources/artifacts.json) file is stored.

* Import the dataset with `mongoimport --type json -d met -c artifacts --drop --jsonArray artifacts.json`

* In Jupyter Notebook, open [mongodb_warm_up.ipynb](Unsolved/mongodb_warm_up.ipynb) and use the following instructions to check that you created the database correctly, and set your variables:

    * Import MongoClient from PyMongo and pprint from pprint.

    * Create an instance of MongoClient.

    * Confirm that you imported the data correctly by listing your database names.

    * Assign the met database to a variable name.

    * Review the collections in your new database.

    * Use `pprint` and `find_one()` to review a document in the artifacts collection.

    * Assign the artifacts collection to a variable.

* Review the code we have explored previously to find:

    * How many documents have the `culture` "Nayarit" using `count_documents()`

    * How many documents have a height of at least 40cm using `$gte`

* Pretty print the results of a query that:

    * Finds the documents where:

        * The culture is "Nayarit" or "Central American Isthmus" and

        * The height is less than or equal to 40cm

    * Returns only the following fields: "title", "department", "culture", "measurements", and "objectURL"

    * Sorts alphabetically by "title"

    * Limits the results to 5


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Before running any of the following code, make sure you import the dataset with mongoimport --type json -d met -c artifacts --drop --jsonArray artifacts.json

# Import dependencies
from pymongo import MongoClient
from pprint import pprint
# Create an instance of MongoClient
mongo = MongoClient(port=27017)
# confirm that our new database was created
print(mongo.list_database_names())
['admin', 'classDB', 'config', 'local', 'met']
# assign the met database to a variable name
db = mongo['met']
# review the collections in our new database
print(db.list_collection_names())

# review a document in the artifacts collection
pprint(db.artifacts.find_one())


# assign the collection to a variable
artifacts = db['artifacts']
Explore the Collection
# Find how many documents have culture as "Nayarit"
Nayarit_documents = artifacts.count_documents({'culture': 'Nayarit'})

# Find how many documents have a height greater than or equal to 40cm
height_gte_40_documents = artifacts.count_documents({'measurements.elementMeasurements.Height': {'$gte': 40}})
height_gte_40_documents

# Create a query that:
# Finds the documents where the culture is "Nayarit" or "Central American Isthmus" and
#     the height is less than or equal to 40cm
# Returns only the following fields: "title", "department", "culture", "measurements", and "objectURL"
# Sorts alphabetically by "title"
# Limits the results to 5
query = {'culture': {'$in': ["Nayarit", "Central American Isthmus"]},
         'measurements.elementMeasurements.Height': {'$lte': 40}}
fields = {"title": 1, "department": 1, "culture": 1, "measurements": 1, "objectURL": 1}
sort = [("title", 1)]
limit = 5

# Cast the results as a list and save the results to a variable
results = list(artifacts.find(query, fields).sort(sort).limit(limit))

# Pretty print the results
pprint(results)

# Data Source: The Metropolitan Museum of Art (2022). The Metropolitan Museum of Art Collection API https://metmuseum.github.io/. Licensed under the Creative Commons 0 License.
# Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".

 
{{% /expand%}}
