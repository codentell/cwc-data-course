+++
title = "10. Traveling Companions  Part 3  👩‍🎓👨‍🎓"
weight = 10
tags = ["matplotlib"] 
+++

# Traveling Companions, Part 3

This is the third and final part of a three-part mini-project.

In this final part, you will take the DataFrame you created and, using Matplotlib, chart a comparison of three different countries for one type of traveling companion between 2016 and 2018.

## Instructions

* Check the comments in each cell of this Jupyter Notebook file for activity instructions.

* Your output should align with the following figure, depending on the user’s input variable:

![outcome.](../images/10-TravelCompanion_Output.png)

## Bonus

Try to modify the notebook file so that it will request user input for the 3 country variables and the traveling companion type.

## References

[Tourism Malaysia](https://www.data.gov.my/data/en_US/dataset/travelling-companion)

- - -



## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Create a variable for each country to chart
country1 = "USA"
country2 = "THAILAND"
country3 = "PHILIPPINES"
# Set type of traveling companion
columns_to_compare = "With Spouse"
# Create a Series for each chosen country that looks for the chosen travel companion from 2016 to 2018
country1_traveler_over_time = travel_reduced.loc[country1,
                                                [f"2016 {columns_to_compare}",
                                                 f"2017 {columns_to_compare}", 
                                                 f"2018 {columns_to_compare}"]]

country2_traveler_over_time = travel_reduced.loc[country2,
                                                [f"2016 {columns_to_compare}",
                                                 f"2017 {columns_to_compare}", 
                                                 f"2018 {columns_to_compare}"]]

country3_traveler_over_time = travel_reduced.loc[country3,
                                                [f"2016 {columns_to_compare}",
                                                 f"2017 {columns_to_compare}", 
                                                 f"2018 {columns_to_compare}"]]
# Create a list of the years that we will use as our x axis
years = [2016,2017,2018]

# Plot our line that will be used to track the first country's traveling companion percentage over the years
plt.plot(years, country1_traveler_over_time, color="green", label=country1)

# Plot our line that will be used to track the second country's traveling companion percentage over the years
plt.plot(years, country2_traveler_over_time, color="blue", label=country2)

# Plot our line that will be used to track the third country's traveling companion percentage over the years
plt.plot(years, country3_traveler_over_time, color="orange", label=country3)

# Place a legend on the chart in what matplotlib believes to be the "best" location
plt.legend(loc="best")

plt.title("Traveling " + columns_to_compare + " Country Comparison")
plt.xlabel("Years")
plt.xticks(np.arange(min(years), max(years)+1, 1.0))
plt.ylabel("% Travelers")

# Print our chart to the screen
plt.show()
```
{{% /expand%}}