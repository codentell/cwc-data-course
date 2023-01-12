+++
title = "02.  Census Merging 👩‍🎓👨‍🎓"
weight = 2
tags = ["pandas"] 
+++

# Census Merging

In this activity, you will merge the two Census datasets that we created in the last class and then do a calculation and sort the values.

## Instructions

* Read in both of the CSV files, and print out their DataFrames.

* Perform an inner merge that combines both DataFrames on the "Year" and "State" columns.

* Create a DataFrame that filters the data on only 2019.

* Add a new column that calculates the Poverty Rate.

* Sort the data by Poverty Rate and Average Per Capita Income by County, highest to lowest, to find the state or territory with the highest poverty rate.

* Print out the data for the state or territory with the highest poverty rate.

* Bonus: Print out the data for the state or territory with the lowest poverty rate with one line of code.

## References

Data Source: [U.S. Census API - ACS 5-Year Estimates 2016-2019](https://www.census.gov/data/developers/data-sets/census-microdata-api.ACS_5-Year_PUMS.html)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
# Import Dependencies
import pandas as pd
state_avg_csv = "Resources/state_avg.csv"
state_totals_csv = "Resources/state_totals.csv"
state_avg_df = pd.read_csv(state_avg_csv)
state_totals_df = pd.read_csv(state_totals_csv)
state_avg_df.head()

state_totals_df.head()

# Merge the two DataFrames together based on the Year and State they share
census_df = pd.merge(state_avg_df, state_totals_df, on=["Year", "State"])
census_df.head()


# Create a DataFrame that filters the data on only 2019
census_2019_df = pd.DataFrame(census_df.loc[census_df["Year"]==2019,:])
census_2019_df.head()


# Add a new column that calculates the Poverty Rate
census_2019_df["Poverty Rate (%)"] = census_2019_df["Total Population in Poverty"] / \
                                        census_2019_df["Total Population"] * 100
census_2019_df.head()
	
# Sort the data by Poverty Rate and Average Per Capita Income by County, Highest to Lowest
poverty_sorted_df = census_2019_df.sort_values(["Poverty Rate (%)", 
                                             "Average Per Capita Income by County"],
                                           ascending=False)

# Reset Index
poverty_sorted_df = poverty_sorted_df.reset_index(drop=True)
poverty_sorted_df.head()

# Print out the data for the most poverty stricken state or territory
highest_poverty = poverty_sorted_df.loc[0, :]
highest_poverty


# Bonus: Print out the data for the least poverty sticken state or territory with one line of code
poverty_sorted_df.loc[len(poverty_sorted_df)-1, :]

 
```
{{% /expand%}}