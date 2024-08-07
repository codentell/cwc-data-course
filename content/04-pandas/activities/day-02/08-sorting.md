+++
title = "08.  Sorting 👩‍🏫🧑‍🏫"
weight = 8
tags = ["pandas"] 
+++

```python

# Import Dependencies
import pandas as pd
csv_path = "Resources/VT_tax_statistics.csv"
taxes_df = pd.read_csv(csv_path, encoding="UTF-8")
taxes_df.head()

# Sorting the DataFrame based on "Meals" column
# Will sort from lowest to highest if no other parameter is passed
meals_taxes_df = taxes_df.sort_values("Meals")
meals_taxes_df.head()

# To sort from highest to lowest, ascending=False must be passed in
meals_taxes_df = taxes_df.sort_values("Meals", ascending=False)
meals_taxes_df.head()

# It is possible to sort based upon multiple columns
meals_and_rent_count_df = taxes_df.sort_values(
    ["Meals Count", "Rent Count"], ascending=False)
meals_and_rent_count_df.head(15)


# To see the sorting by multiple columns better, we can compare the last 
# DataFrame with a second column sort on "Alcohol Count"
# (Compare the order of the two "54" value Rent Count rows)
meals_and_alcohol_count_df = taxes_df.sort_values(
    ["Meals Count", "Alcohol Count"], ascending=False)
meals_and_alcohol_count_df.head(15)

# The index can be reset to provide index numbers based on the new rankings.
new_index_df = meals_and_alcohol_count_df.reset_index(drop=True)
new_index_df.head()

 
```