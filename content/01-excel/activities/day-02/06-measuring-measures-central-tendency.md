+++
title = "06. Measuring Measures Central Tendency 👩‍🏫🧑‍🏫"
weight = 6
tags = ["excel"] 
+++

File: 
* **06-Evr_MeasuringMeasures-CentralTendency/MeasuringMeasures.xlsx**

* The measures of central tendency can summarize the dataset using single values, so they are a type of **summary statistic**. Whenever we analyze a new dataset, we should calculate all three measures of central tendency.

* Depending on the type and size of the dataset, the different measures of central tendency may or may not describe the dataset effectively. 
    * Therefore, we should always consider what measures of central tendency will summarize the data well before we use them in a summary table.

* Looking at variety of example datasets; calculating the mean, median, and mode; and determining which measures of central tendency describe the data effectively.

* Dataset contains the number of cup holders in 20 vehicles surveyed in a school parking lot. Point out that in this example, we plotted out the distribution of cup-holder results into categories and determined the number of vehicles for each category, as captured in the following image:

![This is the first example](../images/06-MeasuringExample1.png)

* Next sheet in the workbook for the solution. This sheet plots the three measures of central tendency for the cup-holder dataset. Point out that we calculated the values for mean, median, and mode using the Excel functions, and we plotted their values using colored lines. In this example, all three measures of central tendency are roughly the same value, as captured in the following image:

![This is the first example](../images/06-MeasuringExample1Solved.png)

* All three measures of central tendency effectively describe the center of the data.

* The next sheet in the workbook, which contains a dataset on the salaries of 10 employees at a small, family-owned car dealership. Point out that in this example, we have already calculated the mean, median, and mode using Excel functions. Additionally, we have already plotted the distribution of salaries and added colored lines for the measures of central tendency, as captured in the following image:

![This is the second example](../images/06-MeasuringExample2.png)

* The mean of the dataset in the second example no longer effectively describes the center of the data.

* Extreme values in a dataset, the mean can drift away from the center of the data.

  * In this example, the $100,000 and $200,000 salaries are much higher than the rest of the salaries; these higher salaries would be considered extreme values for this dataset

* Point out to the students that the `MODE.SNGL` function in Excel returned an "#N/A" value. Explain that this means there is no mode for the dataset.


* The mode is used to describe the center of a dataset when measurements are repeated or there are finite options for each data point. When there are infinite possible values, there is typically no mode for the dataset.

  * In this example, each employee's salary was a different amount. Therefore, the dataset does not have a mode.

*  That the median salary is $24,500, which is right around the center of the dataset.

* Some example answers may be:

  * “The median only considers the _center_ of a sorted dataset”
  * “The mean is affected by very large values”
  * “The median is less sensitive”

* The mean and median values are _usually_ very close when a dataset is large or doesn’t contain extreme values. When the dataset is smaller or contains extreme values, the mean and median _usually_ differ.

* The next sheet in the workbook. The third dataset contains the results from an office survey asking employees how many cups of coffee they drink per day.  The mean, median, and mode for the dataset, and we’ve plotted the cups of coffee per day to help visualize the data. The mean, median, and mode are represented on the plot by colored lines, as captured in the following image:

![This is the third example](../images/06-MeasuringExample3.png)

* Once again dealing with a dataset with discrete groups. The counts for cups of coffee fall into four groups: 0 cups, 1 cup, 2 cups, or 3 cups.

* This example, there are two modes in the data, which represent two distinct groups of employees: one group drinks two cups of coffee per day, and the other group does not drink coffee at all.

* The mean and median both estimate that the center of the data is around 1.5 cups of coffee per day. However, if we used the mean or median to describe the dataset, we would be misrepresenting the large group of employees who do not drink any coffee.

* The measure of central tendency that we choose may be dependent on what question we are trying to answer.

*  The fourth dataset contains the amount of rainfall per month at an airport over a year from January through December. Calculated the mean, median, and mode for the dataset, and that the rainfall per month has been plotted to help visualize the data. The mean, median, and mode are represented by color lines on the plot, as captured in the following image:

![This is the fourth example](../images/06-MeasuringExample4.png)



  * This dataset contains rainfall measurements, and there are infinite possibilities for the amount of rainfall per month. Therefore, using mode to describe the dataset is not the best measure.

  * The mean or median could be used to describe the center of this dataset because the values are relatively close together.

  * Because there are relatively extreme values in January and April, the median would be the best measure of central tendency.

* The median is typically the safest measure of central tendency to use when you are uncertain about the origins of the data or what questions you are trying to answer with the data.

  *Caution when people ask for the average of the dataset, they are most likely referring to the mean.

