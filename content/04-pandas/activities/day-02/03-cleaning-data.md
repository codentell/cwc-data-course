+++
title = "03.  Cleaning Data 👩‍🏫🧑‍🏫"
weight = 3
tags = ["pandas"] 
+++

```python
# Dependencies
import pandas as pd
# Name of the CSV file
file = 'resources/donors2021_unclean.csv'
# The correct encoding must be used to read the CSV in pandas
df = pd.read_csv(file, encoding="ISO-8859-1")
# Preview of the DataFrame
# Note that Memo_CD is likely a meaningless column
df.head()

# Delete extraneous column
del df['Memo_CD']
df.head()

# Identify incomplete rows
df.count()

# Drop all rows with missing information
df = df.dropna(how='any')
# Verify dropped rows
df.count()

# The Zip column is the wrong data type. It should be a string (object).
df.dtypes

# Use df.astype() method to convert the datatype of the Zip column
df = df.astype({"Zip": str}, errors='raise')
# Verify that the Zip column datatype has been made an object
df['Zip'].dtype

# Display an overview of the Employers column
df['Employer'].value_counts()

# Clean up Employer category. Replace 'SELF' and 'SELF EMPLOYED' with 'SELF-EMPLOYED'
df['Employer'] = df['Employer'].replace({'SELF': 'SELF-EMPLOYED', 'SELF EMPLOYED': 'SELF-EMPLOYED'})
# Verify clean-up.
df['Employer'].value_counts()

df['Employer'] = df['Employer'].replace({'NOT EMPLOYED': 'UNEMPLOYED'})
df['Employer'].value_counts()


# Display a statistical overview
# We can infer the maximum allowable individual contribution from 'max'
df.describe()

df.to_csv("./resources/donors2021.csv", index=False, encoding="ISO-8859-1")

```