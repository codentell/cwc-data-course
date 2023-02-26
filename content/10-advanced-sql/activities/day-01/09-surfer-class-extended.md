+++
title = "09. Surfer Class Extended 👩‍🎓👨‍🎓 "
weight = 9
tags = ["advanced sql"] 
+++

In this activity, you will rework your `Surfer` script as you add in methods to perform specific tasks.

## Instructions

* Create a `Surfer` class that has `name`, `hometown`, `rank`, and `wipeouts` instance variables.

* Create a method called `speak` that prints "Hang loose, bruh!"

* Create a method called `biography` that prints the surfer's name and hometown.

* Create a method called `cheer` that will print "I totally rock man, no wipeouts!" if the surfer has no wipeouts. Otherwise, it prints “Bummer, bruh, keep on keeping on!”

* Create two surfer instances of the Surfer class, and run all the methods.

## Bonus

Add a method to your class that prints out how many surfers are currently “shredding.”

## Hint

* Create a class variable shared by all instances of `Surfer`, and create an instance variable to increment it each time a new surfer is created.

* For more on class syntax and examples, refer to the [Python documentation on classes](https://docs.python.org/3/tutorial/classes.html).

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Define the Surfer Class
class Surfer():

    # Keep track of surfer count as they are created
    surferCount = 0

    # Constructor
    # --------------------------------------------------------------------------------
    # Initialize the surfer and assign each surfer a new surfer count upon creation
    def __init__(self, name, hometown, rank, wipeouts=0):
        self.name = name
        self.hometown = hometown
        self.rank = rank
        self.wipeouts = wipeouts
        Surfer.surferCount += 1

    # Class Methods
    # --------------------------------------------------------------------------------
    # Prints what number surfer they are based on when they were created
    def surfer_count(self):
         print("Total surfers shredding waves %d" % Surfer.surferCount)

    # Prints out simple string
    def speak(self):
        print("Hang loose bruh!")

    # Interpolates based on their attributes
    def biography(self):
        print(f"My name is {self.name}, I am from {self.hometown} and rank #{self.rank}, I've wiped out {self.wipeouts} times!")

    # Check how many wipeouts and print out a statement
    def cheer(self):
        if self.wipeouts == 0:
            print('I totally rock man, no wipeouts!')
        else:
            print('Bummer bruh, keep on keeping on!')

# Create Surfers
# --------------------------------------------------------------------------------

surfer = Surfer('Kelly Slater', 'Cocoa Beach', 1,)
print(surfer.name)
print(surfer.hometown)
print(surfer.rank)
print(surfer.wipeouts)
surfer.speak()
surfer.biography()
surfer.cheer()
surfer.surfer_count()

surfer = Surfer('John Breezy', 'Spring Lake', 1, 10)
print(surfer.name)
print(surfer.hometown)
print(surfer.rank)
print(surfer.wipeouts)
surfer.speak()
surfer.biography()
surfer.cheer()
surfer.surfer_count()

```
{{% /expand%}}