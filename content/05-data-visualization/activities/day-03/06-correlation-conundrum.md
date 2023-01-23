+++
title = "06. Correlation Conundrum 👩‍🏫🧑‍🏫"
weight = 6
tags = ["matplotlib"] 
+++

```python

# Dependencies
import pandas as pd
import matplotlib.pyplot as plt
import scipy.stats as st
# Import the WDI dataset, drop missing data
wdi_data = pd.read_csv('../Resources/WDI_2018.csv')
wdi_data = wdi_data.dropna()
wdi_data.head()
	
# For the first example, determine which pairs of factors are correlated. 
plt.scatter(wdi_data.iloc[:,1],wdi_data.iloc[:,8])
plt.xlabel('Income Per Capita')
plt.ylabel('Average Alcohol Consumed Per Person Per Year (L)')
plt.show()

plt.scatter(wdi_data.iloc[:,3],wdi_data.iloc[:,10])
plt.xlabel('Population Median Age')
plt.ylabel('Cell Phones Per 100 People')
plt.show()

plt.scatter(wdi_data.iloc[:,9],wdi_data.iloc[:,7])
plt.xlabel('% Population with Access to Clean Water')
plt.ylabel('Male Life Expectancy')
plt.show()

plt.scatter(wdi_data.iloc[:,1],wdi_data.iloc[:,12])
plt.xlabel('Income Per Capita')
plt.ylabel('% Measles Immunization')
plt.show()

# The next example will compute the Pearson correlation coefficient between "Income per Capita" and "Average Alcohol Consumed"
income = wdi_data.iloc[:,1]
alcohol = wdi_data.iloc[:,8]
correlation = st.pearsonr(income,alcohol)
print(f"The correlation between both factors is {round(correlation[0],2)}")

# Compare the calcualted Pearson's r to the plots
plt.scatter(income,alcohol)
plt.xlabel('Income Per Capita')
plt.ylabel('Average Alcohol Consumed Per Person Per Year (L)')
print(f"The correlation between both factors is {round(correlation[0],2)}")
plt.show()

age = wdi_data.iloc[:,3]
cell_phones = wdi_data.iloc[:,10]
correlation = st.pearsonr(age,cell_phones)
plt.scatter(age,cell_phones)
plt.xlabel('Population Median Age')
plt.ylabel('Cell Phones Per 100 People')
print(f"The correlation between both factors is {round(correlation[0],2)}")
plt.show()

water = wdi_data.iloc[:,9]
life = wdi_data.iloc[:,7]
correlation = st.pearsonr(water,life)
plt.scatter(water,life)
plt.xlabel('% Population with Access to Clean Water')
plt.ylabel('Male Life Expectancy')
print(f"The correlation between both factors is {round(correlation[0],2)}")
plt.show()

income = wdi_data.iloc[:,1]
measles = wdi_data.iloc[:,12]
correlation = st.pearsonr(income,measles)
plt.scatter(income,measles)
plt.xlabel('Income Per Capita')
plt.ylabel('% Measles Immunization')
print(f"The correlation between both factors is {round(correlation[0],2)}")
plt.show()

 
```