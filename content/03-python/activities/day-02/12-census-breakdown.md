+++
title = "12. Census Breakdown  👩‍🎓👨‍🎓"
weight = 12
tags = ["python"] 
+++

In this activity, you will be provided with a large dataset from the 2019 U.S. Census. Your task is to clean up this dataset and create a new CSV file that is easier to comprehend.

## Instructions

* Create a Python application that reads in the data from the 2019 U.S. Census.

* Then, store the contents of `Place`, `Population`, `Per Capita Income`, and `Poverty Count` into Python Lists.

* Then, zip these lists together into a single tuple.

* Finally, write the contents of your extracted data into a CSV. Make sure to include the titles of these columns in your CSV.

## Bonus

* Find the poverty rate (percentage of population living in poverty). Include this in your final output, converting the rate to a string and including a "%" at the end of the string.

* Parse the string associated with `Place`, separating it into `County` and `State`, so we can store both in separate columns.

## Hints

* Windows users may get a `UnicodeDecodeError`. To avoid this, pass in `encoding="utf8"` as an additional parameter when reading in the file.

* As with many datasets, the file does not include the header line. Use the following list as a guide to the columns: "Place,Population,Median Age,Household Income,Per Capita Income,Employed Civilians,Unemployed Civilians,People in the Military,Poverty Count"

## References

Data Source: [U.S. Census API - ACS 5-Year Estimates 2019](https://www.census.gov/data/developers/data-sets/census-microdata-api.ACS_5-Year_PUMS.html)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
import os
import csv

census_csv = os.path.join(".", "Resources", "census_starter.csv")

# Lists to store data
place = []
population = []
income = []
poverty_count = []
poverty_rate = []
county = []
state = []

# with open(udemy_csv, encoding='utf-8') as csvfile:
with open(census_csv) as csvfile:
    csvreader = csv.reader(csvfile, delimiter=",")
    for row in csvreader:
        # Add place
        place.append(row[0])

        # Add population
        population.append(row[1])

        # Add per capita income
        income.append(row[4])

        # Add poverty count
        poverty_count.append(row[8])

        # Determine poverty rate to 2 decimal places, convert to string
        percent = round(int(row[8]) / int(row[1]) * 100, 2)
        poverty_rate.append(str(percent) + "%")

        # Split the place into county and state
        split_place = row[0].split(", ")
        county.append(split_place[0])
        state.append(split_place[1])

# Zip lists together
cleaned_csv = zip(place, population, income, poverty_count, poverty_rate, county, state)

# Set variable for output file
output_file = os.path.join("./output/census_final.csv")

#  Open the output file
with open(output_file, "w") as datafile:
    writer = csv.writer(datafile)

    # Write the header row
    writer.writerow(["Place", "Population", "Per Capita Income", "Poverty Count", "Poverty Rate",
                    "County", "State"])

    # Write in zipped rows
    writer.writerows(cleaned_csv)
```
{{% /expand%}}