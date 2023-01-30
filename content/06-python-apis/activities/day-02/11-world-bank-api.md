+++
title = "11. World Bank API  👩‍🏫🧑‍🏫"
weight = 11
tags = ["apis"] 
+++

```python
# Dependencies
import requests

url = "http://api.worldbank.org/v2/"
api_format = "json"

# Get country information in JSON format
countries_response = requests.get(f"{url}countries?format={api_format}").json()

# First element is general information, second is countries themselves
countries = countries_response[1]
# Report the names
for country in countries:
    print(country["name"])
```