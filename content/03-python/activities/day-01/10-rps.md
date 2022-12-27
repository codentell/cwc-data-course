+++
title = "10.  Rock Paper Scissors 👩‍🎓👨‍🎓"
weight = 10
tags = ["python"] 
+++

Create a Rock, Paper, Scissors game that takes user input from the command line and plays against the computer.

## Instructions

* Using the notebook, take an input of `r`, `p`, or `s` for rock, paper, or scissors.

* Have the computer randomly pick one of these three choices.

* Compare the user's input to the computer's choice to determine if the user won, lost, or tied.

## Hint

* Check out this [Stack Overflow](https://stackoverflow.com/questions/306400/how-to-randomly-select-an-item-from-a-list) question for help with using the `random` module to select a value from a list.

---

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Incorporate the random library
import random

# Print Title
print("Let's Play Rock Paper Scissors!")

# Specify the three options
options = ["r", "p", "s"]

# Computer Selection
computer_choice = random.choice(options)

# User Selection
user_choice = input("Make your Choice: (r)ock, (p)aper, (s)cissors? ")

# Run Conditionals
if (user_choice == "r" and computer_choice == "p"):
    print("You chose rock. The computer chose paper.")
    print("Sorry. You lose.")

elif (user_choice == "r" and computer_choice == "s"):
    print("You chose rock. The computer chose scissors.")
    print("Yay! You won.")

elif (user_choice == "r" and computer_choice == "r"):
    print("You chose rock. The computer chose rock.")
    print("A smashing tie!")

elif (user_choice == "p" and computer_choice == "p"):
    print("You chose paper. The computer chose paper.")
    print("A smashing tie!")

elif (user_choice == "p" and computer_choice == "s"):
    print("You chose paper. The computer chose scissors.")
    print("Sorry. You lose.")

elif (user_choice == "p" and computer_choice == "r"):
    print("You chose paper. The computer chose rock.")
    print("Yay! You won.")

elif (user_choice == "s" and computer_choice == "p"):
    print("You chose scissors. The computer chose paper.")
    print("Yay! You won.")

elif (user_choice == "s" and computer_choice == "s"):
    print("You chose scissors. The computer chose scissors.")
    print("A smashing tie!")

elif (user_choice == "s" and computer_choice == "r"):
    print("You chose scissors. The computer chose rock.")
    print("Sorry. You lose.")

else:
    print("I don't understand that!")
    print("Next time, choose from 'r', 'p', or 's'.")

```
{{% /expand%}}


