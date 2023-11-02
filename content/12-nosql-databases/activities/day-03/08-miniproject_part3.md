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
[{'_id': {'classification': 'Bark-Paintings', 'country': 'Australia'},
  'count': 6},
 {'_id': {'classification': 'Wood-Sculpture', 'country': 'Burkina Faso'},
  'count': 18},
 {'_id': {'classification': 'Wood-Sculpture', 'country': 'Cameroon'},
  'count': 10},
 {'_id': {'classification': 'Bone/Ivory-Sculpture', 'country': 'Canada'},
  'count': 16},
 {'_id': {'classification': 'Stone-Sculpture', 'country': 'Canada'},
  'count': 11},
 {'_id': {'classification': 'Metal-Ornaments', 'country': 'Colombia'},
  'count': 22},
 {'_id': {'classification': 'Metal-Ornaments', 'country': 'Costa Rica'},
  'count': 7},
 {'_id': {'classification': 'Stone-Ornaments', 'country': 'Costa Rica'},
  'count': 5},
 {'_id': {'classification': 'Metal-Ornaments',
          'country': 'Costa Rica or Panama'},
  'count': 10},
 {'_id': {'classification': 'Wood-Sculpture', 'country': "Côte d'Ivoire"},
  'count': 34}]
# Extract the fields from the _id so they're in separate columns in a Pandas DataFrame
aggregated_df = pd.json_normalize(results)
aggregated_df.head()
count	_id.country	_id.classification
0	6	Australia	Bark-Paintings
1	18	Burkina Faso	Wood-Sculpture
2	10	Cameroon	Wood-Sculpture
3	16	Canada	Bone/Ivory-Sculpture
4	11	Canada	Stone-Sculpture
# Rename the columns
aggregated_df = aggregated_df.rename(columns={"count": "number of artifacts",
                                              "_id.classification": "classification",
                                              "_id.country": "country"})
aggregated_df.head()
number of artifacts	country	classification
0	6	Australia	Bark-Paintings
1	18	Burkina Faso	Wood-Sculpture
2	10	Cameroon	Wood-Sculpture
3	16	Canada	Bone/Ivory-Sculpture
4	11	Canada	Stone-Sculpture
# Reorder the columns
aggregated_df = aggregated_df[["country", "classification", "number of artifacts"]]

# Print the first 10 rows of the DataFrame
aggregated_df.head(10)
country	classification	number of artifacts
0	Australia	Bark-Paintings	6
1	Burkina Faso	Wood-Sculpture	18
2	Cameroon	Wood-Sculpture	10
3	Canada	Bone/Ivory-Sculpture	16
4	Canada	Stone-Sculpture	11
5	Colombia	Metal-Ornaments	22
6	Costa Rica	Metal-Ornaments	7
7	Costa Rica	Stone-Ornaments	5
8	Costa Rica or Panama	Metal-Ornaments	10
9	Côte d'Ivoire	Wood-Sculpture	34
# Print out the unique countries
aggregated_df["country"].unique()
array(['Australia', 'Burkina Faso', 'Cameroon', 'Canada', 'Colombia',
       'Costa Rica', 'Costa Rica or Panama', "Côte d'Ivoire",
       'Democratic Republic of the Congo',
       'Ecuador, Peru, Bolivia, Chile, or Argentina', 'Indonesia',
       'Liberia', 'Mali', 'Mexico', 'Nigeria', 'Panama',
       'Papua New Guinea', 'Peru', 'United States', 'Western Australia'],
      dtype=object)
# Print out the unique classifications
aggregated_df["classification"].unique()
array(['Bark-Paintings', 'Wood-Sculpture', 'Bone/Ivory-Sculpture',
       'Stone-Sculpture', 'Metal-Ornaments', 'Stone-Ornaments',
       'Wood-Implements', 'Bone/Ivory-Ornaments', 'Sculpture-Sheet metal',
       'Textiles', 'Textiles-Woven', 'Bone/Ivory-Implements',
       'Ceramics-Containers', 'Wood-Architectural', 'Ceramics-Sculpture',
       'Ceramics-Implements', 'Bone/Ivory-Musical Instruments',
       'Bone/Ivory-Containers', 'Metal-Sculpture', 'Metal-Implements',
       'Shell-Ornaments', 'Shell'], dtype=object)
# Find out which countries have the most classifications
# Create a DataFrame that groups by country
countries_grouped = pd.DataFrame(aggregated_df[["country", "classification"]].groupby("country").count())

# Print the DataFrame, sorted in descending order on classification
countries_grouped.sort_values("classification", ascending=False)
classification
country	
Indonesia	6
Nigeria	6
United States	5
Peru	4
Mexico	4
Democratic Republic of the Congo	3
Canada	2
Costa Rica	2
Papua New Guinea	2
Côte d'Ivoire	2
Mali	1
Panama	1
Australia	1
Liberia	1
Burkina Faso	1
Ecuador, Peru, Bolivia, Chile, or Argentina	1
Costa Rica or Panama	1
Colombia	1
Cameroon	1
Western Australia	1
# Create a DataFrame of just the Indonesian artifacts
indonesia_df = aggregated_df.loc[aggregated_df["country"]=="Indonesia",["classification", "number of artifacts"]]
indonesia_df
classification	number of artifacts
15	Wood-Sculpture	14
16	Textiles	13
17	Textiles-Woven	12
18	Bone/Ivory-Implements	7
19	Ceramics-Containers	6
20	Wood-Architectural	5
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
country	classification	number of artifacts
27	Nigeria	Bone/Ivory-Sculpture	17
28	Nigeria	Wood-Sculpture	14
29	Nigeria	Bone/Ivory-Ornaments	11
30	Nigeria	Bone/Ivory-Musical Instruments	9
31	Nigeria	Bone/Ivory-Containers	7
32	Nigeria	Metal-Sculpture	7
Data Source: The Metropolitan Museum of Art (2022). The Metropolitan Museum of Art Collection API https://metmuseum.github.io/. Licensed under the Creative Commons 0 License.
Accessed Oct 3, 2022. Data collected from departmentId=5 ("Arts of Africa, Oceania, and the Americas") and search string "animal".
```

 