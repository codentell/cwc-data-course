+++
title = "06. Importing Data 👩‍🏫🧑‍🏫"
weight = 6
tags = ["sql"] 
+++

## Files:

Fauna_Vertabrate.csv

```sql
-- Drop table if exists
DROP TABLE fauna_vertabrate;

-- Create new table
CREATE TABLE fauna_vertabrate (
    longitude DEC,
    latitude DEC,
    OBJECTID INT,
    suburb VARCHAR,
    property_name VARCHAR,
    GI_class VARCHAR,
    GI_type    VARCHAR,
    group_ VARCHAR,
    family VARCHAR,
    family_common_name VARCHAR,
    scientific_name VARCHAR,
    genus VARCHAR,
    species VARCHAR,    
    common_name VARCHAR,    
    fauna_status VARCHAR
);


-- View table columns and datatypes
SELECT * FROM fauna_vertabrate;
```

So far, the class has created their own tables and values manually using SQL code. 

As one might imagine, this process can be tedious when translating large datasets from external sources. Thankfully, pgAdmin includes a built-in import tool that can take CSV files and easily import the data into tables.

Return to pgAdmin and create a new database called Miscellaneous_DB.

Open the CSV file within an integrated development environment (IDE), such as Excel, to show the dataset that will be imported. Be sure to point out that the first row of this dataset includes headers.

Open a query tool within Miscellaneous_DB and create a table named fauna_vertabrate.

* Using the code from importing_data.sql, create the columns necessary to import the data. Point out that the columns created match the data in the CSV file.

* Once the table and columns have been created, right-click Miscellaneous_DB from the left-hand menu and select Refresh.

* Scroll down to Schemas and expand that menu, and then expand the Tables menu, as captured in the following image:

![](table-expand.png)

Right-click the new table and select Import/Export from the menu, as captured in the following image:

import-export.png

In the Options tab, complete the following steps:

Slide the Import/Export tab to Import.

Click on the dot menu to navigate to the Fauna_Vertabrate.csv file on your computer.

Slide the Header tab to Yes.

Select the comma from the drop-down menu to set it as the Delimiter.

Leave the other fields as they are, and then click OK.

These settings are captured in the following image:

import.png

In the query tool, rerun SELECT * FROM fauna_vertabrate to verify that data has been imported.

Let the class know that the bigger a dataset is, the longer it will take for pgAdmin to import values.

Data Source: City of Perth/Data WA (2021). Fauna Vertebrate. https://catalogue.data.wa.gov.au/dataset/perth-fauna-vertabrate

