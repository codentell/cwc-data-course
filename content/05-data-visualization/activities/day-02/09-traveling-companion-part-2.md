+++
title = "09. Traveling Companions  Part 2  👩‍🎓👨‍🎓"
weight = 9
tags = ["matplotlib"] 
+++


# Traveling Companions, Part 2

This is Part 2 of a three-part mini-project.

In this second part, you will examine the averages of each column and reduce the DataFrame to include only types of companion travelers that are above 1% across all three years.

## Instructions

* Your final table should align with the following table:

![Companion Output.](../images/09-TravelingCompanion2_Output.png)


## References

[Tourism Malaysia](https://www.data.gov.my/data/en_US/dataset/travelling-companion)


- - -




## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Check the mean of the columns
combined_travel_df.mean()

# Reduce columns where mean of traveling companions is > 1 across all years
travel_reduced = pd.DataFrame(combined_travel_df[["COUNTRY OF NATIONALITY",
                                                  "2016 Alone","2016 With Spouse","2016 With Children",
                                                  "2016 With Family/Relatives","2016 With Friends",
                                                  "2016 With Business Associate","2017 Alone",
                                                  "2017 With Spouse","2017 With Children",
                                                  "2017 With Family/Relatives","2017 With Friends",
                                                  "2017 With Business Associate","2018 Alone",
                                                  "2018 With Spouse","2018 With Children",
                                                  "2018 With Family/Relatives","2018 With Friends",
                                                  "2018 With Business Associate"]])

# Set index to "Country of Nationality"
travel_reduced = travel_reduced.set_index("COUNTRY OF NATIONALITY")
travel_reduced
```
{{% /expand%}}