+++
title = "03. Group Plots 👩‍🏫🧑‍🏫"
weight = 3
tags = ["matplotlib"] 
+++


```python

%matplotlib notebook

# Import Dependencies
import matplotlib.pyplot as plt
import pandas as pd
# Import our data into pandas from CSV
accident_string = '../Resources/accidents.csv'
accidents_df = pd.read_csv(accident_string, low_memory=False)

accidents_df

# Create a group based on the values in the 'FUNC_SYSNAME' column
# 'FUNC_SYSNAME' stores the type of road the accident occurred
accident_road_type = accidents_df.groupby('FUNC_SYSNAME')

# Count how many times each road type appears in our group
count_road_types = accident_road_type['FUNC_SYSNAME'].count()

count_road_types

# Create a bar chart based off of the group series from before
count_chart = count_road_types.plot(kind='bar', figsize=(6,8))

# Set the xlabel and ylabel using class methods
count_chart.set_xlabel("Road Type")
count_chart.set_ylabel("Number of Accidents")

plt.show()
plt.tight_layout()
```
