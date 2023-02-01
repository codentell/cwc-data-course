+++
title = "06. Chi Square 👩‍🏫🧑‍🏫"
weight = 6
tags = ["project"] 
+++

```python

import numpy as np
import pandas as pd
# The statistical module used to run chi square test
import scipy.stats as stats
# Observed data in a (hypothetical) survey of 300 people 
observed = pd.Series([220,55,25], index=["omnivores", "carnivores", "herbivores"])
# Create a data frame
df = pd.DataFrame([observed]).T
# Add a column whose default values are the expected values
df[1] = 100
# Rename columns
df.columns = ["observed", "expected"]
# View the data frame
df

# The degree of freedom is 3-1 = 2
# With a p-value of 0.05, the confidence level is 1.00-0.05 = 0.95.
critical_value = stats.chi2.ppf(q = 0.95, df = 2)
# The critical value
critical_value
5.99146454710798
# Run the chi square test with stats.chisquare()
stats.chisquare(df['observed'], df['expected'])

# Conclusion
# Since the chi square value of 220.5 exceeds the critical value of 5.99, we conclude that the results are statistically significant.
 

```