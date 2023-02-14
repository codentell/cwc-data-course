+++
title = "08. Designing ERD 👩‍🎓👨‍🎓"
weight = 8
tags = ["sql"] 
+++

# Designing an ERD, Part 1

In this activity, you will work on the following scenario with a partner:

You are meeting with a gym owner who wants to organize his data in a database. This will require creating a conceptual ERD for the owner.

## Instructions

* Create a conceptual ERD by determining the entities and their attributes that will exist in the database. Be sure to include the following: `trainers`, `members`, and `gym` as well as one more entity that you think is necessary.

* Create a diagram using the [Quick Database Diagrams](https://app.quickdatabasediagrams.com/#/) tool.

* When you are satisfied with the conceptual diagram, update it to a logical ERD by including column data types and primary keys.

* Update your existing diagram to reflect the changes.

## Hint

Read this [documentation](https://www.visual-paradigm.com/support/documents/vpuserguide/3563/3564/85378_conceptual,l.html) for more in-depth explanations of entity relationship diagrams.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
Gym
-
ID INTEGER PK
Gym_Name VARCHAR
Address VARCHAR
City VARCHAR
Zipcode VARCHAR

Trainers
-
ID INTEGER PK
First_Name VARCHAR
Last_Name VARCHAR

Members
-
ID INTEGER PK
First_Name VARCHAR
Last_Name VARCHAR
Address VARCHAR
City VARCHAR

Payments
-
ID INTEGER PK
CreditCard_Info INTEGER
Billing_Zip INTEGER
```
{{% /expand%}}

