+++
title = "05. SEM and Error Bars 👩‍🎓👨‍🎓"
weight = 5
tags = ["matplotlib"] 
+++

# SEM and Error Bars

In this activity, you will work with a partner to characterize sample data from a California housing dataset. Make sure to compare your calculated values as you progress through the activity.

## Instructions

Work with a partner on this activity. Be sure to compare your calculated values as you progress through the activity.

* Execute the starter code to import the California housing dataset from Scikit-learn.

    * Create a sample set of median housing prices using Pandas. Set the sample size to 20.

    * Calculate the means and standard errors for each sample.

    * Create a plot displaying the means for each sample, with the standard error as error bars.

    * Calculate the range of SEM values across the sample set.

    * Determine which sample's mean is closest to the population mean.

    * Compare this sample's mean to the population's mean.

    * Rerun your sampling code a few times to generate new sample sets. Try changing the sample size and then rerunning the sampling code.

* Discuss with your partner what changes you observe when sample size changes.

## References

[Scikit-learn’s California housing dataset](https://scikit-learn.org/stable/modules/generated/sklearn.datasets.fetch_california_housing.html)

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

%matplotlib notebook
# Import dependencies
from matplotlib import pyplot as plt
import numpy as np
import pandas as pd
from sklearn.datasets import fetch_california_housing
from scipy.stats import sem

# Import the California housing data set and get description
california_dataset = fetch_california_housing()

print(california_dataset.DESCR)


# Read California housing data into a Pandas dataframe
housing_data = pd.DataFrame(data=california_dataset.data,columns=california_dataset.feature_names)
housing_data['MEDV'] = california_dataset.target
housing_data.head()

# Create a bunch of samples, each with sample size of 20
nsamples = 25
div = 20
samples = [housing_data.sample(div) for x in range(0,nsamples)]
# Calculate means
means = [s['MEDV'].mean() for s in samples]
# Calculate standard error on means
sems = [sem(s['MEDV']) for s in samples]
# Plot sample means with error bars
fig, ax = plt.subplots()
ax.errorbar(np.arange(0, len(samples), 1)+1,means, yerr=sems, fmt="o", color="b",
            alpha=0.5, label="Mean of House Prices")
ax.set_xlim(0, len(means)+1)
ax.set_xlabel("Sample Number")
ax.set_ylabel("Mean of Median House Prices ($100,000)")
plt.legend(loc="best", fontsize="small", fancybox=True)
plt.show()

# Calculate the range of SEM values
print(f"The range of SEM values in the sample set is {max(sems)-min(sems)}")

# Determine which sample's mean is closest to the population mean
print(f"The smallest SEM observed was {min(sems)}")
samp_index = sems.index(min(sems))
print(f"The sample with the smallest SEM is sample {samp_index+1}")

# Compare to the population mean
print(f"The mean of the sample 5 is {samples[samp_index]['MEDV'].mean()}")
print(f"The mean of the population data set is {housing_data['MEDV'].mean()}")
```
{{% /expand%}}