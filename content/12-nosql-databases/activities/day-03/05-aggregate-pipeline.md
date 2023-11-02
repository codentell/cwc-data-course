+++
title = "05. Aggregate Pipeline 👩‍🎓👨‍🎓"
weight = 5
tags = ["mongo"] 
+++

# Build a Pipeline

In this activity, you will practice building an aggregation pipeline in MongoDB.

## Instructions

* In Jupyter Notebook, open [build_a_pipeline.ipynb](Unsolved/build_a_pipeline.ipynb). Run the first two blocks of code to import your dependencies, create an instance of the MongoClient, and save the database and collection to variables.

* Write a match query to find only the documents about artifacts that have a classification where "Wood" is contained in the value.

    **Hint:** Remember to use the `$regex` operator.

* Write an aggregation query that counts the number of documents and finds the maximum height, grouped by "classification". You may repurpose the query from the last student activity, so you only need to add the key-value pair for the aggregation operator to find the maximum height.

    **Hint:** `$max` is the aggregation operator to find the maximum value in a field.

* Create a dictionary that will allow the pipeline to sort by count in descending order, then sort by classification in alphabetical order.

* Create a list called `pipeline` that contains each stage in the pipeline process: match, group, and sort.

* Run the pipeline through the aggregate method and save the results to a variable.

* Print the number of classifications in the result.

* Print the first 10 results.

* Convert mongo result to Pandas DataFrame.

* Display the first 10 rows of the Pandas DataFrame.
