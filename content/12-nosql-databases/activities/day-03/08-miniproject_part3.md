+++
title = "08.  MongoDB Mini-Project Part 3: Plotting the Data 👩‍🎓👨‍🎓"
weight = 8
tags = ["mongo"] 
+++

# MongoDB Mini-Project Part 3: Plotting the Data

For Part 3 of the mini-project, you will practice plotting Mongo results with Matplotlib.

## Instructions

You may use the starter code provided, which contains code for an aggregation pipeline and resulting normalized DataFrame, which you can practice plotting with Matplotlib. However, you are also welcome to write your own aggregation pipeline to plot the data.

If there is enough remaining time at the end of the class, groups will be invited to present their charts to the class.

You may wish to review your Matplotlib content in order to complete the mini-project, but this is an exciting time to see how you can integrate different skills you have learned throughout the course. Feel free to also review the [Pandas Plot documentation](https://pandas.pydata.org/docs/reference/api/pandas.DataFrame.plot.html)

You are welcome to use whatever type of chart you think will best represent the results from your aggregation pipeline, or use the starter code comments as a guide.

Use `plt.savefig()` to save your chart(s).

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
import matplotlib.pyplot as plt
# Create an instance of MongoClient
mongo = MongoClient(port=27017)

# assign the met database to a variable name
db = mongo['met']

# assign the collection to a variable
artifacts = db['artifacts']
# Build the aggregation pipeline

# Write an aggregation query that counts the number of documents, grouped by "Country", then "classification"
group_query = {'$group': {'_id': {"country": "$country",
                                  "classification": "$classification"}, 
                          'count': { '$sum': 1 }
                         }
              }

# Create a match query that matches only the rows that have 5 or more documents in 'count'
match_query = {'$match': {'count': {'$gte': 5}}}

# Create a dictionary that will allow the pipeline to sort by country in alphabetical order, 
# then count in descending order
sort_values = {'$sort': { '_id.country': 1, 'count': -1 }}

# Put the pipeline together
pipeline = [group_query, match_query, sort_values]
# Run the pipeline through the aggregate method, cast the results as a list, and save the results to a variable
results = list(artifacts.aggregate(pipeline))
# Print the number of rows in the result
print("Number of rows in result: ", len(results))
Number of rows in result:  46
# Print the first 10 results
pprint(results[0:10])


# Extract the fields from the _id so they're in separate columns in a Pandas DataFrame
aggregated_df = pd.json_normalize(results)
aggregated_df.head()

# Rename the columns
aggregated_df = aggregated_df.rename(columns={"count": "number of artifacts",
                                              "_id.classification": "classification",
                                              "_id.country": "country"})
aggregated_df.head()

# Reorder the columns
aggregated_df = aggregated_df[["country", "classification", "number of artifacts"]]

# Print the first 10 rows of the DataFrame
aggregated_df.head(10)

# Print out the unique countries
aggregated_df["country"].unique()

# Print out the unique classifications
aggregated_df["classification"].unique()

# Find out which countries have the most classifications
# Create a DataFrame that groups by country
countries_grouped = pd.DataFrame(aggregated_df[["country", "classification"]].groupby("country").count())

# Print the DataFrame, sorted in descending order on classification
countries_grouped.sort_values("classification", ascending=False)


# Create a DataFrame of just the Indonesian artifacts
indonesia_df = aggregated_df.loc[aggregated_df["country"]=="Indonesia",["classification", "number of artifacts"]]
indonesia_df

# Create a pie chart of the Indonesian artifacts
indonesia_df.plot(kind="pie", 
                  y="number of artifacts",
                  autopct='%1.1f%%', 
                  ylabel='',
                  labels=indonesia_df.classification, 
                  legend=False,
                  title="Percentage of Indonesian Artifacts by classification", 
                  figsize=(6,6))
plt.savefig("charts/IndonesiaChart.png")
plt.show()

# Create a horizontal bar chart of the Nigerian artifacts
aggregated_df.loc[aggregated_df["country"]=="Nigeria",:].plot(kind="barh", x="classification", y="number of artifacts",
              title="Number of Nigerian Artifacts by classification", figsize=(6,6))
plt.xlabel("Number of Artifacts")
plt.savefig("charts/NigeriaChart.png")
plt.show()

# Print out the DataFrame with just the Nigerian artifacts
aggregated_df.loc[aggregated_df["country"]=="Nigeria",:]

# Data Source: The Metropolitan Museum of Art (2022). The Metropolitan Museum of Art Collection API https://metmuseum.github.io/. Licensed under the Creative Commons 0 License.
# Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".
```
{{% /expand%}}

 