+++
title = "07. Pandas Multi Line 👩‍🏫🧑‍🏫"
weight = 7
tags = ["matplotlib"] 
+++

```python

# Dependencies
import matplotlib.pyplot as plt
import numpy as np
import pandas as pd
# Read CSV
unemployed_data_one = pd.read_csv("../Resources/unemployment_2010-2015.csv")
unemployed_data_two = pd.read_csv("../Resources/unemployment_2016-2020.csv")

# Merge our two data frames together
combined_unemployed_data = pd.merge(unemployed_data_one, unemployed_data_two, on="Country Name")
combined_unemployed_data.head()

# Delete the duplicate 'Country Code' column and rename the first one back to 'Country Code'
del combined_unemployed_data['Country Code_y']
combined_unemployed_data = combined_unemployed_data.rename(columns={"Country Code_x":"Country Code"})
combined_unemployed_data.head()
	
# Set the 'Country Code' to be our index for easy referencing of rows
combined_unemployed_data = combined_unemployed_data.set_index("Country Code")
# Collect the mean unemployment rates for the world
average_unemployment = combined_unemployed_data.mean()

# Collect the years where data was collected
years = average_unemployment.keys()
# Plot the world average as a line chart
world_avg, = plt.plot(years, average_unemployment, color="blue", label="World Average" )

# Plot the unemployment values for a single country
country_one, = plt.plot(years, combined_unemployed_data.loc['USA',["2010","2011","2012","2013","2014","2015",
                                                                  "2016","2017","2018","2019","2020"]], 
                        color="green",label=combined_unemployed_data.loc['USA',"Country Name"])

# Create a legend for our chart
plt.legend(handles=[world_avg, country_one], loc="best")

# Show the chart
plt.show()

average_unemployment.plot(label="World Average")
combined_unemployed_data.loc['USA', "2010":"2020"].plot(label="United States")
plt.legend()
plt.show()

```