+++
title = "07. Hide and Seek 👩‍🎓👨‍🎓"
weight = 8
tags = ["sql"] 
+++

# Hide and Seek

In this activity, you will create a new table and import data from a CSV file. To learn more about this dataset, you may review the reference at the end of this document.

## Instructions

1. Open the `soft-attributes.csv` CSV file from the Resources folder to analyze the data.

2. Using the column headers and data types from the CSV file, write the table schema to create a new table in the `Miscellaneous_DB` database called `movie_words_comparison`.

3. Import the data from the `soft-attributes.csv` file in the Resources folder.

4. Create a query that collects all rows where `Home Alone (1990)` is in the `reference_title` column.

5. Create a query that collects all rows where the rater is within the 10-15 range.

6. Create a query that searches for the words `artsy` and `heartfelt` in the `soft_attribute` column.

## Bonus

* Create a query that will collect all rows with a reference title of `Batman (1989)` and a soft attribute of `scary`.

* Create a query that will collect all rows with a rater within the 30-40 range and has a reference title of `Home Alone (1990)` and a soft attribute of `artsy`.

## References

Krisztian Balog, Filip Radlinski and Alexandros Karatzoglou from Google LLC (2021). SoftAttributes: Relative movie attribute dataset for soft attributes. [https://github.com/google-research-datasets/soft-attributes](https://github.com/google-research-datasets/soft-attributes).

- - -


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Drop table if exists
DROP TABLE movie_words_comparison;

-- Create table and view column datatypes
CREATE TABLE movie_words_comparison (
	rater_id INT,
	reference_title VARCHAR,
	soft_attribute VARCHAR,
	less_than VARCHAR,
	about_as VARCHAR,
	more_than VARCHAR
);

SELECT * 
FROM movie_words_comparison;

-- Collect all rows where "Home Alone (1990)" is in the "reference_title" column
SELECT * 
FROM movie_words_comparison
WHERE reference_title = 'Home Alone (1990)';

-- Collect all rows where the rater is within the 10-15 range
SELECT *
FROM movie_words_comparison
WHERE
	rater_id >= 10
	AND rater_id <= 15;

-- Search for the words "artsy" and "heartfelt" in the "soft_attribute" column
SELECT *
FROM movie_words_comparison
WHERE
	soft_attribute = 'artsy'
	OR soft_attribute = 'heartfelt';

-- BONUS
-- Select all rows with a reference title of "Batman (1989)" and a soft attribute of "scary"
SELECT *
FROM movie_words_comparison
WHERE
	reference_title = 'Batman (1989)'
	AND soft_attribute = 'scary';

-- Collect all rows where the rater is within the 30-40 range and has a reference title of "Home Alone (1990)" and a soft attribute of "artsy"
SELECT *
FROM movie_words_comparison
WHERE
	reference_title = 'Home Alone (1990)'
	AND soft_attribute = 'artsy'
	AND rater_id >= 30
	AND rater_id <= 40;
```
{{% /expand%}}