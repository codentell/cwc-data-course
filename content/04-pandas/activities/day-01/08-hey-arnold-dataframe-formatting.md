+++
title = "08.  Hey Arnold DataFrame 👩‍🎓👨‍🎓" 
weight = 8
tags = ["pandas"] 
+++


In this activity, you will take a premade DataFrame of “Hey Arnold!” characters and reorganize it so that it is easier to understand.

## Instructions

Use Pandas to create a DataFrame with the following columns and values:

* “Character_in_show”: Arnold, Gerald, Helga, Phoebe, Harold, Eugene

* “color_of_hair”: blonde, black, blonde, black, unknown, red

* “Height”: average, tallish, tallish, short, tall, short

* “Football_Shaped_Head”: True, False, False, False, False, False

Note that the column names are inconsistent and difficult to work with. Rename them to the following, respectively:

* “Character”, “Hair Color”, “Height”, “Football Head”

Create a new table that contains all of the columns in the following order:

* “Character”, “Football Head”, “Hair Color”, “Height”

---
## ✅ Solutions
{{%expand "Solutions Click Here" %}}
````python
# Dependencies
import pandas as pd

# Create a DataFrame with given columns and value
hey_arnold_df = pd.DataFrame(
    {"Character_in_show": ["Arnold", "Gerald", "Helga", "Phoebe", "Harold", "Eugene"],
     "color_of_hair": ["blonde", "black", "blonde", "black", "unknown", "red"],
     "Height": ["average", "tallish", "tallish", "short", "tall", "short"],
     "Football_Shaped_Head": [True, False, False, False, False, False]
     })

hey_arnold_df

# Rename columns for readability
hey_arnold_renamed_df = hey_arnold_df.rename(columns={"Character_in_show": "Character",
                                                "color_of_hair": "Hair Color",
                                                "Height": "Height",
                                                "Football_Shaped_Head": "Football Head"
                                                })
hey_arnold_renamed_df

# Organize the columns so they are in a more logical order
hey_arnold_alphabetical_df = hey_arnold_renamed_df[[
    "Character", "Football Head", "Hair Color", "Height"]]

hey_arnold_alphabetical_df
```
{{% /expand%}}