+++
title = "03. Dow Dates 👩‍🎓👨‍🎓"
weight = 3
tags = ["sql"] 
+++


# Dates

In this activity, you will practice working with dates, both in SQLAlchemy and with the `datetime` library.

## Instructions

* Use the provided `dow.sqlite` dataset to analyze the average stock prices (average open, average high, average low, and average close) for all stocks in the month of May.

* Plot the results as a Pandas or Matplotlib bar chart.

## Bonus

* Calculate the high-low peak-to-peak (PTP) values for `IBM` stock after `2011-05-31`.

    * The high-low PTP is calculated by subtracting `low_price` from `high_price`.

* Use a `DateTime.date` object in the query filter.

* Use list comprehension to create a list of dictionaries from the query results.

* Create a DataFrame from the list of dictionaries.

* Use the `boxplot()` method on the DataFrame to plot PTP distribution statistics.

---

## References

Brown, Michael. (2013). Weekly Dow Jones Index Data. 10.13140/2.1.2729.4409.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python

# Setup
# Import dependencies.
import matplotlib
from matplotlib import style
style.use('fivethirtyeight')
import matplotlib.pyplot as plt
import pandas as pd

# Python SQL toolkit and Object Relational Mapper
import sqlalchemy
from sqlalchemy.ext.automap import automap_base
from sqlalchemy.orm import Session
from sqlalchemy import create_engine, text, inspect, func

engine = create_engine("sqlite:///../Resources/dow.sqlite", echo=False)

engine.execute(text('SELECT * FROM dow LIMIT 5')).fetchall()

inspector = inspect(engine)
columns = inspector.get_columns('dow')
for c in columns:
    print(c['name'], c["type"])

# Reflect and query dates
# Reflect Database into ORM class
Base = automap_base()
Base.prepare(autoload_with=engine)
Dow = Base.classes.dow
session = Session(engine)

# Analysis
# Analyze the Average prices (open, high, low, close) for all stocks in the Month of May

# Query for the stock and average prices (open, high, low, close) 
# for all stock in the month of May
# Sort the result by stock name
sel = [Dow.stock, 
       func.avg(Dow.open_price), 
       func.avg(Dow.high_price), 
       func.avg(Dow.low_price), 
       func.avg(Dow.close_price)]
may_averages = session.query(*sel).\
    filter(func.strftime("%m", Dow.date) == "05").\
    group_by(Dow.stock).\
    order_by(Dow.stock).all()
may_averages

# Plot the Results in a Matplotlib bar chart
df = pd.DataFrame(may_averages, columns=['stock', 'open_avg', 'high_avg', 'low_avg', 'close_avg'])
df.set_index('stock', inplace=True)
df.plot.bar()
plt.tight_layout()
plt.show()

# Bonus
# Calculate the high-low peak-to-peak (PTP) values for IBM stock after 2011-05-31.

# Note: high-low PTP is calculated using high_price - low_price
# Use a DateTime.date object in the query filter
# Use list comprehension to create a list of dictionaries from the query results
# Create a dataframe from the list of dictionaries
# Use the boxplot() method on the dataframe to plot PTP distribution statistics

# Design a query to calculate the PTP for stock `IBM` after May, 2011
import datetime as dt

date = dt.datetime(2011, 5, 31)

results = session.query(Dow.high_price - Dow.low_price, 
                        Dow.date).\
                  filter(Dow.date > date).filter(Dow.stock == 'IBM').all()

# List comprehension solution
ptp_rows = [{"Date": result[1], "PTP": result[0]} for result in results]
ptp_rows

# Load the list comprehension rows into a dataframe, set the index to the date, and plot the PTPs
pd.DataFrame(ptp_rows).set_index("Date").boxplot(patch_artist=True)
plt.title("IBM PTPs")
plt.show()



```
{{% /expand%}}