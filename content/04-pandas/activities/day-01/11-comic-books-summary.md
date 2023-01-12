+++
title = "11.  Comic Books Summary 👩‍🎓👨‍🎓"
weight = 11
tags = ["pandas"] 
+++


In this activity, you use some of Pandas’ built-in functions to create a new summary DataFrame based on the modified version of the comic book DataFrame.

## Instructions

Using the modified DataFrame that was created earlier, create a summary table for the dataset that includes the following pieces of information:

* The count of unique authors within the DataFrame

* The count of unique countries of publication within the DataFrame

* The year of the earliest published book in the DataFrame

* The year of the latest published book in the DataFrame

## References

 Data modified from "Comic books CSV" Updated April 2021. Initially released in 2014 to accompany the British Library's exhibition Comics Unmasked. [https://www.bl.uk/collection-metadata/downloads](https://www.bl.uk/collection-metadata/downloads)

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Import Dependencies
import pandas as pd

# File to Load
comics_path = "./Resources/books_clean.csv"

# Read the modified Comic Books csv and store into Pandas DataFrame
comics_df = pd.read_csv(comics_path, encoding="utf-8")
comics_df.head()

# Calculate the number of unique authors in the DataFrame
author_count = len(comics_df["Author"].unique())

# Calculate the number of unique publication countries in the DataFrame
country_count = len(comics_df["Country of Publication"].unique())

# Calculate the earliest/latest year a book was published
earliest_year = comics_df["Publication Year"].min()
latest_year = comics_df["Publication Year"].max()

# Place all of the data found into a summary DataFrame
summary_df = pd.DataFrame({"Total Unique Authors": [author_count],
                              "Total Unique Publication Countries": [country_count],
                              "Earliest Year": [earliest_year],
                              "Latest Year": [latest_year]})
summary_df
```
{{% /expand%}}