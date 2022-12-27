+++
title = "01. Cereal Cleaner 👩‍🎓👨‍🎓"
weight = 1
tags = ["python"] 
+++

In this activity, you will create an application that reads in cereal data from a CSV file and then prints only those cereals that contain 5 or more grams of fiber.

## Instructions

* Read the file using the code in the notebook, `cereal.csv` and start by skipping the header row. See hints below for this.

* Read through the remaining rows and find the cereals that contain five grams of fiber or more, printing the data from those rows to the terminal.

## Hints

* Every value within the csv is stored as a string, and certain values have a decimal. This means that they will have to be cast to be used.

* `csv.reader` begins reading the CSV file from the first row. `next(csv_reader, None)` will skip the header row.

  * Refer to this Stack Overflow post on [how to skip the header](https://stackoverflow.com/a/14257599) for more information.

* Integers in Python are whole numbers and, as such, cannot contain decimals. Decimal numbers As such, your numbers containing decimal points will have to be cast as a `float`.

## Bonus

Try the activity again, but this time use `cereal_bonus.csv`, which does not include a header.

## References

Crawford, C. (2017, October 24). 80 cereals. [https://www.kaggle.com/crawford/80-cereals](https://www.kaggle.com/crawford/80-cereals), originally sourced from [http://lib.stat.cmu.edu/datasets/1993.expo/](http://lib.stat.cmu.edu/datasets/1993.expo/)

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
import os
import csv

cereal_csv = os.path.join(".", "Resources", "cereal.csv")

# Open and read csv
with open(cereal_csv) as csv_file:
    csv_reader = csv.reader(csv_file, delimiter=",")

    # Read the header row first (skip this part if there is no header)
    csv_header = next(csv_file)
    print(f"Header: {csv_header}")

    # Read through each row of data after the header
    for row in csv_reader:

        # Convert row to float and compare to grams of fiber
        if float(row[7]) >= 5:
            print(row)          
```


{{% /expand%}}


## ✅ Bonus Solutions
{{%expand "Solutions Click Here" %}}

```python
import os
import csv

cereal_csv = os.path.join(".", "Resources", "cereal_bonus.csv")

with open(cereal_csv) as csvfile:
    csv_reader = csv.reader(csvfile, delimiter=",")

    # @NOTE: This time, we do not use `next(csv_reader)` because there is no header for this file

    # Read through each row of data after the header
    for row in csv_reader:

        # Convert row to float and compare to grams of fiber
        if float(row[7]) >= 5:
            print(row)
```

{{% /expand%}}