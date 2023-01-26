+++
title = "11.  NYT API 👩‍🏫🧑‍🏫"
weight = 11
tags = ["apis"] 
+++


```python

# Dependencies
import requests
from pprint import pprint
from config import api_key

url = "https://api.nytimes.com/svc/search/v2/articlesearch.json?"
# Search for articles that mention granola
query = "granola"
# Build query URL
query_url = url + "api-key=" + api_key + "&q=" + query
# Request articles
articles = requests.get(query_url).json()

# The "response" property in articles contains the actual articles
# list comprehension.
articles_list = articles["response"]["docs"]
pprint(articles_list)

# Print the web_url of each stored article
print("Your Reading List")
for article in articles_list:
    print(article["web_url"])

 

```