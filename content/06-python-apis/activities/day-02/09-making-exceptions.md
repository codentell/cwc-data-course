+++
title = "09. Making Exceptions 👩‍🎓👨‍🎓"
weight = 9
tags = ["apis"] 
+++

# Making Exceptions

In this activity, you will create an application that uses `try` and `except` to resolve a number of errors.

## Instructions

* Without removing any of the lines from the provided starter code, create try-except blocks that will allow the application to run without terminating.

* Each `except` block should handle the specific error that will occur.

* Add a `print` statement under the `except` block to log the error.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Your assignment is to get the last line to print without changing any
# of the code below. Instead, wrap each line that throws an error in a
# try/exept block.

try:
    print("Infinity looks like + " + str(10 / 0) + ".")
except ZeroDivisionError:
    print("Woops. Can't do that.")

try:
    print("I think her name was + " + name + "?")
except NameError:
    print("Oh, I forgot to define 'name'. D'oh.")

try:
    print("Your name is a nonsense number. Look: " + int("Gabriel"))
except ValueError:
    print("Drat. 'Gabriel' isn't a number?")

print("I made it through the gauntlet. The message survived!")
```
{{% /expand%}}