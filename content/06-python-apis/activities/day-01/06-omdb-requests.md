+++
title = "06. OMDb Requests  👩‍🏫🧑‍🏫"
weight = 6
tags = ["apis"] 
+++

```python

import requests
import json
from config import api_key
# New Dependency! Use this to pretty print the JSON
# https://docs.python.org/3/library/pprint.html
from pprint import pprint
# Note that the ?t= is a query param for the t-itle of the
# movie we want to search for.
url = "http://www.omdbapi.com/?t="
api_key = "&apikey=" + api_key
# Performing a GET request similar to the one we executed
# earlier
response = requests.get(url + "Aliens" + api_key)
# Converting the response to JSON, and printing the result.
data = response.json()
pprint(data)

# Print a few keys from the response JSON.
print(f"Movie was directed by {data['Director']}.")
print(f"Movie was released in {data['Country']}.")

 

```