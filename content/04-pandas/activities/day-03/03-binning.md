+++
title = "03.  Census Merging 👩‍🏫🧑‍🏫"
weight = 3
tags = ["pandas"] 
+++

```python

# Import Dependencies
import pandas as pd
raw_data = {
    'Class': ['Oct', 'Oct', 'Jan', 'Jan', 'Oct', 'Jan'], 
    'Name': ["Cyndy", "Logan", "Laci", "Elmer", "Crystle", "Emmie"], 
    'Test Score': [90, 59, 72, 88, 98, 60]}
df = pd.DataFrame(raw_data)
df

# Create the bins in which Data will be held
# Bins are 0, 59.9, 69.9, 79.9, 89.9, 100.   
bins = [0, 59.9, 69.9, 79.9, 89.9, 100]

# Create the names for the five bins
group_names = ["F", "D", "C", "B", "A"]
df["Test Score Summary"] = pd.cut(df["Test Score"], bins, labels=group_names, include_lowest=True)
df

# Creating a group based off of the bins
df = df.groupby("Test Score Summary")
df.max()

 

```