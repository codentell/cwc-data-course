+++
title = "05. Central Tendency 👩‍🏫🧑‍🏫"
weight = 5
tags = ["excel"] 
+++

File: 
* **05-Ins_CentralTendency/CentralTendency.xlsx**

* **Measures of central tendency** are some of the most basic concepts in statistics.

  *  **measures of central tendency** are values that describe a dataset. More specifically, the **measures of central tendency** describe the _center_ of a dataset.

  * The most common measures of central tendency are the **mean**, **median**, and **mode**.

  *  **mean** of a dataset is also referred to as the _arithmetic_ average of a dataset.


  *  **median**, we sort the values in the dataset and then select the middle element.

    * For even-length datasets, we will have _two_ elements in the middle of the list. The average of the two elements is the median of such a list.

  *  **mode** of a dataset is the _most frequently occurring value_.

    * Unlike the **mean** and **median**, which can only be used to describe numerical datasets, the **mode** can be used to describe numerical or _categorical_ datasets.

  *  **mode**, we would count every element in a dataset. The most frequent element in the dataset is the **mode**.

    * If multiple elements in a dataset share the greatest frequency (that is, there’s a tie), the dataset would have multiple **modes** and, therefore, be considered **multimodal**.

* Introduce the students to the first sheet in the workbook.

  * Point out that this example consists of a dataset of 30 numbers that range between one and ten. Explain that we have plotted each value and its frequency to better visualize the dataset in Excel, as captured in the following image:

![Example of mean in Excel](../images/05-MeanExample.png)

  * "If any of you are unfamiliar with bar plots, that is fine; we will learn how to make plots like these tomorrow!"

* Explain the steps needed to manually calculate the mean in Excel.

  * Calculate the sum of all values in the dataset using the `SUM` function.

  * Calculate the number of elements in the dataset using the `COUNT` function.

  * Divide the sum of all the values by the number of elements to calculate the mean.

* Point out that in Excel, we have already calculated the mean of a dataset in previous activities using the `AVERAGE` function.

* Introduce the students to the next sheet in the workbook. Point out that this example consists of another 30 numbers that range between one and ten; and once again, we’ve plotted each value and its frequency to visualize the dataset, as captured in the following image:

![Example of median in Excel](../images/05-MedianExample.png)

* The steps to manually calculate the median.

  * Sort the dataset in ascending order.

  * Determine the length of the dataset.

  * Identify the middle element. This is the median value.

* Point out that because our dataset is even in length, the middle of the dataset is between two numbers. Therefore, we must calculate the mean between both numbers, which is five in this case.

* Explain that in Excel, we use the `MEDIAN` function to calculate the median of the dataset for us.

* Introduce the students to the next sheet in the workbook, which includes another 30 numbers between one and ten and a plot of each value’s frequency. In this dataset, the distribution has changed slightly, as captured in the following image:

![Example of a single mode in Excel](../images/05-SingeModeExample.png)

* Explain the steps to manually calculate the mode.

  * Count the occurrences of each value in the dataset.

  * Determine the most frequent value or values in the dataset to find the mode or modes.

* This dataset, there is only one element with the highest count. In this case, the number five is the only mode in the data.

* Explain that in Excel, we would use the `MODE` or `MODE.SNGL` function to determine the single mode of the dataset.

* Point out to the students that the `MODE` function is just an abbreviation of the `MODE.SNGL` function.

* In the dataset, as captured in the following image:

![Example of a multi-mode in Excel](../images/05-MultiModeExample.png)

* The occurrences of each element in the dataset, the values two, five, and eight occur four times. Therefore, we would call this dataset _multimodal_.

* Mode manually, we would say that two, five, and eight are modes of the dataset.

*  `MODE.SNGL` function will only return the first mode it finds. When a dataset is multimodal, the `MODE.SNGL` function should not be used.

*  `MODE.SNGL`, we use `MODE.MULT` to return all of the modes in a dataset.

*  `MODE.MULT` is different from other functions in Excel.

  * "`MODE.MULT` is an array function in Excel. All that means, for now, is that the function will act slightly differently than any of the other functions you will learn in this unit."

  * When you use `MODE.MULT`, you start by typing the function into the cell just like any other Excel function. Then, you select a range of data.

  * Once the data has been selected, press `Enter` on your keyboard to execute the function; this action fills in all mode values in the array of cells.

*  `MODE.MULT`, it returns all of the modes in the dataset correctly.

* We are calculating the mode but are uncertain if the dataset is multimodal, it is better to use the `MODE.MULT` function and select a large array of cells.

  * Any unused cells in Excel array functions will have an "N/A" value, but it is better to have unused cells than to miscalculate the mode.

