+++
title = "05.  Data Functions 👩‍🏫🧑‍🏫"
weight = 5
tags = ["pandas"] 
+++


```python
# Dependencies
import pandas as pd

# Save path to data set in a variable
data_file = "./Resources/dataSet.csv"

# Use Pandas to read data
data_file_df = pd.read_csv(data_file)
data_file_df.head()

# Display a statistical overview of the DataFrame
data_file_df.describe()

# Reference a single column within a DataFrame
data_file_df["Amount"].head()

# Reference multiple columns within a DataFrame
data_file_df[["Amount", "Gender"]].head()

# The mean method averages the series
average = data_file_df["Amount"].mean()
average

# The sum method adds every entry in the series
total = data_file_df["Amount"].sum()
total

# The unique method shows every element only once
unique = data_file_df["Car"].unique()
unique

# The value_counts method counts unique values in a column
count = data_file_df["Gender"].value_counts()
count

# Calculations can also be performed on Series and added into DataFrames as new columns
thousands_of_dollars = data_file_df["Amount"]/1000
data_file_df["Thousands of Dollars"] = thousands_of_dollars

data_file_df.head()

```