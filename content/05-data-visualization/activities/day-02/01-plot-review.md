+++
title = "01. Plots Review  👩‍🎓👨‍🎓"
weight = 1
tags = ["matplotlib"] 
+++

# PyPlot Warmup

In this activity, you will use PyPlot to create the most effective visualization for a variety of datasets.

## Instructions

* Examine the starter code for each dataset.

* Determine what chart or plot fits with the starter code for each dataset.

* Complete the code block to create a plot for each of the datasets.

* Be sure to provide each plot with a title and labels.

## Hint

If you are unsure about what type of data is contained in the starter code, print it out!

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Import Dependencies
import numpy as np
import matplotlib.pyplot as plt
# DATA SET 1
gyms = ["Crunch", "Planet Fitness", "NY Sports Club", "Rickie's Gym"]
members = [49, 92, 84, 53]
x_axis = np.arange(0, len(gyms))
tick_locations = []
for x in x_axis:
    tick_locations.append(x)

plt.title("NYC Gym Popularity")
plt.xlabel("Gym Name")
plt.ylabel("Number of Members")

plt.xlim(-0.75, len(gyms)-.25)
plt.ylim(0, max(members) + 5)

plt.bar(x_axis, members, facecolor="red", alpha=0.75, align="center")
plt.xticks(tick_locations, gyms)
plt.show()

# DATA SET 2
x_lim = 2 * np.pi
x_axis = np.arange(0, x_lim, 0.1)
sin = np.sin(x_axis)
plt.title("Sin from 0 to 2$\pi$")
plt.xlabel("Real Numbers from 0 to 2$\pi$")
plt.ylabel("sin(x)")

plt.hlines(0, 0, x_lim, alpha=0.2)
plt.xlim(0, x_lim)
plt.ylim(-1.25, 1.25)

plt.plot(x_axis, sin, marker="o", color="red", linewidth=1)
plt.show()

# DATA SET 3
gyms = ["Crunch", "Planet Fitness", "NY Sports Club", "Rickie's Gym"]
members = [49, 92, 84, 53]
colors = ["yellowgreen", "red", "lightcoral", "lightskyblue"]
explode = (0, 0.05, 0, 0)
plt.title("NYC Gym Popularity")
plt.pie(members, explode=explode, labels=gyms, colors=colors,
        autopct="%1.1f%%", shadow=True, startangle=90)
plt.axis("equal")
plt.show()

# DATA SET 4
x_axis = np.arange(0, 10, 0.1)
times = []
for x in x_axis:
    times.append(x * x + np.random.randint(0, np.ceil(max(x_axis))))
plt.title("Running Time of FakeSort for Sample Input Sizes")
plt.xlabel("Length of Input Array")
plt.ylabel("Time to Sort (s)")

plt.scatter(x_axis, times, marker="o", color="red")
plt.show()
```
{{% /expand%}}