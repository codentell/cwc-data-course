+++
title = "01. Request Intro  👩‍🏫🧑‍🏫"
weight = 1
tags = ["apis"] 
+++


```python
# Dependencies
import requests
import json


# URL for GET requests to retrieve vehicle data
url = "https://api.spacexdata.com/v4/launchpads"
# Print the response object to the console
print(requests.get(url))

# Retrieving data and converting it into JSON
print(requests.get(url).json())

# Pretty Print the output of the JSON
response = requests.get(url).json()
print(json.dumps(response, indent=4, sort_keys=True))

```