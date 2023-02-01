+++
title = "04. Anova 👩‍🏫🧑‍🏫"
weight = 4
tags = ["project"] 
+++

```python

import warnings
warnings.filterwarnings('ignore')
%matplotlib inline
import pandas as pd
import scipy.stats as stats

# Comparison of 5 Durations of Workouts
# The problem: How do we know if working out on a regular basis will reduce overall average resting heart rate?

# The solution: ANOVA - does working out more regularly reduce average resting heart rate?

# Dataset: resting_heart_rate.csv
# Source: Internally generated data.

# Description: Comparison of people who work out during the week and average resting heart rate.

# Number of Workouts per week: 0=zero workouts, 1=one 30 minute workout, 2=two 30 minute workouts, 3=three 30 minute workouts, 4=four or more 30 minute workouts

df = pd.read_csv("../Resources/resting_heart_rate.csv")
df.head()

# Create a boxplot to compare means
df.boxplot("resting_heart_rate", by="num_workouts", figsize=(20, 10))


# Extract individual groups
group0 = df[df["num_workouts"] == 0]["resting_heart_rate"]
group1 = df[df["num_workouts"] == 1]["resting_heart_rate"]
group2 = df[df["num_workouts"] == 2]["resting_heart_rate"]
group3 = df[df["num_workouts"] == 3]["resting_heart_rate"]
group4 = df[df["num_workouts"] == 4]["resting_heart_rate"]
# Perform the ANOVA
stats.f_oneway(group0, group1, group2, group3, group4)

 

```