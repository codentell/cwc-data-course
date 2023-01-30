+++
title = "02. Request Review👩‍🎓👨‍🎓"
weight = 2
tags = ["apis"] 
+++

# Requests & Responses

This activity provides practice making requests, converting the response to JSON, and then manipulating the result with Python.

## Instructions

* Make a request to the following endpoint (<https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.1/06-Python-APIs/request_review.json>), and store the response.

* Print the JSON representations of the first and last posts.

* Print number of posts received.

## References

Data Source: Mockaroo, LLC. (2021). Realistic Data Generator. [https://www.mockaroo.com/](https://www.mockaroo.com/)

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Dependencies
import json
import requests 
from pprint import pprint
# Specify the URL
url = "https://2u-data-curriculum-team.s3.amazonaws.com/dataviz-classroom/v1.1/06-Python-APIs/request_review.json"

# Make request and store response
response = requests.get(url)

# Verify status code
response.status_code

# JSON-ify response
response_json = response.json()
# Print first and last articles
pprint(f"The first response is {response_json[0]}.")
pprint(f"The last response is {response_json[-1]}.")


print(f"We received {len(response_json)} responses.")

 
```
{{% /expand%}}