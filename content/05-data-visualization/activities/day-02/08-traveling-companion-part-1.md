+++
title = "08. Traveling Companions  Part 1  👩‍🎓👨‍🎓"
weight = 8
tags = ["matplotlib"] 
+++

# Traveling Companions, Part 1

This is Part 1 of a three-part mini-project.

In this first part of the activity, you will take three separate CSVs that were gathered from Tourism Malaysia, merge them together, and then create charts to visualize a comparison of travelers to Malaysia from different countries of origin over three years.

## Instructions

* Check the comments in each cell of this Jupyter Notebook file for activity instructions.

* Your final table should align with the following table:

![Merged Table.](../images/08-TravelingCompanion_Output.png)

## References

[Tourism Malaysia](https://www.data.gov.my/data/en_US/dataset/travelling-companion)

- - -




## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

import matplotlib.pyplot as plt
import pandas as pd
import numpy as np
# Take in all of our traveler data and read it into pandas
travel_2016 = "./Resources/2016_travelers.csv"
travel_2017 = "./Resources/2017_travelers.csv"
travel_2018 = "./Resources/2018_travelers.csv"

travel_2016_df = pd.read_csv(travel_2016)
travel_2017_df = pd.read_csv(travel_2017)
travel_2018_df = pd.read_csv(travel_2018)
# Merge the first two datasets on "COUNTRY OF NATIONALITY" so that no data is lost (should be 44 rows)
combined_travel_df = pd.merge(travel_2016_df, travel_2017_df,
                                 how='outer', on='COUNTRY OF NATIONALITY')
combined_travel_df.head()

# Rename our _x columns to "2016 Alone", "2016 With Spouse", "2016 With Children", "2016 With Family/Relatives",
# "2016 Student Group", "2016 With Friends", "2016 With Business Associate", "2016 With Incentive Group",
# and "2016 Others"

combined_travel_df = combined_travel_df.rename(columns={"ALONE_x":"2016 Alone",
                                                        "WITH SPOUSE_x":"2016 With Spouse",
                                                        "WITH CHILDREN_x":"2016 With Children",
                                                        "WITH FAMILY/RELATIVES_x":"2016 With Family/Relatives",
                                                        "STUDENT GROUP_x":"2016 Student Group",
                                                        "WITH FRIENDS_x":"2016 With Friends",
                                                        "WITH BUSINESS ACCOCIATE_x":"2016 With Business Associate",
                                                        "WITH INCENTIVE GROUP_x":"2016 With Incentive Group",
                                                        "OTHERS_x":"2016 Others"})

# Rename our _y columns to "2016 Alone", "2016 With Spouse", "2016 With Children", "2016 With Family/Relatives",
# "2016 Student Group", "2016 With Friends", "2016 With Business Associate", "2016 With Incentive Group",
# and "2016 Others"
combined_travel_df = combined_travel_df.rename(columns={"ALONE_y":"2017 Alone",
                                                        "WITH SPOUSE_y":"2017 With Spouse",
                                                        "WITH CHILDREN_y":"2017 With Children",
                                                        "WITH FAMILY/RELATIVES_y":"2017 With Family/Relatives",
                                                        "STUDENT GROUP_y":"2017 Student Group",
                                                        "WITH FRIENDS_y":"2017 With Friends",
                                                        "WITH BUSINESS ACCOCIATE_y":"2017 With Business Associate",
                                                        "WITH INCENTIVE GROUP_y":"2017 With Incentive Group",
                                                        "OTHERS_y":"2017 Others"})

combined_travel_df.head()

# Merge our newly combined dataframe with the 2018 dataframe
combined_travel_df = pd.merge(combined_travel_df, travel_2018_df, how="outer", on="COUNTRY OF NATIONALITY")
combined_travel_df


# Rename "ALONE", "WITH SPOUSE", "WITH CHILDREN", "WITH FAMILY/RELATIVES", "STUDENT GROUP", "WITH FRIENDS",
# "WITH BUSINESS ACCOCIATE","WITH INCENTIVE GROUP", "OTHERS" to 
# "2018 Alone", "2018 With Spouse", "2018 With Children", "2018 With Family/Relatives", "2018 Student Group", 
# "2018 With Friends", "2018 With Business Associate", "2018 With Incentive Group", and "2018 Others"
combined_travel_df = combined_travel_df.rename(columns={"ALONE":"2018 Alone",
                                                        "WITH SPOUSE":"2018 With Spouse",
                                                        "WITH CHILDREN":"2018 With Children",
                                                        "WITH FAMILY/RELATIVES":"2018 With Family/Relatives",
                                                        "STUDENT GROUP":"2018 Student Group",
                                                        "WITH FRIENDS":"2018 With Friends",
                                                        "WITH BUSINESS ACCOCIATE":"2018 With Business Associate",
                                                        "WITH INCENTIVE GROUP":"2018 With Incentive Group",
                                                        "OTHERS":"2018 Others"})

combined_travel_df.head()
 
```
{{% /expand%}}