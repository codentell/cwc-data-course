+++
title = "01. Geoapify Geocode  👩‍🏫🧑‍🏫"
weight = 1
tags = ["apis"] 
+++


```python

# Dependencies
import requests
import json

# Import the API key
from config import geoapify_key
# Target city
target_city = "Sydney, Australia"

# Build the endpoint URL
target_url = f"https://api.geoapify.com/v1/geocode/search?text={target_city}&format=json&apiKey={geoapify_key}"
target_url
'https://api.geoapify.com/v1/geocode/search?text=Sydney, Australia&format=json&apiKey=7757f89767bc454db74be2b640389f77'
# Run a request to endpoint and convert result to json
geo_data = requests.get(target_url).json()

# Print the json
print(geo_data)

# Print the json (pretty printed)
print(json.dumps(geo_data, indent=4, sort_keys=True))

# Extract latitude and longitude
lat = geo_data["results"][0]["lat"]
lon = geo_data["results"][0]["lon"]

# Print the latitude and longitude
print('''
    City: {0}
    Latitude: {1}
    Longitude: {2}
    '''.format(target_city, lat, lon))

 
```