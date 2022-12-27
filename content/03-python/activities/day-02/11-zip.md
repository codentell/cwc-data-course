+++
title = "11 Zip 👩‍🏫🧑‍🏫"
weight = 11
tags = ["python"] 
+++


```python
import csv
import os

# Three Lists
indexes = [1, 2, 3, 4]
employees = ["Michael", "Dwight", "Meredith", "Kelly"]
department = ["Boss", "Sales", "Sales", "HR"]

# Zip all three lists together into tuples
roster = zip(indexes, employees, department)
print(roster)

# Print the contents of each row
for employee in roster:
    print(employee)

# save the output file path
output_file = os.path.join("./output/activity-11-output.csv")

# open the output file, create a header row, and then write the zipped object to the csv
with open(output_file, "w") as datafile:
    writer = csv.writer(datafile)

    writer.writerow(["Index", "Employee", "Department"])

    writer.writerows(roster)

# Zip all three lists together into tuples
# NOTE WHEN ZIPPING data it will only store once 
# SO BELOW THIS COMMENT
# IS WHY WE DECLARE the variable called roster again 
# in order to print and view

roster = zip(indexes, employees, department)
# to print out to terminal:
#comment out above code and run the code below
for employee in roster:
    print(employee)

```