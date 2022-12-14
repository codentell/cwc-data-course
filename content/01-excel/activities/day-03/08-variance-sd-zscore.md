+++
title = "08. Variance SDZ Score Review 👩‍🏫🧑‍🏫"
weight = 8
tags = ["excel"] 
+++


  * We will discuss the **summary statistics** that are used to describe the variability of a dataset.

  * **variance**, **standard deviation**, and **z-score** are the **summary statistics** used to describe the variability in data.

  * **variance** is an overall description of how far values in the dataset are from the mean. In other words, **variance** describes how much variation exists within the data.

  * the equation for variance with the as captured in the following image:

  ![equation for variance](../images/VarianceEquation.png)

  * Know how to manually calculate variance is not critical for this course. Almost all analytical tools and programming languages have functions that can calculate variance for us.

  * The most important takeaway from the equation is that the variance calculation considers the distance of each value in the dataset from the center of the dataset.

  * it does not matter if a value is above or below the mean of the dataset. The difference from the mean is squared, so the **variance** will always be positive.

* Open 08-Ins_Variance-SD-Zscore/Variance-SD-Zscore.xlsx in Excel.

  * Explain that this dataset contains the monthly average temperatures for Austin, Texas, and San Francisco, California, as captured in the following image:

  ![Example of variance](../images/13-VarianceExample.png)

  * We can identify from the bar chart that the overall temperature in Austin is hotter than San Francisco.

  * We can calculate the total variance of temperature for each city using Excel's `VAR.P` function.

  * The variance of temperature in Austin is much higher than in San Francisco. Therefore, we can quantitatively determine that the overall temperature is less variable in San Francisco than in Austin.

  * Using variance to describe a dataset can be problematic because the units of variance are not the same units that we use to measure the mean&mdash;or the dataset itself.

  * The variance equation, the difference between an observation and the mean is in the same unit of measurement; however, squaring it changes the unit of measurement (for example, _meters_ are a different measurement than _square meters_). The number of points in the dataset is a dimensionless quantity, and does not affect the unit of measurement.

  * The first example, we would say that the average annual temperature in Austin was 79.6 degrees, with a variance of 149.91. Technically, the units for the variance are “degrees  squared”, but this is confusing and often dropped in practice.

  * The complexity of the measurement, describing the variability in terms of units squared may be complicated.

* The slideshow, and step through the next few slides to accompany the next section of the activity. Be sure to cover the following talking points:

  * In statistics, we use the **standard deviation** to interpret how _spread out_ the data is from its mean.

  *  **standard deviation** can be derived by calculating the square root of the variance. As with variance, most analytical tools and programming languages have functions that automatically calculate the **standard deviation**.

  * Calculating the square root of the variance, the **standard deviation** describes the variability of the data using the same units as the mean&mdash;in this case, degrees.

* To the next sheet in the Excel workbook. Explain that this is the same temperature dataset from the previous sheet, except now we’ve also calculated the temperature standard deviation for both cities using the `STDEV.P` function in Excel.

  * Manually calculated the standard deviation by taking the square root of the variance; the manual calculations are equal to the Excel calculations, as captured in the following image:

![Example of standard deviation](../images/13-SDExample.png)

  * under certain circumstances, the standard deviation becomes an even more powerful statistical tool than just describing the variability of the data.

  *  when a dataset is considered **normally distributed**, the standard deviation can be used to describe how many data points are close to the mean.

  *  we will discuss **normal distributions** later in the course, but for now we will use a general rule of thumb: when measurements in a dataset are obtained independently of one another, the data is considered to be normally distributed.

  * Each temperature reading was independently obtained month to month and region to region. Therefore, we will assume that the data is normally distributed.

  * when a dataset is normally distributed, the data points follow a **68-95-99.7** rule.

  *  **68-95-99.7** rule, roughly 68% of all values in a dataset fall within one standard deviation from the mean (in either direction). Additionally, 95% of the values fall within two standard deviations, and 99.7% of the values fall within three standard deviations.

* To the next sheet in the Excel workbook. Explain that in this sheet, we have taken the same average temperature data, we have our calculations for the mean and the standard deviation, and now we’ve added calculations for the boundary values at one standard deviation from the mean in either direction, as captured in the following image:

![Example of normal dist 68 rule](../images/13-Normal68.png)

  * the Austin data, six of the twelve months fall within one standard deviation.

  * the San Francisco data, eight of the twelve months fall within one standard deviation.

  * the 68-95-99.7 rule is not perfect, it helps analysts extrapolate characteristics about a dataset using only summary statistic values.

  *  we have now studied two different statistical values that we can use to describe the overall dataset in terms of distance from the mean.

    * "But what if we wanted to describe a single data point in terms of its distance from the mean?"

  * calculate a data point's **z-score** to measure its distance from the mean in terms of standard deviations.

  ![equation for z-score](../images/ZScoreEquation.png)

  * Programming languages and software tools include a function to calculate **z-score**. Therefore, we will be calculating the z-score manually using the standard deviation and the mean of the data.

  * z-score can be positive or negative. If the z-score is negative, the data point is less than the mean; if the z-score is positive, the data point is greater than the mean.

* on this sheet, we now used the mean and standard deviation to calculate the temperature z-scores for each month in both cities, as in the following image:

![Example of z-score](../images/13-ZScoreExample.png)

  * z-scores provide an overview of each value in a dataset, so we can easily determine which values are the most extreme relative to the mean.

  * Note that in this example dataset, the months with the most extreme differences in temperature from the mean were January and December in Austin, and January, September, and December in San Francisco.
