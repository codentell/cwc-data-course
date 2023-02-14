+++
title = "11. Unions 👩‍🎓👨‍🎓"
weight = 11
tags = ["sql"] 
+++

In this activity, you will practice unions by combining data from tables without the use of joins.

## Instructions

* Using `UNION`, write a PostgreSQL statement to query the number of rows in tables `city` and `country`.

* Use `UNION` to display from the tables `customer` and `customer_list` the ID of all customers who live in the city of London. Determine whether both tables contain the same customers by using `UNION ALL`.

## Hint

For the second task, consider using subqueries.

---



## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Question 1

SELECT COUNT(*)
FROM city
UNION
SELECT COUNT(*)
FROM country;


-- Question 2

SELECT customer_id
FROM customer
WHERE address_id IN
(
  SELECT address_id
  FROM address
  WHERE city_id IN
  (
    SELECT city_id
    FROM city
    WHERE city = 'London'
  )
)
UNION ALL
SELECT id
FROM customer_list
WHERE city = 'London';
```
{{% /expand%}}