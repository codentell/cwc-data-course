+++
title = "10. Pypies  👩‍🎓👨‍🎓"
weight = 10
tags = ["matplotlib"] 
+++

# Pies Pie Chart

In this activity, you will create a pie chart that visualizes pie flavor preferences in the United States.

## Instructions

Using the [starter file](Unsolved/py_pie.ipynb), create a pie chart that matches the following image:

![py_pie](../images/PyPies.png)

* Include all of the lists provided in the starter file: pies, pie_votes, colors, explode.

* Display the popularity percentages to one decimal place.

* Include a shadow, and determine the starting angle so the exploded pie piece is in the middle left section of the pie.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

%matplotlib notebook
import matplotlib.pyplot as plt
import numpy as np

pies = ["Apple", "Pumpkin", "Chocolate Creme", "Cherry", "Apple Crumb", "Pecan", "Lemon Meringue", "Blueberry", "Key Lime", "Peach"]

pie_votes = [47,37,32,27,25,24,24,21,18,16]
colors = ["yellow","green","lightblue","orange","red","purple","pink","yellowgreen","lightskyblue","lightcoral"]
explode = (0.1,0,0,0,0,0,0,0,0,0)

# Tell matplotlib to create a pie chart based upon the above data
plt.pie(pie_votes, explode=explode, labels=pies, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=140)
# Create axes which are equal so we have a perfect circle
plt.axis("equal")
# Save an image of our chart and print the final product to the screen
plt.savefig("../Images/PyPies.png")
plt.show()

```
{{% /expand%}}