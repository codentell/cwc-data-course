+++
title = "07. Surfer Class 👩‍🎓👨‍🎓"
weight = 7
tags = ["advanced sql"] 
+++

In this activity, you will create your own classes in Python.

## Instructions

* Create a class, `Surfer`, and initialize it with name, hometown, and rank-instance variables.

* Create an _instance_ of a surfer.

* Then, print the name, hometown, and rank of your surfer object.

## Bonus

* Create a `while` loop that will allow you to continuously create new instances of surfers using `input()`.

* Keep the loop going until otherwise specified by user input.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Define the Surfer Class
class Surfer():

  # Initialize the Surfer constructor 
  def __init__(self, name, hometown, rank):
    self.name = name + " " + "Dude"
    self.hometown = hometown + " " + "Waves"
    self.rank = rank
# Create an instance of the Surfer Class
surfer = Surfer('Kelly Slater', 'Cocoa Beach', 1)
# Print the object's attributes
print(surfer.name)
print(surfer.hometown)
print(surfer.rank)

# ----BONUS----
# Variable to keep track of changes to while loop
go = True

# While loop runs so long as go is True
while go:
    # Ask for user input and store answers within variables
    name = input("What is the surfer's name? ")
    hometown = input("What is the surfer's hometown? ")
    rank = int(input("What is the surfer's rank? "))

    # Create a new instance of the Surfer class using these values
    surfer = Surfer(name, hometown, rank)

    # Print the object's attributes
    print(surfer.name)
    print(surfer.hometown)
    print(surfer.rank)

    # Check to see if the user would like to continue
    check = input("Would you like to continue? (y/n) ")
    if(check.lower() == "y"):
        go = True
    else:
        go = False
```
{{% /expand%}}