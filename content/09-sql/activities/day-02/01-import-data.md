+++
title = "01. Import Data 👩‍🎓👨‍🎓"
weight = 1
tags = ["sql"] 
+++

### Option 1 copy csv to sql table command

```sql
COPY actor FROM '<path to actor.csv>' DELIMITER ',' CSV HEADER;
COPY address FROM '<path to actor.csv>' DELIMITER ',' CSV HEADER;
COPY city FROM '<path to city.csv>' DELIMITER ',' CSV HEADER;
COPY country FROM '<path to country.csv>' DELIMITER ',' CSV HEADER;
COPY customer_list FROM '<path to customer_list.csv>' DELIMITER ',' CSV HEADER;
COPY customer FROM '<path to customer.csv>' DELIMITER ',' CSV HEADER;
COPY film_actor FROM '<path to film_actor.csv>' DELIMITER ',' CSV HEADER;
COPY film FROM '<path to film.csv>' DELIMITER ',' CSV HEADER;
COPY inventory FROM '<path to inventory.csv>' DELIMITER ',' CSV HEADER;
COPY payment FROM '<path to payment.csv>' DELIMITER ',' CSV HEADER;
COPY rental FROM '<path to rental.csv>' DELIMITER ',' CSV HEADER;
COPY staff FROM '<path to staff.csv>' DELIMITER ',' CSV HEADER;
COPY store FROM '<path to store.csv>' DELIMITER ',' CSV HEADER;
```

### Option 2 copy the pagila-insert-data.sql file in resources and run to get all the data

### Option 3 right click import csv one by one
