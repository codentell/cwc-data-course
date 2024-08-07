+++
title = "05. Pandas Recap 👩‍🏫🧑‍🏫"
weight = 5
tags = ["pandas"] 
+++

# Pandas Recap and Data Types

In this activity, we will recap what we have learned about Pandas up to this point.

## Instructions

* Open ‘PandasRecap.ipynb’ under the ‘unsolved’ folder in your Jupyter notebook.

* Go through the cells, and follow the instructions in the comments.

## Hints

* A list of a DataFrame's data types can be checked by accessing its `dtypes` property.

* To change a non-numeric column to a numeric column, use the `df.astype(<datatype>)` method and pass in the desired data type as the parameter.

## References

National Fire Incident Reporting System (NFIRS). Connecticut Fire Department Incidents (2012-2016). [https://data.ct.gov/Public-Safety/Connecticut-Fire-Department-Incidents-2012-2016-/qem9-rt8k](https://data.ct.gov/Public-Safety/Connecticut-Fire-Department-Incidents-2012-2016-/qem9-rt8k), reduced in Pandas.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Import the Pandas library
import pandas as pd
# Create a reference the CSV file desired
csv_path = "Resources/CT_fires_2015.csv"

# Read the CSV into a Pandas DataFrame
fires_df = pd.read_csv(csv_path)

# Print the first five rows of data to the screen
fires_df.head()

# Check the names of all the columns and see if there are any rows with missing data
fires_df.count()

# Rename mistyped columns "Aid Given or Received Code " and "Propery Loss"
fires_df = fires_df.rename(columns={"Aid Given or Received Code ": "Aid Given or Received Code", 
                                    "Propery Loss": "Property Loss"})
# Reduce to columns: Reporting Year, Fire Department Name, Incident date, Incident Type,
# Aid Given or Received Code, Aid Given or Received, Number of Alarms, Alarm Date and Time,
# Arrival Date and Time, Last Unit Cleared Date and Time, Actions Taken 1, Actions Taken 2,
# Actions Taken 3, Property Value, Property Loss, Contents Value, Contents Loss,
# Fire Service Deaths, Fire Service Injuries, Other Fire Deaths, Other Fire Injuries,
# Property Use, Incident Street Address, Incident Apartment Number, Incident City, Incident Zip Code

fires_reduced = fires_df[["Reporting Year", "Fire Department Name", "Incident date", 
                          "Incident Type", "Aid Given or Received Code", "Aid Given or Received", 
                          "Number of Alarms", "Alarm Date and Time", "Arrival Date and Time", 
                          "Last Unit Cleared Date and Time", "Actions Taken 1", 
                          "Actions Taken 2", "Actions Taken 3", "Property Value", 
                          "Property Loss", "Contents Value", "Contents Loss", "Fire Service Deaths", 
                          "Fire Service Injuries", "Other Fire Deaths", "Other Fire Injuries", 
                          "Property Use", "Incident Street Address", "Incident Apartment Number", 
                          "Incident City", "Incident Zip Code"]]
fires_reduced.head()

# Fill NAs for columns "Actions Taken 1", "Actions Taken 2", "Actions Taken 3", 
# and "Incident Apartment Number" with ''
# Fill NAs for columns "Other Fire Deaths", "Other Fire Injuries",
# "Property Loss", and "Contents Loss" with 0
fires_reduced = fires_reduced.fillna({"Actions Taken 1": '', 
                                      "Actions Taken 2": '', 
                                      "Actions Taken 3": '',
                                      "Incident Apartment Number": '',
                                      "Other Fire Deaths": 0,
                                      "Other Fire Injuries": 0,
                                      "Property Loss": 0,
                                      "Contents Loss": 0})
fires_reduced.head()


# Remove remaining rows with missing data
fires_cleaned_df = fires_reduced.dropna(how="any")
fires_cleaned_df.count()

# Filter data to incidents that caused Property or Contents Loss
loss_df = fires_cleaned_df.loc[(fires_cleaned_df["Property Loss"] > 0) |
                               (fires_cleaned_df["Contents Loss"] > 0) , :]
loss_df.head()

# Count how many incidents occured in each city
city_counts = loss_df["Incident City"].value_counts()

# Convert the city_counts Series into a DataFrame
city_loss_counts_df = pd.DataFrame(city_counts)
city_loss_counts_df.head()

# Convert the column name into "Sum of Loss Incidents"
city_loss_counts_df = city_loss_counts_df.rename(
    columns={"Incident City": "Sum of Loss Incidents"})
city_loss_counts_df.head()

# Calculate the number of deaths from fire incidents where loss occurred
deaths = loss_df["Fire Service Deaths"].sum() + loss_df["Other Fire Deaths"].sum()
deaths

# Want to calculate the fire department response time? There is a problem
# Problem can be seen by examining datatypes within the DataFrame
loss_df.dtypes

# Convert relevant date columns to datetime
loss_df = loss_df.astype({"Alarm Date and Time": "datetime64",
                         "Arrival Date and Time": "datetime64",
                         "Last Unit Cleared Date and Time": "datetime64"})
loss_df.dtypes

# Now it is possible to find the response time in seconds
# Hint: create a new column for "Response Time (seconds)" and use .dt.total_seconds()
# to calculate the seconds
loss_df["Response Time (seconds)"] = loss_df["Arrival Date and Time"] - loss_df["Alarm Date and Time"]
loss_df["Response Time (seconds)"] = loss_df["Response Time (seconds)"].dt.total_seconds()
loss_df["Response Time (seconds)"] = loss_df["Response Time (seconds)"].astype("int")
# Check data for columns of your choosing
response_times = loss_df[["Fire Department Name", "Incident date", "Incident Type", "Arrival Date and Time",
        "Alarm Date and Time", "Response Time (seconds)"]]
response_times.head() 
```
{{% /expand%}}