+++
title = "05.  Mapping 👩‍🏫🧑‍🏫"
weight = 5
tags = ["pandas"] 
+++

```python

import pandas as pd
# Mapping lets you format an entire DataFrame
file = "Resources/Seattle_Housing_Cost_Burden.csv"
file_df = pd.read_csv(file)
file_df.head()

# Use Map to format all the columns
file_df["INCOME"] = file_df["INCOME"].map("${:,.2f}".format)
file_df["COSTS"] = file_df["COSTS"].map("${:,.2f}".format)
file_df["PERCENT30"] = (file_df["PERCENT30"]*100).map("{:.1f}%".format)
file_df["PERCENT3050"] = (file_df["PERCENT3050"]*100).map("{:.1f}%".format)
file_df["PERCENT50"] = (file_df["PERCENT50"]*100).map("{:.1f}%".format)
file_df["PERCENT_NODATA"] = (file_df["PERCENT_NODATA"]*100).map("{:.1f}%".format)
file_df["PERCENT_NOBURDEN"] = (file_df["PERCENT_NOBURDEN"]*100).map("{:.1f}%".format)
file_df["TOTAL"] = file_df["TOTAL"].map("{:,}".format)
file_df.head()

# Mapping has changed the datatypes of the columns to strings
file_df.dtypes

```