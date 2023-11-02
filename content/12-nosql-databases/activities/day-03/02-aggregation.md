+++
title = "02. Aggregation 👩‍🏫🧑‍🏫"
weight = 2
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
# Write an aggregation query that counts the number of documents, grouped by "country"
query = [{'$group': {'_id': "$country", 'count': { '$sum': 1 }}}]
# Run the query with the aggregate method and save the results to a variable
results = list(artifacts.aggregate(query))
# Print the number of countries in the result
print("Number of countries in result: ", len(results))

# Print the first 10 results
pprint(results[0:10])

# Convert mongo result to Pandas DataFrame
result_df = pd.DataFrame(results)

print("Rows in DataFrame: ", len(result_df))
result_df.head(10)

 


 
```