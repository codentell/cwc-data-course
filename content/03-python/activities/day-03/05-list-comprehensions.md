+++
title = "05 List Comprehensions 👩‍🎓👨‍🎓"
weight = 5
tags = ["python"] 
+++


In this activity, you’ll use list comprehensions to compose a wedding invitation, which you will send to every name on your mailing list.

## Instructions

* Fill the cell below.

* Run the provided program. Note that nothing forces you to write the name properly in title case&mdash;for example, as "Jane" instead of "jAnE". You will use list comprehensions to fix this.

  * First, use list comprehensions to create a new list that contains the lowercase version of each of the names your user provided.

  * Then, use list comprehensions to create a new list that contains the title-case versions of each of the names in your lowercase list.

## Hint

* Check out the documentation for the [title method](https://docs.python.org/3/library/stdtypes.html#str.title).

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
names = []
for _ in range(5):
    name = input("Please enter the name of someone you know. ")
    names.append(name)

lowercased = [name.lower() for name in names]
title cased = [name.title() for name in lowercased]
invitations = [
    f"Dear {name}, please come to the wedding this Saturday!" for name in title cased]

for invitation in invitations:
    print(invitation)
```

{{% /expand%}}


