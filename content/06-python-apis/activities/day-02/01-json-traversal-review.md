+++
title = "01. JSON Traversal Review 👩‍🎓👨‍🎓"
weight = 1
tags = ["apis"] 
+++


# JSON Traversal Review

This activity is an opportunity to practice loading and parsing JSON in Python.

## Instructions

* Load the provided JSON.

* Retrieve the video's title.

* Retrieve the video's rating.

* Retrieve the link to the video's first tag.

* Retrieve the number of views for the video.

## References

Data Source:
Data for this dataset was generated by edX Boot Camps LLC, and is intended for educational purposes only.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python

# Dependencies
import json
import os

# Load JSON
filepath = os.path.join("..", "Resources", "video_api_response.json")
with open(filepath) as jsonfile:
    video_json = json.load(jsonfile)
# Isolate "data items" for easy reading
data = video_json["data"]
data_items = data["items"]

# Retrieve the video's title
title = data_items[0]["title"]
print("Title: ", title)

# Retrieve the video's rating
rating = data_items[0]["rating"]
print("Rating:", rating)

# Retrieve the link to the video's first tag
tag_one = data_items[0]["tags"][0]
print("Tags: ", tag_one)

# Retrieve the number of views this video has
view_count = data_items[0]["viewCount"]
print(f"View count: {view_count}")

 
```
{{% /expand%}}