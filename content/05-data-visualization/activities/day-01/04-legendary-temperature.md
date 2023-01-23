+++
title = "04. Legendary Temperature 👩‍🎓👨‍🎓"
weight = 4
tags = ["matplotlib"] 
+++

# Legendary Temperature

In this activity, you will expand upon your temperature plots to add a legend.

## Instructions

* Modify the New Jersey temperature line charts from earlier so that they match the image provided.

    ![model image](../images/avg_temp.png)

* Once the plot has been created, check the [Matplotlib documentation](https://matplotlib.org/2.0.2/index.html) to see what additional formatting could be added to the chart.

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Include this line to make plots interactive
%matplotlib notebook
# Dependencies
import matplotlib.pyplot as plt
import numpy as np

# Set x axis to numerical value for month
x_axis = np.arange(1,13,1)
x_axis

# Avearge weather temp
points_F = [39, 42, 51, 62, 72, 82, 86, 84, 77, 65, 55, 44]
# Convert to Celsius C = (F-32) * 0.56
points_C = [(x-32) * 0.56 for x in points_F]
points_C

# Create a handle for each plot
fahrenheit, = plt.plot(x_axis, points_F, marker="+",color="blue", linewidth=1, label="Fahrenheit")
celsius, = plt.plot(x_axis, points_C, marker="s", color="Red", linewidth=1, label="Celsius")

# Set our legend to where the chart thinks is best
plt.legend(handles=[fahrenheit, celsius], loc="best")

# Create labels for the X and Y axis
plt.xlabel("Months")
plt.ylabel("Degrees")

# Save and display the chart
plt.savefig("../Images/avg_temp.png")
plt.show()
```
{{% /expand%}}