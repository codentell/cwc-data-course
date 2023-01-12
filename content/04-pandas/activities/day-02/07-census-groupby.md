+++
title = "07. Census Group By 👩‍🎓👨‍🎓"
weight = 7
tags = ["pandas"] 
+++

# Exploring Census Data

In this activity, you will revisit the U.S. Census data and create DataFrames with calculated totals and averages for each state by year.

## Instructions

1. Read in the census CSV file with Pandas.

2. Create two new DataFrames, one to find totals and another to find averages. DataFrames should include:

    * Totals for population, employed civilians, unemployed civilians, people in the military, and poverty count.

    * Averages for median age, household income, and per capita income.

3. Create new DataFrames once the totals and averages have been grouped by each year and state.

4. Rename any columns to reflect the data calculations.

5. Export the resulting tables to CSVs. We will be using them again in our next class.

## References

[U.S. Census API - ACS 5-Year Estimates 2016-2019](https://www.census.gov/data/developers/data-sets/census-microdata-api.ACS_5-Year_PUMS.html)

- - -


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Dependencies
import pandas as pd
import numpy as np
# Save file path to variable
census_csv = "Resources/census_data_2016-2019.csv"
# Read with Pandas
census_df = pd.read_csv(census_csv)
census_df.head()


# Create a DataFrame with columns to total: Year, County, State, Population, 
# Employed Civilians, Unemployed Civilians, People in the Military, Poverty Count
census_totals_df = census_df[["Year", "County", "State", "Population", 
                              "Employed Civilians", "Unemployed Civilians",
                              "People in the Military", "Poverty Count"]]
census_totals_df.head()


# Create a dataframe of the totals for each state by year.
census_total_group = census_totals_df.groupby(["Year", "State"])

state_totals_df = census_total_group.sum()
state_totals_df


# Rename columns to make them more understandable
state_totals_df = state_totals_df.rename(columns={"Population": "Total Population",
                                               "Employed Civilians": "Total Employed Civilians",
                                               "Unemployed Civilians": "Total Unemployed Civilians",
                                               "People in the Military": "Total People in the Military",
                                               "Poverty Count": "Total Population in Poverty"})
state_totals_df


# Create a DataFrame with columns to average: Year, County, State, Median Age, 
# Household Income, Per Capita Income
census_avg_df = census_df[["Year", "County", "State", "Median Age", 
                           "Household Income", "Per Capita Income"]]
census_avg_df.head()


# Rename columns to make them more understandable
state_avg_df = state_avg_df.rename(columns={"Median Age": "Average Median Age by County",
                                            "Household Income": "Average Household Income by County",
                                            "Per Capita Income": "Average Per Capita Income by County"})
state_avg_df


# Export the DataFrames to CSV
state_totals_df.to_csv("output/state_totals.csv", index=True)
state_avg_df.to_csv("output/state_avg.csv", index=True)
 
```
{{% /expand%}}