+++
title = "06. TV Rating DataFrame 👩‍🎓👨‍🎓"
weight = 6
tags = ["apis"] 
+++

# TV Ratings

In this activity, you will create an application that reads in a list of TV shows, makes multiple requests from an API to retrieve rating information, creates a Pandas DataFrame, and then visually displays the data.

## Instructions

* You may use the list of TV shows provided in the starter file or create your own.

* Request information on each TV show from the [TVmaze API's Show Search endpoint](https://www.tvmaze.com/api#show-search)

* Store the name and rating information into lists.

* Store this data in a dictionary, and use it to create a Pandas DataFrame.

* Use Pandas to create a bar chart comparing the ratings of each show.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

#Dependencies
import requests
import json
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
# list of tv show titles to query
tv_shows = ["Altered Carbon", "Grey's Anatomy", "This is Us", "The Flash",
            "Vikings", "Shameless", "Arrow", "Peaky Blinders", "Dirk Gently"]

# tv maze show search base url
base_url = "http://api.tvmaze.com/search/shows?q="

# set up lists to hold response data for name and rating
titles = []
ratings = []

# loop through tv show titles, make requests and parse
for show in tv_shows:
    target_url = base_url + show
    response = requests.get(target_url).json()
    titles.append(response[0]['show']['name'])
    ratings.append(response[0]['show']['rating']['average'])
# create dataframe
shows_df = pd.DataFrame({
    "title": titles,
    "rating": ratings
})


shows_df.plot('title', 'rating', kind='bar', figsize=(10,5), rot=45)


```
{{% /expand%}}