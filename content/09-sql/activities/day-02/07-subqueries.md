+++
title = "07. Subqueries 👩‍🎓👨‍🎓"
weight = 7
tags = ["sql"] 
+++

# Subqueries

In this activity, you will practice creating subqueries.

## Instructions

* List the names and ID numbers of cities that are in the following list: `Qalyub`, `Qinhuangdao`, `Qomsheh`, `Quilmes`.

* Display the districts in the above list of cities.

   **Hint:** Use the `address` and `city` tables.

## Bonus

Using subqueries, find the first and last names of customers who reside in cities that begin with the letter *Q*.

  **Hint:** You will need to use three tables and more than one subquery.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
-- Question 1

SELECT city, city_id
FROM city
WHERE city IN ('Qalyub', 'Qinhuangdao', 'Qomsheh', 'Quilmes');


-- Question 2

SELECT district
FROM address
WHERE city_id IN
(
  SELECT city_id
  FROM city
  WHERE city IN ('Qalyub', 'Qinhuangdao', 'Qomsheh', 'Quilmes')
);


-- Bonus

SELECT first_name, last_name
FROM customer cus
WHERE address_id IN
(
  SELECT address_id
  FROM address a
  WHERE city_id IN
  (
    SELECT city_id
    FROM city
    WHERE city LIKE 'Q%'
  )
);

```
{{% /expand%}}