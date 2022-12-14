+++
title = "04. Scatter plot 👩‍🏫🧑‍🏫"
weight = 4
tags = ["excel"] 
+++

* Open 04-Ins_ScatterPlot/ScatterPlot.xlsx in Excel, navigate into the "Normal Trend" worksheet, and we can use a scatter plot to compare an individual's salary to the price of their car.

* **PC steps**

  * Adding a trend line to a chart is a quick process. Click the plus symbol to the right of your selected chart, then, under “Chart Elements”, select the "Trendline" option, as in the following image:

    ![PC Trend line](../images/PC_TrendLine.png)

* **Mac steps**

  * Click "Add Chart Element" on the left side of the ribbon, then navigate to "Trendline" in the dropdown, and select the trend line that best fits our data, as in the following image:

    ![Mac Trend line](../images/mac_trendline.png)

* Our original scatter plot showed the most common form of trend line, the straight line, but other types of trend lines may be more fitting for some datasets.

  * Navigate to the second sheet of the Excel workbook, named “Power Trend,” and  the _y_ variable increases exponentially in relation to the _x_ variable. Due to this relationship, the "Power" trend line would fit this dataset better than a straight line.

    * **PC steps**

      * To change the type of trend line, double-click on a chart's trend line, and then select an available option, as in the following image:

        ![PC Format Trendline](../images/PC_FormatTrend.PNG)

    * **Mac steps**

      * Click "Add Chart Element" on the left side of the ribbon, then navigate to "Trendline". This time, select "More Trendline Options" to bring up the "Format Trendline" menu.

      * Select the "Power" option, as in the following image:

        ![Mac Power line](../images/mac_power.png)

* Navigate into the third sheet of the Excel workbook, named Exponential Trend, and this dataset's second value increases exponentially based on the row it is contained within. This means that an "Exponential" trend line would fit this data best.

* Configuring the axes themselves is another way to modify charts based on the data. For example, if our data increases exponentially, then we may want to create a chart with axes that also increase exponentially.

  * We can adjust axis formats by double-clicking on an axis and then changing the bounds, units, and the methods through which the axes are displayed.

  * Steps for adjusting axis formats are captured in the following image:

    ![Mac Axis Options](../images/mac_axis_options.png)

  * Be sure to mention that although axis editing allows for more customization, it can also be used to make charts misleading. For example, if we used larger units on a dataset whose values are relatively low, we could make it look as if the correlation between two variables was smaller than it really is.

* How to reverse the _x_ and _y_ axes of their charts. To do this, make sure the chart is selected, and then click “Select Data” from the “Chart Design” tab on the ribbon. In the “Select Data Source” window, select the data series.

  * On a Mac, the “X Values” and “Y Values” properties are to the right.

  * On a PC, click “Edit”. You will see a new “Edit Series” window with “Series X values” and “Series Y values”

  * These will contain selection formulas for the respective ranges. Switch the formulas by copying and pasting to switch the axes of the scatter plot.

