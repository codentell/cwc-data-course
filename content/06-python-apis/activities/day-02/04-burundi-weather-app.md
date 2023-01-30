+++
title = "04. Burundi Weather App 👩‍🎓👨‍🎓"
weight = 4
tags = ["apis"] 
+++

# Weather in Bujumbura

This activity gives students practice with making API calls and handling responses.

## Instructions

* Save all of your "config" information—i.e., your API key; the base URL; etc.—before moving on.

* Build your query URL.

* **Hint:** Check the documentation to figure out how to request temperatures in Celsius.

* Make your request, and save the API response.

* Retrieve the current temperature in Bujumbura from the JSON response.

* Print the temperature to the console.

## Bonus

* Augment your code to report the temperature in both Fahrenheit _and_ Celsius.

* **Note:** Don't forget to change the API key in config.py!

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python


# Dependencies
import requests
from config import api_key

# Save config information.
url = "http://api.openweathermap.org/data/2.5/weather?"
city = "Bujumbura"
units = "metric"
# Build query URL and request your results in Celsius
query_url = f"{url}appid={api_key}&q={city}&units={units}"

# Get weather data
weather_response = requests.get(query_url)
weather_json = weather_response.json()
# Get temperature from JSON response
temperature = weather_json["main"]["temp"]
# Report temperature
print(f"The temperature in Bujumbura is {temperature} C.")
The temperature in Bujumbura is 16.81 C.
# BONUS

# use list of units
units = ["metric", "imperial"]

# set up list to hold two different temperatures
temperatures = []

# loop through the list of units and append them to temperatures list
for unit in units:
    # Build query URL based on current element in units
    query_url = url + "appid=" + api_key + "&q=" + city + "&units=" + unit

    # Get weather data
    weather_response = requests.get(query_url)
    weather_json = weather_response.json()

    # Get temperature from JSON response
    temperature = weather_json["main"]["temp"]

    temperatures.append(temperature)

# Report temperatures by accessing each element in the list
print(
    f"The temperature in Bujumbura is {temperatures[0]}C or {temperatures[1]}F.")


```
{{% /expand%}}