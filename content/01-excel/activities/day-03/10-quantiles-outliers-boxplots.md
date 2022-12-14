+++
title = "10. Quantiles Outliers Boxplots 👩‍🏫🧑‍🏫 "
weight = 10
tags = ["excel"] 
+++

* Wwe are characterizing a dataset, we need to be careful that our summary statistics don't misrepresent the data.

  * The biggest challenges in statistics is that real-world data is imperfect. Oftentimes, real-world data will contain extreme values that can skew our interpretations, especially when we try to describe the center of a dataset.

  * We use **quantiles** to describe segments of a dataset.

  *  **quantiles** are the "cut points" that separate a sorted dataset into equal-sized fragments.

  *  Two most popular types of **quantiles** are **quartiles** and **percentiles**.

  * **quartiles** divide a dataset into four equal parts, and **percentiles** divide a dataset into 100 equal parts.

*10-Ins_QuantilesOutliersBoxplots/quantiles_outliers_boxplots.xlsx, This dataset is a sorted list of 11 values ranging between 10 and 100, and quartiles have been calculated, as in the following image:

![The first quartile examples](../images/10-QuartileExample1.png)

  * The median can also be considered the cut point that divides a dataset into two equal parts. Therefore, the median can also be called the **second quartile** or **Q2**.

  * Point out that the median of this dataset is 55. There are five values below 55 and five values above 55.

  * Explain that the **first quartile** (also known as **Q1**) is the median of the first set of values separated by **Q2**. Alternatively, the **third quartile** (also known as **Q3**) is the median of the second set of values separated by **Q2**.

  * Point out that this is a simplified example; it’s easy to identify the cut points in order to make four equally sized groups of data.

* The next sheet in the workbook. Explain that this data is a sorted list of car speeds on a residential street, measured in miles per hour. In total, 123 measurements were made, ranging from 22 to 37 mph, as captured in the following image:

![The second quartile examples](../images/10-QuartileExample2.png)

  * Explain that when a dataset is large, it can be difficult to determine where the quartiles are.

  * Note that we can use the `QUARTILE.EXC` function in Excel to calculate the quartile values.

  * Point out that the input to the `QUARTILE.EXC` function is a range of values and the number of the quartile it should calculate.

  * Note that in this dataset, the quartiles divide the data into groups of 34 values, with one group consisting of 35 values.

  * Quartiles allow us to make observations about the dataset without needing to plot the distribution of values.

  * One observation that we can make is that on average, the cars are driving 30 mph.

  * Another observation we can make is that 50% of the cars were driving between 25 and 34 mph.

  * Quartiles divide the data into 4 equal segments, the range between Q1 and Q3 covers roughly 50% of all data points.

  * Note that this range is known as the **interquartile range**, or **IQR** for short. In statistics, the **interquartile range** is used to help identify the most trustworthy measurements in a dataset. The **interquartile range** is calculated by subtracting Q1 from Q3.


  * That in data science, we call suspicious data points that are at either extreme of a dataset **potential outliers**.

  * **outlier** is a data point that differs from the rest of a dataset.

  * **outliers** can be caused by changes in data collection methods, experimental error, a malfunction of a machine, or any general source of unaccounted variability when generating a dataset.

  * **outliers** cause a dataset’s distribution to change, which causes issues when we try to characterize a dataset with summary statistics. Therefore, it is critical to identify **potential outliers** in a dataset before moving forward with any analysis.

  * two common ways to identify potential outliers in a dataset.

  * Explain that the most common qualitative method to identify potential outliers is the **box and whisker plot**.

  *  **box and whisker plot** is also known as a **box plot**, and it shows the distribution of values from a single list.

  * Note that the most common quantitative method to identify potential outliers is the `1.5*IQR` rule.

  * Explain that the `1.5*IQR` rule states that any data point that is 1.5 times the interquartile range lower than Q1 could be a potential outlier. Alternatively, any data point that is 1.5 times the interquartile range higher than Q3 could be a potential outlier.

* The next sheet, which contains a dataset describing car speeds on a two-lane road, as captured in the following image.

![The third quartile examples](../images/10-QuartileExample3.png)

  * Real-world data, it’s common to encounter suspicious data points at the low and high ends of a sorted dataset.

  * We remove data points that are not outliers, or if we report data without disclosing that we removed data points, we can be held liable for showing deceptive statistics.

  * Point out that in this example, the lower boundary of the `1.5*IQR` rule is 42.625 mph.

  * We were to remove potential outlier data, we must report that the value was removed alongside any table or figure generated from the dataset.

* final worksheet, captured in the follwing image. The worksheet now includes a box and whisker plot in addition to the car speeds, quartile values, IQR, and the boundaries for the `1.5*IQR` rule.

![The fourth quartile examples](../images/10-QuartileExample4.png)

  * Note that a **box plot** is a powerful visualization that provides a number of summary statistics at a glance.

  * Most analytical tools and programming languages have methods to build a **box plot**, and most **box plots** use the same shapes and styles to convey summary statistics.

  * The box in a box plot is the interquartile range, and the line in the middle of the box is the median of the dataset.

  * a box plot will sometimes include an `X` or triangle in the middle of the box; this symbol indicates the mean of the dataset.

  * The lines, or whiskers, protruding from the box indicate the largest and smallest data points inside the `1.5*IQR` rule.

  * The data points plotted past the whiskers indicate the potential outliers.

  * The data points on the box plot to the extreme values of the dataset to determine which data points are the potential outliers.

    * In Excel, you can hover over any data point to determine what value is being represented.

* Point out that in this example, we are looking at a vertical box plot. Explain that just like bar plots can be displayed with vertical or horizontal bars, box plots can also be displayed vertically or horizontally.
