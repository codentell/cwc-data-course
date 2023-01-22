+++
title = "01. Basic Line Graphs 👩‍🏫🧑‍🏫"
weight = 1
tags = ["matplotlib"] 
+++

### exponential chart

```python

# Import Numpy for calculations and matplotlib for charting
import numpy as np
import matplotlib.pyplot as plt
# Creates a numpy array from 0 to 5 with each step being 0.1 higher than the last
x_axis = np.arange(0, 5, 0.1)
x_axis

# Creates an exponential series of values which we can then chart
e_x = [np.exp(x) for x in x_axis]
e_x

# Create a graph based upon the list and array we have created
plt.plot(x_axis, e_x)
# Show the graph that we have created
plt.show()

# Give our graph axis labels
plt.xlabel("Time With MatPlotLib")
plt.ylabel("How Cool MatPlotLib Seems")

# Have to plot our chart once again as it doesn't stick after being shown
plt.plot(x_axis, e_x)
plt.show() 
```

### sin cos

```python
# Import Numpy for calculations and matplotlib for charting
import numpy as np
import matplotlib.pyplot as plt
# Create our x_axis numpy array
x_axis = np.arange(0, 6, 0.1)
# Creates a numpy array based on the sin of our x_axis values
sin = np.sin(x_axis)
# Creates a numpy array based on the cos of our x_axis values
cos = np.cos(x_axis)
# Plot both of these lines so that they will appear on our final chart
plt.plot(x_axis, sin)
plt.plot(x_axis, cos)

plt.show()
```