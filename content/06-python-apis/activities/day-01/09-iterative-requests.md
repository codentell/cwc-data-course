+++
title = "09. Iterative Requests 👩‍🏫🧑‍🏫"
weight = 9
tags = ["apis"] 
+++


```python

# Dependencies
import random
import json
import requests

# Let's get the JSON for 100 posts sequentially.
url = "http://jsonplaceholder.typicode.com/posts/"
# Create an empty list to store the responses
response_json = []
# Create random indices representing
# a user's choice of posts
indices = random.sample(list(range(1, 100)), 10)
indices

# Make a request for each of the indices
for x in range(len(indices)):
    print(f"Making request number: {x} for ID: {indices[x]}")

    # Get one of the posts
    post_response = requests.get(url + str(indices[x]))

    # Save post's JSON
    response_json.append(post_response.json())


 


```