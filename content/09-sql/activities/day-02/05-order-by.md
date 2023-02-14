+++
title = "05. Order By  👩‍🎓👨‍🎓"
weight = 5
tags = ["sql"] 
+++


# Movies Ordered By

In this activity, you will use `ORDER BY` in combination with other SQL methods to query and order the tables.

## Instructions

* Determine the count of actor first names with the names ordered in descending order.

* Determine the average rental duration for each rating rounded to two decimals. Order these in ascending order.

* Determine the top 10 average replacement costs for movies, ordered by their length.

## Bonus

Using the city and country tables, determine the count of countries in descending order.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Select count of actors first names in descending order
SELECT first_name, COUNT(first_name) AS "actor count"
FROM actor
GROUP BY first_name
ORDER BY "actor count" DESC;

-- Select the average duration of movies by rating
SELECT rating, ROUND(AVG(rental_duration),2) AS "avg duration"
FROM film
GROUP BY rating
ORDER BY "avg duration";

-- Select top ten replace costs for the length of the movie
SELECT length, ROUND(AVG(replacement_cost)) AS "avg cost"
FROM film
GROUP BY length
ORDER BY "avg cost" DESC
LIMIT 10;

-- Select the count of countries
SELECT country.country, COUNT(country.country) AS "country count"
FROM city
JOIN country ON city.country_id = country.country_id
GROUP BY country.country
ORDER BY "country count" DESC;
```
{{% /expand%}}

