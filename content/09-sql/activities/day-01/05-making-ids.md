+++
title = "05. Making IDs 👩‍🎓👨‍🎓"
weight = 4
tags = ["sql"] 
+++

# Making and Using an ID

In this activity, you will recreate a table and then query, insert, and update data.

## Instructions

1. Create a new database named `programming_db`.

2. Recreate the `programming_languages` table using the following image.

    ![programming_languages.png](../images/programming_languages.png)

    | id<br>integer | language<br>character varying (20) | rating<br>integer |
    |----|----|----|
    | 1 | HTML | 95 |
    | 2 | JS | 99 |
    | 3 | JQuery | 98 |
    | 4 | MySQL | 70 |
    | 5 | MySQL | 70 |

3. Query the table to return the rows containing MySQL, and then delete one of the duplicates.

4. Insert a few more rows of data for additional programming languages by adding the `language` and `rating` of your choice to the `programming_languages` table.

5. Change the name of the JS language to JavaScript.

6. Change the rating for HTML to 90.

## Bonus

* Research how to add columns to a table. Then create a Boolean column named `expert` that has a default value of `true`.

* Start looking into the concept of joins in SQL. (This concept will be covered later in the lesson.)

---



## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Drop table if exists
DROP TABLE programming_languages;

-- Create new programming_languages table
CREATE TABLE programming_languages (
  id SERIAL PRIMARY KEY,
  language VARCHAR(20),
  rating INT
);

-- Insert new data
INSERT INTO programming_languages (language, rating)
VALUES ('HTML', 95),
	('JS', 99),
	('JQuery', 98),
	('MySQL', 70),
	('MySQL', 70);

SELECT * FROM programming_languages;

-- Query the rows with the language "MySQL"
SELECT *
FROM programming_languages
WHERE language = 'MySQL';

-- Drop a duplicate row
DELETE FROM programming_languages
WHERE id = 5;

SELECT *
FROM programming_languages;

-- Add additional data
INSERT INTO programming_languages (language, rating)
VALUES ('Python', 98),
	('C++', 73),
	('R', 95);

SELECT *
FROM programming_languages;

-- Update "JS" to "JavaScript"
UPDATE programming_languages
SET language = 'JavaScript'
WHERE id = 2;

SELECT *
FROM programming_languages;

-- Change HTML's rating to 90
UPDATE programming_languages
SET rating = 90
WHERE id = 1;

SELECT *
FROM programming_languages;

-- BONUS
-- Add a "expert" column with the boolean default of true
ALTER TABLE programming_languages
ADD COLUMN expert BOOLEAN default true;
```
{{% /expand%}}
