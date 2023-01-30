+++
title = "10. API Exceptions 👩‍🎓👨‍🎓"
weight = 10
tags = ["apis"] 
+++

# API Exceptions

Not every call placed to an API will return a result. In this activity, you will use `try` and `except` to handle errors from API calls.

## Instructions

* Loop through the characters in the list, and send a request to the Star Wars API.

* Create a `try` clause and an `except` clause. In the `try` clause, append the height, mass, and character name that is available in the Star Wars API to their respective lists. If the character is not available in the Star Wars API, use the `except` clause to print a message and `pass`.

* Create a DataFrame from the results.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

import json
import requests
import pandas as pd
# List of character
search_characters = ['R2-D2', 'Darth Vader', 'Godzilla', 'Luke Skywalker', 'Frodo', \
              'Boba Fett', 'Iron Man', 'Jon Snow', 'Han Solo']

# Set url for API
url = 'https://swapi.dev/api/people/?search='

# Set empty lists to hold characters height and mass
height = []
mass = []
starwars_characters = []

# Loop through each character
for character in search_characters:
    
    # Create search query, make request and store in json
    query = url + character
    response = requests.get(query)
    response_json = response.json()
    
    # Try to grab the height and mass of characters if they are available in the Star Wars API
    try:
        height.append(response_json['results'][0]['height'])
        mass.append(response_json['results'][0]['mass'])
        starwars_characters.append(character)
        print(f"{character} found! Appending stats")
        
    # Handle exceptions for a character that is not available in the Star Wars API
    except:
        # Append null values
        print("Character not found")
        pass

# Create DataFrame
character_height = pd.DataFrame({
    'character': starwars_characters,
    'height': height,
    'mass': mass
})
character_height

 
```
{{% /expand%}}