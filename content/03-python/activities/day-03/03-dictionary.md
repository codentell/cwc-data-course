+++
title = "03 Dictionary  👩‍🎓👨‍🎓"
weight = 3
tags = ["python"] 
+++


In this activity, you will create and access dictionaries that are based on your own hobbies.

## Instructions

1. Create a dictionary to store the following information:

* Your name
* Your age
* A list of a few of your hobbies
* A dictionary that includes a few days and the time you typically wake up on those days

2. Print out your name, how many hobbies you have, and a time you typically wake up during the week.

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
# Dictionary full of info
my_info = {"name": "Rex",
           "occupation": "dog",
           "age": 21,
           "hobbies": ["barking", "eating", "sleeping", "loving my owner"],
           "wake-up": {"Mon": 5, "Friday": 5, "Saturday": 10, "Sunday": 9}}

# Print out results are stored in the dictionary
print(f'Hello I am {my_info["name"]} and I am a {my_info["occupation"]}')
print(f'I have {len(my_info["hobbies"])} hobbies!')
print(f'On the weekend I get up at {my_info["wake-up"]["Saturday"]}')
```
{{% /expand%}}