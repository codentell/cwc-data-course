+++
title = "02. Geoapify Places  👩‍🏫🧑‍🏫"
weight = 2
tags = ["apis"] 
+++

```python

Geoapify Places Demo
# Dependencies
import requests
import json

# Import the API key
from config import geoapify_key
# Set the geographical coordinates for Sydney, Australia
latitude = -33.8698439
longitude = 151.2082848

# Set the parameters for the type of place
categories = "catering.restaurant"
conditions = "vegetarian"
radius = 8000

# Set the parameters for the type of search
filters = f"circle:{longitude},{latitude},{radius}"
bias = f"proximity:{longitude},{latitude}"
limit = 20

# set up a parameters dictionary
params = {
    "categories":categories,
    "conditions":conditions,
    "limit":limit,
    "filter":filters,
    "bias":bias,
    "apiKey":geoapify_key    
}

# Set base URL
base_url = "https://api.geoapify.com/v2/places"

# run a request using our params dictionary
response = requests.get(base_url, params=params)
# print the response url, avoid doing for public github repos in order to avoid exposing key
print(response.url)

# convert response to json
places_data = response.json()

# Print the json (pretty printed)
print(json.dumps(places_data, indent=4, sort_keys=True))

# Print the name and address of the first restaurant that appears
print(places_data["features"][0]["properties"]["name"])
print(places_data["features"][0]["properties"]["address_line2"])

 
```