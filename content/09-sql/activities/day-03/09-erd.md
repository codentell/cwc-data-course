+++
title = "09. ERD Part 2 👩‍🎓👨‍🎓"
weight = 9
tags = ["sql"] 
+++

# Designing an ERD, Part 2

In this activity, you and your partner will continue designing an entity relationship diagram for the gym by transitioning your logical ERD (created in the previous activity) to a physical ERD.

## Instructions

1. Using the starter code provided, return to [Quick Database Diagrams](https://app.quickdatabasediagrams.com/#/) and transition your logical ERD to a physical ERD by creating the relationships between tables.

2. When you are satisfied with your ERD, write a corresponding schema file containing your `CREATE TABLE` statements

3. In pgAdmin, connect to your server and create a new database named `gym`. Then open a query tool.

4. Paste the code from your schema file in pgAdmin, and then execute the code.

## Hint

* Foreign keys are added to each table represented by the `FK` acronym, which is followed by the relationship, e.g., `OrderID INT FK >- Order.OrderID`.

* You will need to add foreign keys to your tables in order to map the data relationships.

* Remember to document the relationships between entities using the correct symbols. Here are the allowed relationship types:

  ```
  -	- one TO one
  -<	- one TO many
  >-<	- many TO many
  -0	- one TO zero or one
  0-	- zero or one TO one
  0-0	- zero or one TO zero or one
  -0<	- one TO zero or many
  >0-	- zero or many TO one
  ```

* Keep in mind the following:

  * Each member belongs to only one gym.

  * Trainers work for only one gym, but a gym has many trainers.

  * Each member must have a trainer, but each trainer may instruct multiple members.

  * Each member has one credit card on file.

* Once you have created tables in pgAdmin, you can check the table creation with the following syntax:

  ```sql
  SELECT * FROM Members;
  ```

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```sql
CREATE TABLE Gym (
    Gym_ID INTEGER   NOT NULL,
    Gym_Name VARCHAR   NOT NULL,
    Address VARCHAR   NOT NULL,
    City VARCHAR   NOT NULL,
    Zipcode VARCHAR   NOT NULL,
    PRIMARY KEY (Gym_ID)
);

CREATE TABLE Trainers (
    Trainer_ID INTEGER   NOT NULL,
    Gym_ID INTEGER   NOT NULL,
    First_Name VARCHAR   NOT NULL,
    Last_Name VARCHAR   NOT NULL,
    PRIMARY KEY (Trainer_ID)
    FOREIGN KEY(Gym_ID) REFERENCES Gym (Gym_ID);
);

CREATE TABLE Members (
    Member_ID INTEGER   NOT NULL,
    Gym_ID INTEGER   NOT NULL,
    Trainer_ID INTEGER   NOT NULL,
    First_Name VARCHAR   NOT NULL,
    Last_Name VARCHAR   NOT NULL,
    Address VARCHAR   NOT NULL,
    CITY VARCHAR   NOT NULL,
    PRIMARY KEY (Member_ID)
    FOREIGN KEY(Gym_ID) REFERENCES Gym (Gym_ID);
    FOREIGN KEY(Trainer_ID) REFERENCES Trainers (Trainer_ID);
);

CREATE TABLE Payments (
    Payment_ID INTEGER   NOT NULL,
    Member_ID INTEGER   NOT NULL,
    CreditCard_Info INTEGER   NOT NULL,
    Billing_Zip INTEGER   NOT NULL,
    PRIMARY KEY (Payment_ID)
    FOREIGN KEY(Member_ID) REFERENCES Members (Member_ID);
);
```

```
Gym
-
Gym_ID INTEGER PK
Gym_Name VARCHAR
Address VARCHAR
City VARCHAR
Zipcode VARCHAR

Trainers
-
Trainer_ID INTEGER PK
Gym_ID INTEGER FK >- Gym.Gym_ID
First_Name VARCHAR
Last_Name VARCHAR

Members
-
Member_ID INTEGER PK
Gym_ID INTEGER FK >- Gym.Gym_ID
Trainer_ID INTEGER FK >- Trainers.Trainer_ID
First_Name VARCHAR
Last_Name VARCHAR
Address VARCHAR
CITY VARCHAR

Payments
-
Payment_ID INTEGER PK
Member_ID INTEGER FK - Members.Member_ID
CreditCard_Info INTEGER
Billing_Zip INTEGER
```
{{% /expand%}}