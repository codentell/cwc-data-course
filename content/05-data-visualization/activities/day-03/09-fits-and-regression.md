+++
title = "09. Fits and Regression 👩‍🎓👨‍🎓"
weight = 9
tags = ["matplotlib"] 
+++

# Fits and Regression

This activity is an opportunity to use SciPy to fit data and Matplotlib to display the fit.

## Instructions

* Generate a scatter plot with Matplotlib using the year as the independent (*x*) variable and the number of petrol-electric cars as the dependent (*y*) variable.

* Use `stats.linregress` to perform a linear regression with the year as the independent variable (*x*) and the number of petrol-electric cars as the dependent variable (*y*).

* Use the information returned by `stats.linregress` to create the equation of a line from the model.

* Calculate the predicted number of petrol-electric cars of the linear model using the year as the *x* values.

* Plot the linear model of year versus number of petrol-electric cars on top of your scatter plot.

  * Your scatter plot and line plot share the same axis.

  * To overlay plots in a notebook, the plots must be in the same code block.

* Repeat the process of generating a scatter plot, calculating the linear regression model, and plotting the regression line over the scatter plot for the following pairs of variables:

  * Year versus number of petrol cars.

  * Year versus number of diesel cars.

## Bonus

* Use `pyplot.subplots` from Matplotlib to create a new figure that displays all three pairs of variables on the same plot. For each pair of variables, there should be a scatter plot and a regression line.

  * All three plots share the same x-axis.

* Use the regression lines you created to predict what the number of petrol-electric, petrol, and diesel cars will be in 2024.

## Hint

* Review the documentation for [stats.linregress](https://docs.scipy.org/doc/scipy/reference/generated/scipy.stats.linregress.html).

* Recall that `stats.linregress` returns a slope, called *m*, and a *y* intercept, called *b*. These let you define a line for each fit simply by writing `y-values = m * x-values + b` for each linear regression you perform.

## References

Singapore Land Transport Authority. (2022). Annual Motor Vehicle Population by Type of Fuel Used. [https://data.gov.sg/dataset/annual-motor-vehicle-population-by-type-of-fuel-used](https://data.gov.sg/dataset/annual-motor-vehicle-population-by-type-of-fuel-used)

- - -


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Dependencies
from matplotlib import pyplot as plt
from scipy import stats
import numpy as np
import pandas as pd
# Load vehicle data set into pandas
vehicle_data = pd.read_csv("../Resources/singapore-motor-vehicle-population.csv")
vehicle_data.head()

# Generate a scatter plot of year versus number of petrol-electric cars
year = vehicle_data.loc[(vehicle_data["type"]=="Cars") & (vehicle_data["engine"]=="Petrol-Electric"),"year"]
petrol_electric_cars = vehicle_data.loc[(vehicle_data["type"]=="Cars") & (vehicle_data["engine"]=="Petrol-Electric"),"number"]
plt.scatter(year,petrol_electric_cars)
plt.xticks(year, rotation=90)
plt.xlabel('Year')
plt.ylabel('Petrol Electric Cars')
plt.show()

# Perform a linear regression on year versus petrol-electric cars
pe_slope, pe_int, pe_r, pe_p, pe_std_err = stats.linregress(year, petrol_electric_cars)
# Create equation of line to calculate predicted number of petrol-electric cars
pe_fit = pe_slope * year + pe_int
# Plot the linear model on top of scatter plot 
year = vehicle_data.loc[(vehicle_data["type"]=="Cars") & (vehicle_data["engine"]=="Petrol-Electric"),"year"]
petrol_electric_cars = vehicle_data.loc[(vehicle_data["type"]=="Cars") & (vehicle_data["engine"]=="Petrol-Electric"),"number"]
plt.scatter(year,petrol_electric_cars)
plt.plot(year,pe_fit,"--")
plt.xticks(year, rotation=90)
plt.xlabel('Year')
plt.ylabel('Petrol Electric Cars')
plt.show()

# Repeat plotting scatter and linear model for year versus petrol cars
petrol_cars = vehicle_data.loc[(vehicle_data["type"]=="Cars") & (vehicle_data["engine"]=="Petrol"), "number"]
p_slope, p_int, p_r, p_p, p_std_err = stats.linregress(year, petrol_cars)
p_fit = p_slope * year + p_int
plt.scatter(year,petrol_cars)
plt.plot(year,p_fit,"--")
plt.xticks(year, rotation=90)
plt.xlabel('Year')
plt.ylabel('Petrol Cars')
plt.show()

# Repeat plotting scatter and linear model for year versus electric cars
diesel_cars = vehicle_data.loc[(vehicle_data["type"]=="Cars") & (vehicle_data["engine"]=="Diesel"), "number"]
d_slope, d_int, d_r, d_p, d_std_err = stats.linregress(
    year, diesel_cars)
d_fit = d_slope * year + d_int
plt.scatter(year,diesel_cars)
plt.plot(year,d_fit,"--")
plt.xticks(year, rotation=90)
plt.xlabel('Year')
plt.ylabel('Diesel Cars')
plt.show()

# Generate a facet plot of all 3 figures
fig, (ax1, ax2, ax3) = plt.subplots(3, sharex=True)
fig.suptitle("Number of Vehicles Over Time", fontsize=16, fontweight="bold")

ax1.set_xlim(min(year), max(year))
ax1.plot(year, petrol_electric_cars, linewidth=1, marker="o")
ax1.plot(year, pe_fit, "b--", linewidth=1)
ax1.set_ylabel("Petrol-Electric Cars")

ax2.plot(year, petrol_cars, linewidth=1, marker="o", color="y")
ax2.plot(year, p_fit, "y--", linewidth=1)
ax2.set_ylabel("Petrol Cars")

ax3.plot(year, diesel_cars, linewidth=1, marker="o", color="g")
ax3.plot(year, d_fit, "g--", linewidth=1)
ax3.set_ylabel("Diesel Cars")
ax3.set_xlabel("Year")

plt.show()

# Calculate the number of cars for 2024
year = 2024
print(f"The number of petrol-electic cars in 2024 will be {round(pe_slope * year + pe_int,0)}.")
print(f"The number of petrol cars in 2024 will be {round(p_slope * year + p_int,0)}.")
print(f"The number of diesel cars in 2024 will be {round(d_slope * year + d_int,0)}.")

```
{{% /expand%}}