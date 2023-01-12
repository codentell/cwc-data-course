+++
title = "10. Comic Books CSV 👩‍🎓👨‍🎓"
weight = 10
tags = ["pandas"] 
+++

In this activity, you will take a large CSV of books, read it into Jupyter Notebook by using Pandas, clean up the columns, and then write a modified DataFrame to a new CSV file.

This dataset is an expanded version of the Comic Books dataset from the British Library, which you’ve already worked with.

## Instructions

* Read in the comic books CSV by using Pandas.

* Remove unnecessary columns from the DataFrame so that only the following columns remain:

  * ISBN
  * Title
  * Other titles
  * Name
  * All names
  * Country of publication
  * Place of publication
  * Publisher
  * Date of publication

* Rename the “Name” column to “Author”, rename the “Date of publication” column to “Publication Year”, and then apply title case styling where appropriate in the remaining columns.

* Write the DataFrame into a new CSV file.

## Hint

* The base CSV file uses UTF-8 encoding. Trying to read in the file by using some other kind of encoding could introduce strange characters to the dataset. Check the tail of the dataset with `.tail()` to determine if you correctly imported the CSV file. You should be able to see characters from other languages.

## References

Data modified from "Comic books CSV" Updated April 2021. Initially released in 2014 to accompany the British Library's exhibition Comics Unmasked. [https://www.bl.uk/collection-metadata/downloads](https://www.bl.uk/collection-metadata/downloads)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Import Dependencies
import pandas as pd

# Make a reference to the comic_books_expanded.csv file path
csv_path = "./Resources/comic_books_expanded.csv"

# Import the comic_books_expanded.csv file as a DataFrame
books_df = pd.read_csv(csv_path, encoding="utf-8")
# Check the special characters imported correctly
books_df.tail()

# Remove unecessary columns from the DataFrame and save the new DataFrame
# Only keep: "ISBN", "Title", "Other titles", "Name", "All names", 
# "Country of publication", "Place of publication", "Publisher", "Date of publication"
reduced_df = books_df[["ISBN", "Title", "Other titles", "Name", "All names", 
                       "Country of publication", "Place of publication", 
                       "Publisher", "Date of publication"]]
reduced_df.head()

# Rename the headers to be more explanatory
renamed_df = reduced_df.rename(columns={"Other titles": "Other Titles",
                                        "Name": "Author",
                                        "All names": "All Names",
                                        "Country of publication": "Country of Publication",
                                        "Place of publication": "Place of Publication",
                                        "Date of publication": "Publication Year", })
renamed_df.head()

# Push the remade DataFrame to a new CSV file
renamed_df.to_csv("./output/books_clean.csv",
                  encoding="utf-8", index=False, header=True)
```
{{% /expand%}}