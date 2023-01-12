+++
title = "01.  Merging 👩‍🏫🧑‍🏫"
weight = 1
tags = ["pandas"] 
+++

```python
# Dependencies
import pandas as pd
raw_data_info = {
    "customer_id": [112, 403, 999, 543, 123],
    "name": ["John", "Kelly", "Sam", "April", "Bobbo"],
    "email": ["jman@gmail", "kelly@aol.com", "sports@school.edu", "April@yahoo.com", "HeyImBobbo@msn.com"]
}
info_df = pd.DataFrame(raw_data_info, columns=["customer_id", "name", "email"])
info_df

# Create DataFrames
raw_data_items = {
    "customer_id": [403, 112, 543, 999, 654],
    "item": ["soda", "chips", "TV", "Laptop", "Cooler"],
    "cost": [3.00, 4.50, 600, 900, 150]
}
items_df = pd.DataFrame(raw_data_items, columns=[
                        "customer_id", "item", "cost"])
items_df

# Merge two dataframes using an inner join
merge_df = pd.merge(info_df, items_df, on="customer_id")
merge_df

# Merge two dataframes using an outer join
merge_df = pd.merge(info_df, items_df, on="customer_id", how="outer")
merge_df

# Merge two dataframes using a left join
merge_df = pd.merge(info_df, items_df, on="customer_id", how="left")
merge_df

# Merge two dataframes using a right join
merge_df = pd.merge(info_df, items_df, on="customer_id", how="right")
merge_df
```
