+++
title = "04. Hello Variable World 👩‍🎓👨‍🎓"
weight = 4
tags = ["python"] 
+++

# Hello, Variable World

In this activity, you will create a simple Python application that uses variables to run calculations on integers and print strings out to the console.

## Instructions

* Create two variables, called `name` and `country`, that will hold strings.

* Create two variables, called `age` and `hourly_wage`, that will hold integers.

* Create a variable called `satisfied`, which will hold a Boolean.

* Create a variable called `daily_wage`, which will hold the value of `hourly_wage` multiplied by 8.

* Use traditional string concatenation to print the `name`, `country`, `age`, and `hourly_wage` variables.

* With an `f-string`, print the `daily_wage` and `satisfied` variables.

## Hint

For additional help with f-strings, visit [Python 3's f-Strings](https://realpython.com/python-f-strings/).

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
# Create a variable called 'country' that holds a string
country = "Australia"

# Create a variable called 'age' that holds an integer
age = 28

# Create a variable called 'hourly_wage' that holds an integer
hourly_wage = 25

# Calculate the daily wage for the user
daily_wage = hourly_wage * 8

# Create a variable called 'satisfied' that holds a boolean
satisfied = True

# Print out "Hello <name>!"
print("Hello " + name + "!")

# Print out what country the user entered
print("You live in " + country)

# Print out the user's age
print("You are " + str(age) + " years old")

# With an f-string, print out the daily wage that was calculated
print(f"You make {daily_wage} per day")

# With an f-string, print out whether the users were satisfied
print(f"Are you satisfied with your current wage? {satisfied}")
```


{{% /expand%}}

