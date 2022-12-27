+++
title = "09. Reading Comic Book  👩‍🎓👨‍🎓"
weight = 9
tags = ["python"] 
+++


In this activity, you will create an application that searches the provided CSV file for a specific graphic novel title and then returns the title, publisher’s name, and the year it was published.

## Instructions

* Prompt the user for the book title they’d like to search.

* Search through the `comic_books.csv` to find the user's book.

* If the CSV contains the user's title, then print out the title, the publisher name, and the year it was published.

  * For example: `"Alien was published by DC Comics in 2015"`.

* If the CSV does not contain the user's title, then print out a message telling them that their book could not be found.

    * Set a variable to `False` to check if we found the comic book.

    * In the `for` loop, change the variable to confirm that the comic book is found.

## References

Data modified from "Comic books CSV" Updated April 2021. Initially released in 2014 to accompany the British Library's exhibition Comics Unmasked. [https://www.bl.uk/collection-metadata/downloads](https://www.bl.uk/collection-metadata/downloads)

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
# Modules
import os
import csv

# Prompt user for title lookup
book = input("What title are you looking for? ")

# Set path for file
csvpath = os.path.join(".", "Resources", "comic_books.csv")

# Set variable to check if we found the video
found = False

# Open the CSV
with open(csvpath, encoding='utf') as csvfile:
    csvreader = csv.reader(csvfile, delimiter=",")

    # Loop through looking for the video
    for row in csvreader:
        # print(row)
        if row[0] == book:
            print(row[0] + " was published by " + row[8] + " in " + row[9])

            # Set variable to confirm we have found the video
            found = True


    # If the book is never found, alert the user
    if found is False:
        print("Sorry about this, we don't seem to have what you are looking for!")     
```


{{% /expand%}}

