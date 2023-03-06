+++
title = "06. Scrape Pandas 👩‍🏫🧑‍🏫"
weight = 6
tags = ["scraping"] 
+++

```python
import pandas as pd

# Read in HTML tables into a DataFrame
df = pd.read_html('https://static.bc-edx.com/data/web/mars_facts/index.html')

# Select the second table
mars_df = df[1]

# Rename columns
mars_df.columns=['description', 'Mars', 'Earth']

# Remove the first row from the DataFrame
mars_df = mars_df.iloc[1:]

mars_df
```

