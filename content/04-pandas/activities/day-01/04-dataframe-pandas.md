+++
title = "04.  DataFrame Pandas 👩‍🎓👨‍🎓"
weight = 4
tags = ["pandas"] 
+++
 
In this activity, you will create DataFrames from scratch using both a list of dictionaries and a dictionary of lists.

## Instructions

* Create a DataFrame for a frame shop. The DataFrame should contain three columns,  "Frame", "Price", and "Sales", and have five rows of data stored within it.

* Using an alternative method, create a DataFrame for an art gallery. The DataFrame should contain three columns, "Painting", "Price", and "Popularity", and have four rows of data stored within it.

## Bonus

Once both DataFrames have been created, discuss which method you preferred and why.

---

```python
# Import Dependencies
import pandas as pd

# Create a DataFrame of frames using a dictionary of lists
frame_df = pd.DataFrame({
    "Frame": ["Ornate", "Classical", "Modern", "Wood", "Cardboard"],
    "Price": [15.00, 12.50, 10.00, 5.00, 1.00],
    "Sales": [100, 200, 150, 300, "N/A"]
})
frame_df

# Create a DataFrame of paintings using a list of dictionaries
painting_df = pd.DataFrame([
    {"Painting": "Mona Lisa (Knockoff)", "Price": 25,
     "Popularity": "Very Popular"},
    {"Painting": "Van Gogh (Knockoff)", "Price": 20, "Popularity": "Popular"},
    {"Painting": "Starving Artist", "Price": 10, "Popularity": "Average"},
    {"Painting": "Toddler Drawing", "Price": 1, "Popularity": "Not Popular"}
])
painting_df

```