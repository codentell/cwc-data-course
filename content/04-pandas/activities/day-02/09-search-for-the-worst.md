+++
title = "09.  Search for the worst 👩‍🎓👨‍🎓"
weight = 9
tags = ["pandas"] 
+++

# Search For The Worst

In this activity, you will take a dataset on San Francisco Airport's utility consumption and determine which day in the dataset had the worst consumption for each utility.

## Instructions

* Read in the CSV file provided, and print it to the screen.

* Print out a list of all the values within the "Utility" column.

* Select a value from this list, and create a new DataFrame that only includes that utility. Note that some utilities have more than one option for "Owner," and you may want to limit this new DataFrame to a single "Owner."

* Sort the DataFrame based on the level of consumption, from most to least.

* Reset the index for the DataFrame so that the index is in order.

* Print out the details of the worst day to the screen.

## References

[SFO Airport Monthly Utility Consumption for Natural Gas, Water, and Electricity](https://data.sfgov.org/Energy-and-Environment/SFO-Airport-Monthly-Utility-Consumption-for-Natura/gcjv-3mzf).

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Import Dependencies
import pandas as pd
# Create reference to CSV file
csv_path = "Resources/SFO_Airport_Utility_Consumption.csv"

# Import the CSV into a pandas DataFrame
consumption_df = pd.read_csv(csv_path)
consumption_df



# Collect a list of all the unique values in "Utility"
consumption_df["Utility"].unique()
array(['Passengers', 'Gas', 'Electricity', 'Water'], dtype=object)
# Looking only at Electricity Consumption with "Tenant" owner
electricity_df = consumption_df.loc[(consumption_df["Utility"] == "Electricity") &
                                    (consumption_df["Owner"] == "Tenant"), :]
electricity_df.head()

# Sort the DataFrame by the values in the "Usage" column to find the worst day
electricity_df = electricity_df.sort_values("Usage", ascending=False)

# Reset the index so that the index is now based on the sorting locations
electricity_df = electricity_df.reset_index(drop=True)

electricity_df.head()

# Save all of the information collected on the worst day
worst_day = electricity_df.loc[0, :]
worst_day

 
```
{{% /expand%}}