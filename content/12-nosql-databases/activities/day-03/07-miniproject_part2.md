+++
title = "07. MongoDB Mini-Project Part 2: Aggregation and Analysis 👩‍🎓👨‍🎓"
weight = 7
tags = ["mongo"] 
+++

# MongoDB Mini-Project Part 2: Aggregation and Analysis

For Part 2 of the mini-project, you will practice building a more complex query and another aggregation pipeline, then normalizing your resulting DataFrame.

## Instructions

* Run the first two blocks of code to import your dependencies, create an instance of MongoClient, and assign the database and collection to variables.

* Write a query that:

    * Uses `find()` to find documents about artifacts that come from the "Maya" culture and returns the following fields: `accessionNumber`, `accessionYear`, `classification`, `country`, `department`, `measurements.elementMeasurements.Height`, `measurements.elementMeasurements.Width`, `measurements.elementMeasurements.Depth`, `medium`, `title`,`objectURL`.

    * Uses `sort()` to sort by the artifact's height.

    * Uses `limit()` to limit the number of results to 5.

* Convert the results to a Pandas DataFrame and then display the DataFrame.

* Build an aggregation pipeline that:

    * Matches:

        * Artifacts that have a width greater than or equal to 10cm and less than 50cm

        * Artifacts that have a height greater than or equal to 20cm and less than 60cm

        * Artifacts that have "Sculpture" as part of their classification

    * Counts the artifacts and groups by: classification and then culture

        **Hint:** Set `_id` to a list or a dictionary of the fields that are being grouped on. If you use a dictionary, you will also need to assign names (or keys) for the fields you are selecting.

    * Sorts by count in descending order

* Pretty print the first 10 results of the aggregation pipeline.

* Write code that will extract the fields from `_id` from the aggregation pipeline to create a Pandas DataFrame that will include the following columns: classification, culture, number of artifacts. If necessary, rename and reorder the columns to match.

    > **Note:** There are multiple ways to do this, but the easiest way is to use `pd.json_normalize()`. If you need help using this new Pandas method, [check out the documentation](https://pandas.pydata.org/docs/reference/api/pandas.json_normalize.html).

## Reference

[The Metropolitan Museum of Art](https://www.metmuseum.org/) (2022). The Metropolitan Museum of Art Collection API https://metmuseum.github.io/. Licensed under the [Creative Commons 0 License](https://creativecommons.org/publicdomain/zero/1.0/)<br />
Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".

---


```python

# Import dependencies
from pymongo import MongoClient
from pprint import pprint
import pandas as pd
# Create an instance of MongoClient
mongo = MongoClient(port=27017)

# assign the met database to a variable name
db = mongo['met']

# assign the collection to a variable
artifacts = db['artifacts']
# Write a query that:

# Uses find() to find documents about artifacts that come from the "Maya" culture and returns the following fields: accessionNumber, accessionYear, classification, country, department, measurements.elementMeasurements.Height, measurements.elementMeasurements.Width, measurements.elementMeasurements.Depth, medium, title,objectURL.

# Uses sort() to sort by the artifact's height.

# Uses limit() to limit the number of results to 5.

# Query
query = {'culture': "Maya"}
fields = {'accessionNumber': 1, 'accessionYear': 1, 'classification': 1, 'country': 1, 
          'department': 1, 'measurements.elementMeasurements.Height': 1, 
          'measurements.elementMeasurements.Width': 1, 'measurements.elementMeasurements.Depth': 1, 
          'medium': 1, 'title': 1, 'objectURL': 1}
sort = [('measurements.elementMeasurements.Height', -1)]
limit = 5

# Cast the results as a list and save them to a variable
results = list(artifacts.find(query, fields).sort(sort).limit(limit))

# Pretty print the results
pprint(results)
                                            
# Convert results to DataFrame
top_maya_artifacts_by_height_df = pd.DataFrame(results)
top_maya_artifacts_by_height_df

# Build the aggregation pipeline
# Write a match query to find only the documents about artifacts that
# have a classification where "Sculpture" is contained the value, and
# have a width greater than or equal to 10cm and less than 50cm, and
# have a height greater than or equal to 20cm and less than 60cm.
match_query = {'$match': {'classification': {'$regex': "Sculpture"},
                          'measurements.elementMeasurements.Width': {'$gte': 10, '$lt': 50},
                          'measurements.elementMeasurements.Height': {'$gte': 20, '$lt': 60}
                         }
              }

# Write an aggregation query that counts the number of documents, grouped by "classification" and "culture"
group_query = {'$group': {'_id': {"classification": "$classification",
                                  "culture": "$culture"}, 
                          'count': { '$sum': 1 }
                         }
              }

# Create a dictionary that will allow the pipeline to sort by count in descending order
sort_values = {'$sort': { 'count': -1 }}

# Put the pipeline together
pipeline = [match_query, group_query, sort_values]
# Run the pipeline through the aggregate method, cast the results as a list, and save the results to a variable
results = list(artifacts.aggregate(pipeline))
# Print the number of rows in the result
print("Number of rows in result: ", len(results))
# Number of rows in result:  63
# Print the first 10 results
pprint(results[0:10])


# Extract the fields from the _id so they're in separate columns in a Pandas DataFrame
aggregated_df = pd.json_normalize(results)
aggregated_df.head()

# Rename the columns
aggregated_df = aggregated_df.rename(columns={"count": "number of artifacts",
                                              "_id.classification": "classification",
                                              "_id.culture": "culture"})
aggregated_df.head()

# Reorder the columns
aggregated_df = aggregated_df[

# Print the first 10 rows of the DataFrame
aggregated_df.head(10)

 
# Data Source: The Metropolitan Museum of Art (2022). The Metropolitan Museum of Art Collection API https://metmuseum.github.io/. Licensed under the Creative Commons 0 License.
# Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".
```