+++
title = "02. NJ Templ Line Plots 👩‍🎓👨‍🎓"
weight = 2
tags = ["matplotlib"] 
+++

# New Jersey Weather

In this activity, you will visualize the differences between temperature recorded in degrees Fahrenheit versus degrees Celsius.

## Instructions

* Using the following data, plot the monthly averages for temperature in New Jersey in both degrees Fahrenheit and degrees Celsius.

  * Average temperature per month in Fahrenheit: 39, 42, 51, 62, 72, 82, 86, 84, 77, 65, 55, 44.

* Assign to the x-axis a range of numerical values representing each month of the year.

* Plot the degrees Fahrenheit points.

* Use a list comprehension to convert the temperature to degrees Celsius.

  * The formula for conversion is: C = (F – 32) * 0.56. In this formula, C is degrees Celsius and F is degrees Fahrenheit.

* Plot the degrees Celsius points.

* Create a third plot with both the degrees Fahrenheit and degrees Celsius points.

## Hint

* Check the [Matplotlib documentation](https://matplotlib.org/2.0.2/index.html) for more information regarding the PyPlot library.

* Also check the [NumPy documentation](https://docs.scipy.org/doc/numpy/reference/) for more information on the NumPy library.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Dependencies
import numpy as np
import matplotlib.pyplot as plt
# Set x axis to numerical value for month
x_axis_data = np.arange(1,13,1)
x_axis_data
array([ 1,  2,  3,  4,  5,  6,  7,  8,  9, 10, 11, 12])
# Average weather temp
points = [39, 42, 51, 62, 72, 82, 86, 84, 77, 65, 55, 44]
# Plot the line
plt.plot(x_axis_data, points)
plt.show()

# Convert to Celsius C = (F-32) * 0.56
points_C = [(x-32) * 0.56 for x in points]
points_C

# Plot using Celsius
plt.plot(x_axis_data, points_C)
plt.show()

# Plot both on the same chart
plt.plot(x_axis_data, points)
plt.plot(x_axis_data, points_C)
plt.show()
```
{{% /expand%}}

