+++
title = "12. Statistics Addon 👩‍🏫🧑‍🏫"
weight = 12
tags = ["excel"] 
+++

* Excel is a fantastic tool for quickly accessing, manipulating, and visualizing small-to-medium-sized datasets. However, Excel does not contain many statistical algorithms or tests "out of the box."

  * As we progress through the curriculum, we will cover a number of more robust statistical functions, tests, and concepts.

  * If we enable Excel's Analysis ToolPak add-on, we can always return to Excel to perform statistical tests on smaller datasets.

  *  The installation process is different for Mac and PC, and using the ToolPak is slightly different between the two operating systems.

  * To learn more, read the [official instructions](https://support.microsoft.com/en-us/office/use-the-analysis-toolpak-to-perform-complex-data-analysis-6c67ccf0-f4a9-487c-8dec-bdb5a2cefab6)

* Now, open 12-Ins_StatisticsAddon/Solved/MovingAverages.xlsx in Excel.

  * We will go over a short example where we use the ToolPak to calculate a moving average on a range of values.

  * Moving average function simply calculates the mean over a set interval of data points.

  * Sufficient documentation online if anyone is interested in the specific use cases for moving averages. For our purposes, the moving average is the most straightforward function in the ToolPak.

  * Navigate into the “Data” tab, locate the “Analyze” group, and select the "Data Analysis" option. Macs just have a "Data Analysis" button.

  * From the menu that comes up, select "Moving Average."

  ![Data Analysis](../images/PC_DataAnalysis.png)

  * In the Moving Average window, click the arrow next to "Input Range," and select the cells that you would like to average. In this case, select B2 to M2.

  * Set the interval whose average you would like to take. We will be setting this particular interval to 2 for now.

  * Select an output range for the averages you are calculating. In this case, select B3 to M3.

![Moving Average](../images/PC_MovingAverage.png)

  * Finally, hit "OK," and Excel will calculate/print the moving average according to your specifications.

    * The first cell of our range has been filled in with the value "#N/A", meaning "Not Available." Because this is the first data point, we don't have enough data to calculate an average (i.e., we need more than one value).

  * Point out that Excel's Analysis ToolPak prompts you for any needed variables; however, it does not provide context around any of the statistical functions.

  * Explain that we will cover many of the functions supported by the ToolPak throughout the curriculum. As we become more familiar with the variables and outputs of each statistical function, the Analysis ToolPak can become more and more of a secondary resource to use when exploring new data.


