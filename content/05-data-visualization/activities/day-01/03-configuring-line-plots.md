+++
title = "03. Configuring Line Plots 👩‍🏫🧑‍🏫"
weight = 3
tags = ["matplotlib"] 
+++

```python

%matplotlib notebook
# Dependencies
import matplotlib.pyplot as plt
import numpy as np
# Set x axis and variables
x_axis = np.arange(0, 10, 0.1)
sin = np.sin(x_axis)
cos = np.cos(x_axis)
# Draw a horizontal line with 0.25 transparency
plt.hlines(0, 0, 10, alpha=0.25)


# Assign plots to tuples that stores result of plot

# Each point on the sine chart is marked by a blue circle
sine_handle, = plt.plot(x_axis, sin, marker ='o', color='blue', label="Sine")
# Each point on the cosine chart is marked by a red triangle
cosine_handle, = plt.plot(x_axis, cos, marker='^', color='red', label="Cosine")
# Adds a legend and sets its location to the lower right
plt.legend(loc="lower right")

# Saves an image of our chart so that we can view it in a folder
plt.savefig("../Images/lineConfig.png")
plt.show()
 
 
```