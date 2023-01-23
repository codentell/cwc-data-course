+++
title = "03. Summary Statistics 👩‍🎓👨‍🎓"
weight = 3
tags = ["matplotlib"] 
+++

# Summary Statistics in Python

In this activity, you will be tasked with calculating a number of summary statistics using California housing data.

## Instructions

* Using Pandas, import the California housing dataset from the `Resources` folder.

* Determine the most appropriate measure of central tendency to describe the population, and then calculate this value.

* Use both data visualization and a quantitative measurement to find whether the age of houses in California is considered normally distributed using a small and large portion of the dataset.

* Examine the average occupancy of housing in California, and determine if there are any potential outliers in the dataset.

* If there are potential outliers in the average occupancy, find the minimum and maximum of the median housing prices across the outliers.

## Bonus

Plot the latitude and longitude of the California housing data using Matplotlib, and color the data points using the median income of the block. Does any location seem to be an outlier?

## References

U.S. Department of Commerce Bureau of the Census. (1990) 1990 Census of Housing General Housing Statistics: California. [https://www2.census.gov/library/publications/decennial/1990/ch-1/ch-1-6.pdf](https://www2.census.gov/library/publications/decennial/1990/ch-1/ch-1-6.pdf)

- - -


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Dependencies
import pandas as pd
import matplotlib.pyplot as plt
import scipy.stats as st
# Read in the california housing data set
california_data = pd.read_csv('../Resources/California_Housing.csv')
california_data.head()

# Get the information on the DataFrame
california_data.info()

# Determine which measure of central tendency is most appropriate to describe the Population
plt.hist(california_data['Population'])
plt.xlabel('Population')
plt.ylabel('Counts')
plt.show()
print(california_data['Population'].mean())
print(california_data['Population'].median())
print(california_data['Population'].mode())

# Determine if the house age in California is normally distributed using a small and large sample size. 
plt.hist(california_data['HouseAge'])
plt.xlabel('House Age (years)')
plt.ylabel('Counts')
plt.show()
print(st.normaltest(california_data["HouseAge"].sample(100)))
print(st.normaltest(california_data["HouseAge"].sample(2000)))


# Determine if there are any potential outliers in the average occupancy in California
quartiles = california_data['AveOccup'].quantile([.25,.5,.75])
lowerq = quartiles[0.25]
upperq = quartiles[0.75]
iqr = upperq-lowerq

print(f"The lower quartile of occupancy is: {lowerq}")
print(f"The upper quartile of occupancy is: {upperq}")
print(f"The interquartile range of occupancy is: {iqr}")
print(f"The the median of occupancy is: {quartiles[0.5]} ")

lower_bound = lowerq - (1.5*iqr)
upper_bound = upperq + (1.5*iqr)
print(f"Values below {lower_bound} could be outliers.")
print(f"Values above {upper_bound} could be outliers.")

outlier_occupancy = california_data.loc[(california_data['AveOccup'] < lower_bound) | (california_data['AveOccup'] > upper_bound)]
outlier_occupancy

# With the potential outliers, what is the lowest and highest median income (in $1000s) observed?
print(f"The minimum median income of the potential outliers is {outlier_occupancy['MedInc'].min()}")
print(f"The maximum median income of the potential outliers is {outlier_occupancy['MedInc'].max()}")

# Bonus - plot the latitude and longitude of the California housing data using Matplotlib, color the data points using the median income of the block.
plt.scatter(california_data['Longitude'],california_data['Latitude'],c=california_data['MedInc'])
clb = plt.colorbar()
plt.xlabel("Longitude")
plt.ylabel("Latitude")
clb.set_label("Median Income")
plt.show()

 
```
{{% /expand%}}