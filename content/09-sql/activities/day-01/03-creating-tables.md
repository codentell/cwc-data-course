+++
title = "03. Creating Tables 👩‍🎓👨‍🎓"
weight = 4
tags = ["sql"] 
+++

In this activity, you will use pgAdmin to recreate and query a table based on an image provided to you.

## Instructions

1. Create a new database in pgAdmin named `city_info`.

2. Using the query tool, create an empty table named `cities`. Be sure to match the data types!

3. Insert data into the new table. The result should match the following image.

    ![cities_table.png](./images/cities_table.png)

    | city<br>character varying (30) | state<br>character varying (30) | population<br>integer |
    |----|----|----|
    | Alameda | California | 79177 |
    | Mesa | Arizona | 496401 |
    | Boerne | Texas | 16056 |
    | Anaheim | California | 352497 |
    | Tucson | Arizona | 535677 |
    | Garland | Texas | 238002 |

4. Query the table to recreate the image below.

    ![cities_only.png](./images/cities_only.png)

    | city<br>character varying (30) |
    |----|
    | Alameda |
    | Mesa |
    | Boerne |
    | Anaheim |
    | Tucson |
    | Garland |

## Bonus

1. Filter the table to view only cities in Arizona.

2. Filter the table to view only cities with a population of less than 100,000.

3. Filter the table to view California cities with a population of less than 100,000.

## Hints

* For the second bonus question, you will need to use a [`WHERE` clause](https://www.tutorialspoint.com/sql/sql-where-clause.htm) to filter the original query.

* For the third bonus question, an [`AND` clause](https://www.tutorialspoint.com/sql/sql-and-or-clauses.htm) will also be necessary.

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Create a new table
CREATE TABLE cities (
  city VARCHAR(30) NOT NULL,
  state VARCHAR(30) NOT NULL,
  population INT
);

-- Insert data into the table
INSERT INTO cities (city, state, population)
VALUES ('Alameda', 'California', 79177),
  ('Mesa', 'Arizona', 496401),
  ('Boerne', 'Texas', 16056),
  ('Anaheim', 'California', 352497),
  ('Tucson', 'Arizona', 535677),
  ('Garland', 'Texas', 238002);

-- View the table data
SELECT *
FROM cities;

-- Use a query to view only the cities
SELECT city
FROM cities;

-- Bonus 1:
-- Create a query to view cities in Arizona
SELECT city, state
FROM cities
WHERE state = 'Arizona';

-- Bonus 2:
-- Create a query to view cities and states
-- with a population less than 100,000
SELECT *
FROM cities
WHERE population < 100000;

-- Bonus 3:
-- Create a query to view the city in California
-- with a population of less than 100,000
SELECT *
FROM cities
WHERE population < 100000
AND state = 'California';
```
{{% /expand%}}