+++
title = "11. Mine the Subquery 👩‍🎓👨‍🎓"
weight = 11
tags = ["sql"] 
+++

# Mine the Subqueries

In this activity, you will continue to practice subqueries. Work individually or in pairs. You can use the [ERD](http://www.postgresqltutorial.com/postgresql-sample-database/) for help with the queries.

## Instructions

* Using subqueries, identify all actors who appear in the film ALTER VICTORY in the `pagila` database.

* Using subqueries, display the titles of films that the employee Jon Stephens rented to customers.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
SELECT first_name, last_name
FROM actor
WHERE actor_id IN
(
  SELECT actor_id
  FROM film_actor
  WHERE film_id IN
  (
    SELECT film_id
    FROM film
    WHERE title = 'ALTER VICTORY'
  )
);

-- Using subqueries, display the titles of films that were rented out by an employee named Jon Stephens.

SELECT title
FROM film
WHERE film_id
IN (
  SELECT film_id
    FROM inventory
    WHERE inventory_id
    IN (
        SELECT inventory_id
        FROM rental
        WHERE staff_id
        IN (
              SELECT staff_id
              FROM staff
              WHERE last_name = 'Stephens' AND first_name = 'Jon'
            )
        )
  );
```
{{% /expand%}}