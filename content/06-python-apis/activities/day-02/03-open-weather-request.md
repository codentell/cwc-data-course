+++
title = "03. Open Weather Request  👩‍🏫🧑‍🏫"
weight = 3
tags = ["apis"] 
+++

```python

# Dependencies
import json
import requests
from config import api_key
# Save config information
url = "http://api.openweathermap.org/data/2.5/weather?"
city = "London"

# Build query URL
query_url = url + "appid=" + api_key + "&q=" + city
# Get weather data
weather_response = requests.get(query_url)
weather_json = weather_response.json()

# Get the temperature from the response
print(f"The weather API responded with: {weather_json}.")

```
