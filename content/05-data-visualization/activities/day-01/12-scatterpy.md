+++
title = "12. Scatter Py 👩‍🎓👨‍🎓"
weight = 12
tags = ["matplotlib"] 
+++

# Scatter Py

In this activity, you will create a scatter plot that visualizes ice cream sales in comparison to temperature increases.

## Instructions

Create a scatter plot that matches the following image:

![scatter](../images/IceCreamSales.png)

## Bonus

Create a new list called `scoop_price`, fill it with values, and then set it so that the size of the dots are set according to those values.

---



## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

%matplotlib notebook
import matplotlib.pyplot as plt
import numpy as np
temp = [14.2, 16.4, 11.9, 15.2, 18.5, 22.1, 19.4, 25.1, 23.4, 18.1, 22.6, 17.2]
sales = [215, 325, 185, 332, 406, 522, 412, 614, 544, 421, 445, 408]
# Tell matplotlib to create a scatter plot based upon the above data

# Without scoop_price
plt.scatter(temp, sales, marker="o", facecolors="red", edgecolors="black")

# BONUS: With scoop_price set to the scalar value
# scoop_price = [89, 18, 10, 28, 79, 46, 29, 38, 89, 26, 45, 62]
# plt.scatter(temp, sales, marker="o", facecolors="red", edgecolors="black", s=scoop_price)

# Set the upper and lower limits of our y axis
plt.ylim(180,620)

# Set the upper and lower limits of our x axis
plt.xlim(11,26)

# Create a title, x label, and y label for our chart
plt.title("Ice Cream Sales v Temperature")
plt.xlabel("Temperature (Celsius)")
plt.ylabel("Sales (Dollars)")


# Save an image of the chart and print to screen
# NOTE: If your plot shrinks after saving an image,
# update matplotlib to 2.2 or higher,
# or simply run the above cells again.
plt.savefig("../Images/IceCreamSales.png")
plt.show()
 
```
{{% /expand%}}