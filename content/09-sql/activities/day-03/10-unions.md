+++
title = "10. Unions 👩‍🏫🧑‍🏫"
weight = 10
tags = ["sql"] 
+++

### schema.sql
```sql
DROP TABLE IF EXISTS toys;
DROP TABLE IF EXISTS games;

CREATE TABLE toys (
    toy_id SERIAL,
    type VARCHAR,
    name VARCHAR
);

CREATE TABLE games (
    game_id SERIAL,
    type VARCHAR,
    name VARCHAR
);

INSERT INTO toys (type, name)
VALUES
('sports', 'baseball'),
('adventure', 'staff'),
('sports', 'tennis ball'),
('fun', 'doll');

INSERT INTO games (type, name)
VALUES
('sports', 'tag'),
('adventure', 'Kings Quest'),
('sports', 'tennis'),
('fun', 'Make believe');
```

### query.sql
```sql
-- Two queries for for actors and customer
-- Union of customers
SELECT actor_id AS id, first_name
FROM actor
WHERE actor_id between 1 and 5;

SELECT customer_id AS id, first_name
FROM customer
WHERE customer_id between 6 and 10;

-- Union of customers
SELECT actor_id AS id, first_name
FROM actor
WHERE actor_id between 1 and 5

UNION

SELECT customer_id AS id, first_name
FROM customer
WHERE customer_id between 6 and 10;

-- Two separte queries for toys and games
SELECT toy_id AS id, type
FROM toys;

SELECT game_id AS id, type
FROM games;

-- Union of toys and game types
SELECT toy_id AS id, type
FROM toys

UNION

SELECT game_id AS id, type
FROM games;

-- Include duplicate rows
SELECT toy_id AS id, type
FROM toys

UNION ALL

SELECT game_id AS id, type
FROM games;
```