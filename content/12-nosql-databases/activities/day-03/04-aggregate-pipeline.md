+++
title = "04. Aggregate Pipeline 👩‍🏫🧑‍🏫"
weight = 4
tags = ["mongo"] 
+++



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
# Build the aggregation pipeline
# Write a match query to find only the documents about artifacts that have a width greater than or equal to 40cm.
match_query = {'$match': {'measurements.elementMeasurements.Width': {'$gte': 40}}}

# Write an aggregation query that counts the number of documents, grouped by "country"
group_query = {'$group': {'_id': "$country", 'count': { '$sum': 1 }}}

# Create a dictionary that will allow the pipeline to sort by count in descending order
sort_values = {'$sort': { 'count': -1 }}

# Put the pipeline together
pipeline = [match_query, group_query, sort_values]
# Run the pipeline through the aggregate method and save the results to a variable
results = list(artifacts.aggregate(pipeline))
# Print the number of countries in the result
print("Number of countries in result: ", len(results))

# Print the first 10 results
pprint(results[0:10])

# Convert mongo result to Pandas DataFrame
result_df = pd.DataFrame(results)

print("Rows in DataFrame: ", len(result_df))
result_df.head(10)

 


 
```