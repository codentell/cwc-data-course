+++
title = "03. Aggregate By Classification 👩‍🎓👨‍🎓"
weight = 3
tags = ["mongo"] 
+++

# Aggregate by Classification

In this activity, you will practice using the aggregate method in MongoDB.

## Instructions

* In Jupyter Notebook, open [aggregate_by_classification.ipynb](Unsolved/aggregate_by_classification.ipynb). Run the first two blocks of code to import your dependencies, create an instance of the MongoClient, and save the database and collection to variables.

* Write an aggregation query that counts the number of documents, grouped by "classification".

* Run the query with the aggregate method and save the results to a variable.

* Print the number of classifications in the result.

* Print the first 10 results.

* Convert mongo result to Pandas DataFrame.

* Display the first 10 rows of the Pandas DataFrame.

## Reference

[The Metropolitan Museum of Art](https://www.metmuseum.org/) (2022). The Metropolitan Museum of Art Collection API https://metmuseum.github.io/. Licensed under the [Creative Commons 0 License](https://creativecommons.org/publicdomain/zero/1.0/)<br />
Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
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
# Write an aggregation query that counts the number of documents, grouped by "classification"
query = [{'$group': {'_id': "$classification", 'count': { '$sum': 1 }}}]
# Run the query with the aggregate method and save the results to a variable
results = list(artifacts.aggregate(query))
# Print the number of classifications in the result
print("Number of classifications in result: ", len(results))
Number of classifications in result:  64
# Print the first 10 results
pprint(results[0:10])

# Convert mongo result to Pandas DataFrame
result_df = pd.DataFrame(results)

# Print out the length of the DataFrame
print("Rows in DataFrame: ", len(result_df))

# Display the first 10 rows of the DataFrame
result_df.head(10)
```
{{% /expand%}}