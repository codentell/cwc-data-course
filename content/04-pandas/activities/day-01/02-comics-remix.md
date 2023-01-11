+++
title = "02.  Comic Remix"
weight = 2
tags = ["pandas"] 
+++

For this activity, you will be creating a Jupyter notebook that performs the same functions as the Comic Book activity from last week.

## Instructions

* Using `comicbooks.py` as a starting point, convert the application so that it runs properly within a Jupyter Notebook.

* Have the application print out the user's input, the path to `comic_books.csv`, and the publisher/date published for the book in different cells.

## Bonus

* Go through any of the activities from last week, and attempt to convert them to run within a Jupyter Notebook. As you go, try to split up the code into cells and print out the outputs.

## References

Data modified from "Comic books CSV" Updated April 2021. Initially released in 2014 to accompany the British Library's exhibition Comics Unmasked. [https://www.bl.uk/collection-metadata/downloads](https://www.bl.uk/collection-metadata/downloads)

—


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Modules
import os
import csv
# Prompt user for video lookup
book = input("What title are you looking for? ")
# Set path for file
csvpath = os.path.join("Resources", "comic_books.csv")
print(csvpath)

# Set variable to check if we found the video
found = False
Resources\comic_books.csv

# Open the CSV
with open(csvpath, encoding="utf8") as csvfile:
    csvreader = csv.reader(csvfile, delimiter=",")

    # Loop through looking for the video
    for row in csvreader:
        if row[0] == book:
            print(row[0] + " was published by " + row[8] + " in " + row[9])

            # Set variable to confirm we have found the video
            found = True

    # If the video is never found, alert the user
    if found == False:
        print("We don't seem to have what you are looking for!")
AWOL was published by Image Comics in 2007-2009
 
```
{{% /expand%}}