+++
title = "04. Cleaning Appliance Data 👩‍🎓👨‍🎓"
weight = 4
tags = ["pandas"] 
+++

# Hong Kong LPG Appliances

In this activity, you will take an LPG appliance dataset from Hong Kong, and clean it up so that the DataFrame is consistent and does not have any rows with missing data.

## Instructions

* Read in the CSV using Pandas, and print out the DataFrame that is returned.

  * **Note:** This dataset uses Chinese characters and should be read in using UTF-8 encoding.

* Reduce the DataFrame to only the columns in English.

* Get a count of the rows within the DataFrame to determine if there are any null values.

* Drop the rows that contain null values.

* Search through the "Applicant" column, and replace any similar values with one consistent value.

* Create a couple DataFrames that look into one Place of Manufacture only, and print them to the screen.

## References

Hong Kong Electrical and Mechanical Services Department via [data.gov.hk](https://data.gov.hk) (2022). Approved List of Domestic Gas Appliances (LP Gas). [https://data.gov.hk/en-data/dataset/hk-emsd-emsd1-domestic-gas-appliances-lpg](https://data.gov.hk/en-data/dataset/hk-emsd-emsd1-domestic-gas-appliances-lpg)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Import Dependencies
import pandas as pd
# Reference the file where the CSV is located
lpg_csv_path = "../Resources/dga_lpg.csv"

# Import the data into a Pandas DataFrame
lpg_df = pd.read_csv(lpg_csv_path, encoding="UTF-8")
lpg_df

# Reduce to columns that are in English
lpg_reduced_columns = lpg_df[["Part", "Type", "Brand", "Model", "Other Information", "Place of Manufacture", 
                              "Applicant", "Telephone Number", "Approval Expiry Date"]]
lpg_reduced_columns


# look for missing values
lpg_reduced_columns.count()

# drop null rows
no_null_lpg_df = lpg_reduced_columns.dropna(how='any')
# verify counts
no_null_lpg_df.count()

# List unique values of "Applicant" to locate any that may be the same
no_null_lpg_df["Applicant"].unique()

# Combine similar applicants together
no_null_lpg_df = no_null_lpg_df.replace(
    {"Crown Gas Stoves (Holdings) Company Limited": "Crown Gas Stoves Co., Ltd.", 
     "Sun Kee LP Gas Co.": "Sun Kee LP Gas Co. Limited"})
no_null_lpg_df

# Check to see if you combined similar applicants correctly in "Applicant"
no_null_lpg_df["Applicant"].unique()

# Create a new DataFrame that looks into a specific Place of Manufacture
malaysia_products_df = no_null_lpg_df.loc[no_null_lpg_df["Place of Manufacture"] == "Malaysia"]
malaysia_products_df

# Create a new DataFrame that looks into a specific Place of Manufacture
portugal_products_df = no_null_lpg_df.loc[no_null_lpg_df["Place of Manufacture"] == "Portugal"]
portugal_products_df

```
{{% /expand%}}