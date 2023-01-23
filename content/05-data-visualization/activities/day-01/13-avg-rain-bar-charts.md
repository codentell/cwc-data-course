+++
title = "13. Average Rain Bar Charts 👩‍🎓👨‍🎓"
weight = 13
tags = ["matplotlib"] 
+++

# Average Rainfall

In this activity, you will create a bar chart that shows the average rainfall in different states by importing data from a CSV file.

## Instructions

* Review the raw data (resources/avg_rain_state.csv) in the `Resources` folder. This dataset contains the average rainfall per state in any given year.

*Ggenerate a plot that shows the average rainfall per state, as per image below:

![rain_fall](../images/avg_state_rain.png)

## Hint

* Think critically about the different plots we discussed today. Ask yourself which type of plot summarizes the data most effectively.

* Be sure to add a title, axis labels, and any other aesthetic elements that may help make the visualization more effective.

## References

M. Palecki, I. Durre, J. Lawrimore, and S. Applequist, 2021: U.S. Annual/Seasonal Climate Normals (2006-2020) [National Centers for Environmental Information, National Oceanic and Atmospheric Administration](https://www.ncei.noaa.gov/metadata/geoportal/rest/metadata/item/gov.noaa.ncdc%3AC01623/html). N.B. This data was downloaded, combined, reduced, and calculated in Pandas.

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

%matplotlib notebook
# Dependencies
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
# Load in csv
rain_df = pd.read_csv("../Resources/avg_rain_state.csv")
rain_df.head()

# Set x axis and tick locations
x_axis = np.arange(len(rain_df))
tick_locations = [value+0.4 for value in x_axis]
# Create a list indicating where to write x labels and set figure size to adjust for space
plt.figure(figsize=(20,4))
plt.bar(x_axis, rain_df["Inches"], color='r', alpha=0.5, align="edge")
plt.xticks(tick_locations, rain_df["State"], rotation="vertical")

# Set x and y limits
plt.xlim(-0.25, len(x_axis))
plt.ylim(0, max(rain_df["Inches"])+10)

# Set a Title and labels
plt.title("Average Rain per State")
plt.xlabel("State")
plt.ylabel("Average Amount of Rainfall in Inches")

# Save our graph and show the grap
plt.tight_layout()
plt.savefig("../Images/avg_state_rain.png")
plt.show()
 
```
{{% /expand%}}