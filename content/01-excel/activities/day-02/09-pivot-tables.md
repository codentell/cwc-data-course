+++
title = "09. Pivot Tables 👩‍🏫🧑‍🏫"
weight = 9
tags = ["excel"] 
+++

* File **09-Ins_PivotTables/PivotTables_Solved.xlsx** for this activity.

  *  Powerful tool in the Excel arsenal is the **pivot table**, which allows users to extract summary data from large, detailed, and consistent datasets.

  * Explain that pivot tables summarize data using functions like `SUM`, `COUNT`, and `AVERAGE` on subsets of the data. These subsets can be as general or as specific as we like.

  * Caution  pivot tables are not designed for deeper analysis. They are designed to provide summary metrics at a glance.

  * To create a pivot table, select "Pivot Table" within the "Insert" tab, and then hit “OK” in the new window that pops up.

  * A menu will appear, and users will be able to pick and choose what columns from the original sheet should be placed into their pivot table.

  * Place "ACTIVITY" into "Rows," and a column containing all products will appear on the screen, with all duplicate data points placed together.

  * Users can also group rows into subcategories to allow for more specific or generalized tables by adding more fields into the "Rows" section. Add "TYPE" into the "Rows" section, as in the following image:

  ![MultiRows](../images/MultiRows.png)

  * Place "INCOME_AMT" into "Values," and a new column will appear containing the sum of the "INCOME_AMT" column from the original spreadsheet as it relates to the "TYPE" column. In other words, all "Cultural, Ethnic Awareness" values are added together, all "Theater" values are added together, and so on.

  * Users can change what kind of data they would like to analyze within a pivot table by clicking on any of the fields placed within the "Values" section and selecting "Field Value Settings" from the dropdown menu. The following “PivotTable Field” window allows users to calculate maximums, minimums, and averages among other options, as captured in the following image:

  ![ValueSettings](../images/ValueSettings.png)

  * Place "STATE" into "Filters", and a new field named "STATE" will appear above the pivot table. By clicking on this field and selecting a value from the list that appears, users can filter data based on what sales took place in a particular state, as captured in the following image:

  ![Images/07-PivotTables.png](../images/07-PivotTables.png)

*  Sort tables by selecting any individual cell and then right-clicking. Within the pop-up menu that appears, select “Sort”, then choose your desired sorting method.

## Data Source:
  * Exempt Organizations Business Master File Extract (EO BMF), Internal Revenue Service (IRS), [https://www.irs.gov/charities-non-profits/exempt-organizations-business-master-file-extract-eo-bmf](https://www.irs.gov/charities-non-profits/exempt-organizations-business-master-file-extract-eo-bmf)
    * [https://www.irs.gov/pub/irs-soi/eo1.csv](https://www.irs.gov/pub/irs-soi/eo1.csv), accessed August 18, 2021.
    * [https://www.irs.gov/pub/irs-soi/eo_info.pdf](https://www.irs.gov/pub/irs-soi/eo_info.pdf), accessed August 31, 2021.
  * Dataset reduced in Pandas. For more information, see exercise [README.md](Activities/09-Ins_PivotTables/README.md)

