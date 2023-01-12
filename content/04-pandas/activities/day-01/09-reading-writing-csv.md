+++
title = "09.  Reading Writing CSV 👩‍🏫🧑‍🏫"
weight = 9
tags = ["pandas"] 
+++

```python
# Dependencies
import pandas as pd

# Store filepath in a variable
file_one = "./Resources/DataOne.csv"

# Read our Data file with the pandas library
# Not every CSV requires an encoding, but be aware this can come up
file_one_df = pd.read_csv(file_one, encoding="ISO-8859-1")

# Show just the header
file_one_df.head()

# Show a single column
file_one_df["full_name"].head()

# Show mulitple specific columns--note the extra brackets
file_one_df[["full_name", "email"]].head()

# Head does not change the DataFrame--it only displays it
file_one_df.head()

# Export file as a CSV, without the Pandas index, but with the header
file_one_df.to_csv("./output/fileOne.csv", index=False, header=True)

```