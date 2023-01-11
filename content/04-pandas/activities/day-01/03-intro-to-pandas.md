+++
title = "03. Intro to pandas 👩‍🏫🧑‍🏫"
weight = 3
tags = ["pandas"] 
+++

```python
# Dependencies
import pandas as pd
# We can create a Pandas Series from a raw list
data_series = pd.Series(["UCLA", "UC Berkeley", "UC Irvine",
                         "University of Central Florida", "Rutgers University"])
print(data_series)
# 0                             UCLA
# 1                      UC Berkeley
# 2                        UC Irvine
# 3    University of Central Florida
# 4               Rutgers University
# dtype: object


# Convert a list of dictionaries into a dataframe
states_dicts = [{"STATE": "New Jersey", "ABBREVIATION": "NJ"},
                {"STATE": "New York", "ABBREVIATION": "NY"}]

states_df = pd.DataFrame(states_dicts)
print(states_df)
# STATE	ABBREVIATION
# 0	New Jersey	NJ
# 1	New York	NY

# Convert a single dictionary containing lists into a dataframe
pharaoh_df = pd.DataFrame(
    {"Dynasty": ["Early Dynastic Period", "Old Kingdom"],
     "Pharaoh": ["Thinis", "Memphis"]
     }
)
print(pharaoh_df)
# Dynasty	Pharaoh
# 0	Early Dynastic Period	Thinis
# 1	Old Kingdom	Memphis
```