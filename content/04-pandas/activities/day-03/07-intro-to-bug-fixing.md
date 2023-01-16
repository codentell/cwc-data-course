+++
title = "07.  Intro to bug fixing 👩‍🏫🧑‍🏫"
weight = 7
tags = ["pandas"] 
+++

```python
# Import dependencies
import pandas as pd
# Reference to CSV and reading CSV into Pandas DataFrame
csv_path = "Resources/veterans.csv"
veterans_df = pd.read_csv(csv_path)
veterans_df.head()

veterans_df.columns

# Converting the "Percentage" column to floats
veterans_df["Percentage"] = veterans_df["Percentage"].str.replace("%", "").astype

# Finding the average percentage of veterans living within 75 miles of a cemetery
veterans_df["Percentage"].mean()
```
 