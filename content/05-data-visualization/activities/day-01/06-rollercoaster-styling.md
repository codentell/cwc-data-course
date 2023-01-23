+++
title = "06. Roller Coaster Styling 👩‍🎓👨‍🎓"
weight = 6
tags = ["matplotlib"] 
+++

# Coaster Speed

In this activity, you will create a line chart that graphs the speed of a roller coaster over time. You will then style the chart and add aesthetics to it.

## Instructions

* Create a visualization with two line plots using the following data:

  * `Danger Drop: [9, 8, 90, 85, 80, 70, 70, 65, 55, 60, 70, 65, 50]`

  * `RailGun: [75, 70, 60, 65, 60, 45, 55, 50, 40, 40, 35, 35, 30]`

* Both coasters are 120 seconds long, and the speed was measured every 10 seconds.

* Apply styling and labels that match the image provided:

  * Title: Coaster Speed Over Time.

  * x-axis label: Coaster Runtime.

  * y-axis label: Speed (mph).

  * Red line for Danger Drop, blue line for RailGun.

  * Include a grid on the chart.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

%matplotlib notebook
# Import Dependencies
import matplotlib.pyplot as plt
import numpy as np

# Create the X and Y axis lists
time = np.arange(0,130,10)
danger_drop_speeds = [9, 8, 90, 85, 80, 70, 70, 65, 55, 60, 70, 65, 50]
railgun_speeds = [75, 70, 60, 65, 60, 45, 55, 50, 40, 40, 35, 35, 30]
# Plot the charts and apply some styling
danger_drop, = plt.plot(time, danger_drop_speeds, color="red", label="Danger Drop")
railgun, = plt.plot(time, railgun_speeds, color="blue", label="RailGun")

# Add labels to X and Y axes :: Add title
plt.title("Coaster Speed Over Time")
plt.xlabel("Coaster Runtime")
plt.ylabel("Speed (MPH)")

# Set the limits for the X and Y axes
plt.xlim(0,120)
plt.ylim(5,95)


# Create a legend for the chart
plt.legend(handles=[danger_drop, railgun], loc="best")

# Add in a grid for the chart
plt.grid()
plt.show()
 
```
{{% /expand%}}