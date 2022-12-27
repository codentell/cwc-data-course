+++
title = "12.  Number Chain 👩‍🎓👨‍🎓"
weight = 12
tags = ["python"] 
+++


In this activity, you will take user input and print out a string of numbers.

## Instructions

* Using a `while` loop, ask the user "How many numbers?", and then print out a chain of numbers in increasing order, from 0 to the user-input number.

* After the results have been printed, ask the user if they would like to continue.

    * If "y" is entered, keep the chain running by inputting a new number and starting a new count from 0 to the new user-input number.

    * If "n" is entered, exit the application.

## Bonus

Rather than just displaying numbers starting from 0, have the numbers begin at the end of the previous chain.

--- 

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Initial variable to track game play
user_play = "y"

# While we are still playing...
while user_play == "y":

    # Ask the user how many numbers to loop through
    user_number = int(input("How many numbers? "))

    # Loop through the numbers. (Be sure to cast the string into an integer.)
    for x in range(user_number):

        # Print each number in the range
        print(x)

    # Once complete...
    user_play = input("Continue: (y)es or (n)o? ")

```
{{% /expand%}}

## ✅ Bonus Solutions
{{%expand "Solutions Click Here" %}}
```python
# Initial variable to track game play
user_play = "y"

# Set start and last number
start_number = 0

# While we are still playing...
while user_play == "y":

    # Ask the user how many numbers to loop through
    user_number = input("How many numbers? ")

    # Loop through the numbers. (Be sure to cast the string into an integer.)
    for x in range(start_number, int(user_number) + start_number):

        # Print each number in the range
        print(x)

    # Set the next start number as the last number of the loop
    start_number = start_number + int(user_number)

    # Once complete...
    user_play = input("Continue the chain: (y)es or (n)o? ")

```
{{% /expand%}}