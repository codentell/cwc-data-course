+++
title = "01. Loc And Iloc 👩‍🏫🧑‍🏫"
weight = 1
tags = ["pandas"] 
+++

```python
import pandas as pd
file = "./resources/baton_streets.csv"
original_df = pd.read_csv(file)
original_df.head()

# Set new index to STREET NAME
df = original_df.set_index("STREET NAME")
df.head()

# Grab the data contained within the "ADDINGTON" row and the "STREET FULL NAME" column
addington_name = df.loc["ADDINGTON", "STREET FULL NAME"]
print("Using Loc: " + addington_name)

also_addington_name = df.iloc[3, 1]
print("Using Iloc: " + also_addington_name)

# Grab the first five rows of data and the columns from "STREET NAME ID" to "POSTAL COMMUNITY"
# The problem with using "STREET NAME" as the index is that the values are not unique so duplicates are returned
# If there are duplicates and loc[] is being used, Pandas will return an error
private_to_chalfont = df.loc[["PRIVATE STREET", "4TH", "11TH", "ADDINGTON", 
                              "CHALFONT"], ["STREET NAME ID", "STREET FULL NAME", "POSTAL COMMUNITY"]]
print(private_to_chalfont)

print()

# Using iloc[] will not find duplicates since a numeric index is always unique
also_private_to_chalfont = df.iloc[0:5, 0:3]
print(also_private_to_chalfont)



# The following will select all rows for columns `STREET FULL NAME` and `POSTAL COMMUNITY`
df.loc[:, ["STREET FULL NAME", "POSTAL COMMUNITY"]].head()

# the following logic test/conditional statement returns a series of boolean values
municipal_parish = df["MUNICIPAL COMMUNITY"] == "PARISH"
municipal_parish.head()

# Loc and Iloc also allow for conditional statments to filter rows of data
# using Loc on the logic test above only returns rows where the result is True
only_prairieville = df.loc[df["POSTAL COMMUNITY"] == "PRAIRIEVILLE", :]
print(only_prairieville)

print()

# Multiple conditions can be set to narrow down or widen the filter
only_prairieville_and_jackson = df.loc[(df["POSTAL COMMUNITY"] == "PRAIRIEVILLE") | (
    df["POSTAL COMMUNITY"] == "JACKSON"), :]
print(only_prairieville_and_jackson)

```                                        
 
 