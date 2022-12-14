+++
title = "06. Walrus Group  👩‍🏫🧑‍🏫"
weight = 6
tags = ["excel"] 
+++

* Now, open **06-Evr_WalrusGroup-Filter/Unsolved/Walrus_Group_Unsolved**.xlsx activity.

* This is real data from the U.S. Geological Survey studying walruses hauled out on ice floes in Alaska.

* Select the first row of data on the sheet, then, in the “Editing” group of the “Home” tab, click the "Sort & Filter" button. Next, select "Filter" from the menu that pops up.

  * Each column should now have an arrow button in the header cell. By clicking these arrows, we can choose which rows we would like to filter out of our chart based on the values that are contained in that column.

  * For example, in the "Ice Form" column, if we select "Ice Cake," then the sheet will display all the rows with a value of "Ice Cake".

  * We can then create charts using only the data that remains. So, if we wanted to create a chart that only takes into account the group sizes observed on "Ice Cake" ice floes, we could now do so.

  * It is very important to note that whatever charts we create using filters will be modified if we change the filtering options again. To preserve your filtered charts, copy and paste them to an external program like MS Paint or Word.

* Another way to create charts from filtered data is to create a "Pivot Chart".

  * **PC steps**

    * Pivot charts operate in much the same way as pivot tables. They allow users to aggregate data of similar types and then create visualizations for them.

    * To create a pivot chart, navigate into the “Charts” group of the “Insert” tab, and select "Pivot Chart" from the options available, as in the following image. Then, set up the pivot table that you want to visualize as a pivot chart.

      ![PC Pivot Chart](../images/PC_PivotChart.png)

  * **Mac steps**

    * First, create a pivot table using “Ice Floe” as our rows value and “GroupSize" and "DistanceToGroup" as values.

    * Click the _**i**_ next to the values, and switch to **Max** to create our pivot table, as in the following image:

      ![Mac pivot](../images/mac_pivot.png)

    * Find "Insert" on the ribbon, and add any recommended chart to create a Pivot Chart.

    * Now, when you play around with the filters in our pivot table, the chart will adjust.

* Data Source: Jay, C. V., Quakenbush, L. T., Citta, J. J., Fischbach, A. S. and Battaile, B. C., 2020, Sex and Age Composition of Walrus Groups Hauled Out on Ice Floes in the Bering and Chukchi Seas, 2013-2015: U.S. Geological Survey data release, [https://doi.org/10.5066/F79K4894](https://doi.org/10.5066/F79K4894)
