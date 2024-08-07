+++
title = "07. ERD 👩‍🏫🧑‍🏫"
weight = 7
tags = ["sql"] 
+++

# Conceptual Schema
```
# Conceptual (without relationships)

Employee
-

Zipcode
-

Employee_Email
-

Owners
-

Estates
-

Estate_Type
-

Agents
-

Regions
-

Agent_Region_Junction
-

# Conceptual (with relationships)

Employee
rel Zipcode
-

Zipcode
-

Employee_Email
rel Employee
-

Owners
-

Estates
rel Owners
rel Estate_Type
rel Zipcode
-

Estate_Type
-

Agents
-

Regions
-

Agent_Region_Junction
rel Agents
rel Regions
-
```

# Logical 

```
# Logical

Employee
-
Employee_ID PK
Name
Age
Address
Zipcode FK - Zipcode.Zip_Code

Zipcode
-
Zip_Code PK
City
State

Employee_Email
-
Email_ID PK
Employee_ID FK - Employee.Employee_ID
Email

Owners
-
Owner_ID PK
First_Name
Last_Name

Estates
-
Estate_ID PK
Owner_ID FK - Owners.Owner_ID
Estate_Type FK - Estate_Type.Estate_Type_ID
Address
Zip_Code FK - Zipcode.Zip_Code

Estate_Type
-
Estate_Type_ID PK
Estate_Type

Agents
-
Agent_ID PK,
First_Name,
Last_Name

Regions
-
Region_ID PK
Region_Name

Agent_Region_Junction
-
Agent_ID FK - Agents.Agent_ID
Region_ID FK - Regions.Region_ID
```

# Physical Schema
```
# Physical

Employee
-
employee_id INT PK
name VARCHAR(255)
age INT
address VARCHAR(255)
zip_code INT FK - Zipcode.zip_code

Zipcode
-
zip_code INT PK
city VARCHAR(255)
state VARCHAR(255)

Employee_Email
-
email_id INT PK
employee_id INT FK >- Employee.employee_id
email VARCHAR(255)

Owners
-
owner_id INT PK
first_name VARCHAR(255)
last_name VARCHAR(255)

Estates
-
estate_id INT PK
owner_id INT FK - Owners.owner_id
estate_type VARCHAR(255) FK - Estate_Type.estate_type_id
address VARCHAR(255)
zip_code INT FK - Zipcode.zip_code

Estate_Type
-
estate_type_id VARCHAR(255) PK
estate_type VARCHAR(255)

Agents
-
agent_id INT PK
first_name VARCHAR(255)
last_name VARCHAR(255)

Regions
-
region_id INT PK
region_name VARCHAR(255)

Agent_Region_Junction
-
agent_id INT FK >- Agents.agent_id
region_id INT FK >- Regions.region_id
```