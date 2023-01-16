+++
title = "08. Bug Fixing Bonanza  👩‍🎓👨‍🎓"
weight = 8
tags = ["pandas"] 
+++


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

import pandas as pd
# Create a reference to the CSV and import it into a Pandas DataFrame
csv_path = "Resources/Bedbug_Reporting.csv"
bugs_df = pd.read_csv(csv_path)
bugs_df.head()

bugs_df.columns

# Remove the extra space from "Re-infested  Dwelling Unit Count" column
bugs_df = bugs_df.rename(
    columns={"Re-infested  Dwelling Unit Count": "Re-infested Dwelling Unit Count"})
# Columns we're interested in: 'Building ID', 'Borough', 'Postcode', '# of Dwelling Units',
#       'Infested Dwelling Unit Count', 'Eradicated Unit Count',
#       'Re-infested Dwelling Unit Count', 'Filing Date', 'Latitude', 'Longitude'
bugs_df = bugs_df[['Building ID', 'Borough', 'Postcode', '# of Dwelling Units',
       'Infested Dwelling Unit Count', 'Eradicated Unit Count',
       'Re-infested Dwelling Unit Count', 'Filing Date',
       'Latitude', 'Longitude']]
bugs_df.head()


# Extract the year from the date
bugs_df["Filing Date"] = bugs_df["Filing Date"].astype("datetime64")
bugs_df["Year"] = bugs_df["Filing Date"].dt.year
bugs_df.head()

bugs_df.dtypes

# Filter to only buildings with infested units greater than 0
bug_infestations = pd.DataFrame(bugs_df.loc[(bugs_df["Infested Dwelling Unit Count"]>0),:])
bug_infestations.head()

bug_infestations = bug_infestations.dropna()
bug_infestations.count()

# Change postcode to int
bug_infestations["Postcode"] = bug_infestations["Postcode"].astype("int64")
bug_infestations.head()

# Create a column for percentage of units infested
bug_infestations["Percent Units Infested"] = bug_infestations["Infested Dwelling Unit Count"] /\
                                                bug_infestations["# of Dwelling Units"] * 100
bug_infestations.head()

# Finding the average percentage of infested units
average_infested_units = bug_infestations["Percent Units Infested"].mean()
average_infested_units

# Grouping the DataFrame by "Year"
year_group = bug_infestations.groupby("Year")

# Count how many buildings were infested in each borough and create DataFrame
year_borough_df = pd.DataFrame(year_group["Borough"].value_counts())
year_borough_df.head(10)

# Rename the "Borough" column to "Total Building Infestations"
year_borough_df = year_borough_df.rename(
    columns={"Borough": "Total Building Infestations"})
year_borough_df.head()

# Create a DataFrame that shows the total infested and re-infested dwelling unit count by year and borough
year_borough_group = bug_infestations.groupby(["Year", "Borough"])
unit_infestations_by_year_borough = pd.DataFrame(year_borough_group[["Infested Dwelling Unit Count",
                                                                   "Re-infested Dwelling Unit Count"]].sum())
unit_infestations_by_year_borough

# Find the total unit infestations and re-infestations by year
total_unit_infestations_each_year = pd.DataFrame(year_group[["Infested Dwelling Unit Count", 
                                                             "Re-infested Dwelling Unit Count"]].sum())
total_unit_infestations_each_year = total_unit_infestations_each_year\
            .rename(columns={"Infested Dwelling Unit Count": "Total Infested Dwelling Units in Year",
                            "Re-infested Dwelling Unit Count": "Total Re-infested Dwelling Units in Year"})
total_unit_infestations_each_year
Total Infested Dwelling Units in Year	Total Re-infested Dwelling Units in Year

# Merge unit_infestations_by_year_borough and join the "Total Infested Dwelling Units in Year"
# into the year_borough_df DataFrame
merged_df = year_borough_df.merge(unit_infestations_by_year_borough, 
                                  on=["Year", "Borough"]).join(total_unit_infestations_each_year,
                                                               on="Year")
merged_df.head()
```
{{% /expand%}}