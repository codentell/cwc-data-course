+++
title = "02. Basic Charting  👩‍🏫🧑‍🏫"
weight = 2
tags = ["excel"] 
+++

* **PC** Excel chart options are captured in the following image:

  ![Excel chart options in Windows](../images/PC_chart_options.png)

* **Mac** Excel chart options are captured in the following image:

  ![Excel chart options on Macs](../images/MAC_chart_options.png)

* Excel enables users to create many kinds of charts, but first we’ll create a bar chart since that fits our data nicely.

* Whenever you select a charting option from the “Charts” group, a new menu will appear that allows you to select various visual options. For bar charts, we can choose between 2-D or 3-D visuals with a horizontal or vertical layout.

  * For now, use the vertical 2-D chart since it is the most basic and commonly used option.

* Once a chart option has been selected, a new chart will automatically be placed into the spreadsheet. Clicking on this chart will allow us to edit it; we can also double-click on any element of the chart to edit it more specifically.

  * For now, click on the chart's title, and demonstrate that we can rename the chart. 
  
  * Note The title may be the generic "Chart Title" if we did not include the header rows in our selection.

* **PC steps**

  * Next, click the plus sign to the right of our chart. This will bring up a list of elements and sub-elements that we can add or remove, as in the following image:

    ![Images/PC_AddElements.png](../images/PC_AddElements.png)

  * Select the “Axes Titles” option to add titles for our vertical and horizontal axes. Then, click the arrow to the right of the “Axes Titles” option to open the sub-menu, which allows us to choose the specific titles that we would like to include.

  * By clicking the paintbrush to the right of a chart, we can access options for “Style” and “Color.” Style options include several basic visual styles. Color options include various color schemes that we can apply to our chart, as in the following image:

    ![Images/PC_ChartColors.png](../images/PC_ChartColors.png)

  * Selecting a new color palette may not feel like much at first, but if we double-click on the bars of our chart, a new menu will pop up to the side of the application and allow us to format our bars. If we then click on the paint can and select the “Vary colors by point” option, each bar will be given a different color that fits the palette we selected earlier.

* **Mac steps**

  * Click “Add Chart Element” on the left side of the ribbon, then click “Axis Titles”. Here, you can select “Primary Horizontal” or “Primary Vertical,” as in the following image:

    ![Images/MAC_axis.png](../images/MAC_axis.png)

  * On the ribbon to the right of “Add Chart” Element, click “Change Colors” to change the colors of the bar graph.

  * Double-click any of the bars to bring up the “Format Data Series” menu. Here, we can check the option to “Vary colors by point” to give each bar a different color, as in the following image:

    ![Images/Mac_colors.png](../images/Mac_colors.png)

* Note The format menu for a chart element can be opened by double-clicking any individual element. This lets them control all aspects of the visualization. Reiterate that the exact location of the formatting control may differ between versions of Excel.

* Let's say that we made a bar chart, but then our employer told us that they really wanted a pie chart. Luckily for us, Excel has an option that allows us to change a chart's type by opening the chart's right-click menu and selecting "Change chart type". This means we can easily turn a bar chart into a pie chart in Excel.

  * You can also change a chart's type by selecting the chart, going into the “Design” tab's “Type” group, and clicking "Change Chart Type".

  * Change the bar chart we’ve been working on into a pie chart. Be sure to add in the "Legend" element for our new pie chart. Otherwise, no one will know what each slice of the pie represents.

    * On Macs, you can add a legend by clicking "Add Chart Element" on the ribbon, selecting "Legend", and then choosing the location of the legend, as in the following image:

      ![Images/mac_legend.png](../images/mac_legend.png)

* Another essential type of graph is the line graph. But the data that we’re using is not ideal for creating a line graph. 

  * “Our data does not show any changing trends over time. It instead compares a single piece of data across multiple named categories.”

* Open **02-Ins_BasicCharting/BasicCharts.xlsx** in Excel, and navigate to the second sheet, named "Ice Cream Sales." This sheet contains data over time: how many scoops of different ice cream flavors have been sold over a year.

  * Select all the data on this sheet, and then choose a 2-D line chart from the “Charts” group on the “Insert” tab, as in the following image: Remember: your selection should include the rows and columns that contain the  data labels:

    ![PC Line Charts](../images/PC_LineGraph.png)

  * Aware of how cluttered this chart is. This makes it difficult to glean information or draw conclusions from the data visualization.

    * **PC steps**: To filter the rows you'd like to include, choose the third option to the right of the chart. This option allows us to filter what categories of data, or ice cream flavors, that we would like to show.

      * Select a few ice cream flavors from the list, and then hit the "Apply" button to filter the data for our chart.

    * **Mac steps**: To filter what data is shown on the chart, select the “Home” tab, select column “A”, then click “Sort & Filter” on the right-hand side of the ribbon. Note that “Sort & Filter” may be hidden in the “Editing” tab at certain screen or window sizes. Select “Filter” to set your column in filter mode, then click the arrow dropdown in the column A header cell: there, you will find the options for sorting and filtering. The following GIF captures this process:

      ![Images/mac-line-chart-filter.gif](../images/mac-line-chart-filter.gif)

      * Select a few ice cream flavors from the list, update the chart, and note the difference in the line chart’s readability.

    * It is important to note that the filter options listed here are limited. When we would like to filter out data based on some condition (for example, greater than, less than, etc.), these limited filter options will not be adequate.