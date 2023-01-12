+++
title = "06.  Group By 👩‍🏫🧑‍🏫"
weight = 6
tags = ["pandas"] 
+++

```python

# Import the Pandas library
import pandas as pd
# Create a reference the CSV file desired
csv_path = "Resources/CT_fires_2015.csv"

# Read the CSV into a Pandas DataFrame
fires_df = pd.read_csv(csv_path)

# Print the first five rows of data to the screen
fires_df.head()

	
# Rename mistyped columns "Propery Loss"
fires_df = fires_df.rename(columns={"Propery Loss": "Property Loss"})

# Reduce to columns: Fire Department Name, Incident date, Incident Type Code, Incident Type,
# Alarm Date and Time, Arrival Date and Time, Last Unit Cleared Date and Time, 
# Property Loss, Contents Loss, Fire Service Deaths, Fire Service Injuries, 
# Other Fire Deaths, Other Fire Injuries, Incident City, Incident Zip Code

fires_reduced = fires_df[["Fire Department Name", "Incident date", "Incident Type Code",
                          "Incident Type", "Alarm Date and Time", "Arrival Date and Time", 
                          "Last Unit Cleared Date and Time", "Property Loss", "Contents Loss", 
                          "Fire Service Deaths", "Fire Service Injuries", "Other Fire Deaths", 
                          "Other Fire Injuries", "Incident City", "Incident Zip Code"]]
fires_reduced.head()

# The columns we selected with missing data are all numbers, so we can fill NAs with 0
fires_cleaned_df = fires_reduced.fillna(0)
fires_cleaned_df.count()

# Convert relevant date columns to datetime
converted_fires_df = fires_cleaned_df.copy()
converted_fires_df = converted_fires_df.astype({"Alarm Date and Time": "datetime64",
                                      "Arrival Date and Time": "datetime64",
                                      "Last Unit Cleared Date and Time": "datetime64"})
converted_fires_df.head()

# Create a new column for "Response Time (seconds)" and calculate
converted_fires_df["Response Time (seconds)"] = converted_fires_df["Arrival Date and Time"] - converted_fires_df["Alarm Date and Time"]
converted_fires_df["Response Time (seconds)"] = converted_fires_df["Response Time (seconds)"].dt.total_seconds()
converted_fires_df["Response Time (seconds)"] = converted_fires_df["Response Time (seconds)"].astype("int")

# Create a new column for "Incident Duration (seconds)" and calculate
converted_fires_df["Incident Duration (seconds)"] = converted_fires_df["Last Unit Cleared Date and Time"] - converted_fires_df["Alarm Date and Time"]
converted_fires_df["Incident Duration (seconds)"] = converted_fires_df["Incident Duration (seconds)"].dt.total_seconds()
converted_fires_df["Incident Duration (seconds)"] = converted_fires_df["Incident Duration (seconds)"].astype("int")

converted_fires_df.head(10)

# Count how many total incidents have occured within each city
city_counts = converted_fires_df["Incident City"].value_counts()
city_counts.head()

# Some cities have a lot of incidents
# Let's filter the data to only incidents of loss
loss_df = converted_fires_df.loc[(fires_reduced["Property Loss"] > 0) | 
                    (fires_reduced["Contents Loss"] > 0),:]
loss_df.head()

# Count how many loss incidents have occured in each city
city_loss_counts = loss_df["Incident City"].value_counts()
city_loss_counts.head()

# Count how many loss incidents occured in each city
grouped_city_df = loss_df.groupby(["Incident City"])

print(grouped_city_df)

grouped_city_df.count().head(10)
						
grouped_city_df[["Property Loss", "Contents Loss"]].sum()


# Save loss sums as series
city_property_loss = grouped_city_df["Property Loss"].sum()
city_contents_loss = grouped_city_df["Contents Loss"].sum()
city_contents_loss.head()

# Create a new DataFrame using count and loss amounts
city_summary_df = pd.DataFrame({"Number of Loss Incidents": city_loss_counts,
                                "Total Property Loss": city_property_loss,
                               "Total Contents Loss": city_contents_loss})
city_summary_df.head()

# It is also possible to group a DataFrame by multiple columns
# This returns an object with multiple indexes, however, which can be harder to deal with
grouped_city_loss_incidents = loss_df.groupby(["Incident City","Incident Type Code"])

grouped_city_loss_incidents.count().head(10)

# Converting a GroupBy object into a DataFrame
total_city_loss_df = pd.DataFrame(
    grouped_city_loss_incidents[["Property Loss", "Contents Loss"]].sum())
total_city_loss_df.head(10)

#GroupBy is also useful for situations where you may want to calculate the average
incident_time_df = converted_fires_df[["Incident City","Response Time (seconds)", "Incident Duration (seconds)"]]
incident_time_df.groupby(["Incident City"]).mean().head(10)

 

```