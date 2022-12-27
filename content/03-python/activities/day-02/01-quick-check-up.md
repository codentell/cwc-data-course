+++
title = "01. Quick Check-Up 👩‍🎓👨‍🎓"
weight = 1
tags = ["python"] 
+++

Let’s start with a quick warm-up activity to get the Python juices flowing.

## Instructions

Create a simple Python program below that does the following:

* Prints "Hello User!"

* Then asks "What is your name?"

* Then responds "Hello &lt;user's name&gt;"

* Then asks: "What is your favorite number? "

* Then responds: "Your favorite number is lower than mine.", "Your favorite number is higher than mine.", or "Your favorite number is the same as mine!" depending on your favorite number.


## Hint

* Remember to cast your variables!


## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
# Print Hello User!
print("Hello User!")

# Take in User Input
name = input("What is your name? ")

# Respond Back with User Input
print("Hi " + name + "!")

# Take in the User Favorite Number
favorite_number = input("What is your favorite number? ")

# Respond Back with a statement based on your favorite number
if (int(favorite_number) < 7):
    print("Your favorite number is lower than mine.")

elif (int(favorite_number) == 7):
    print("Your favorite number is the same as mine!")

else:
    print("Your favorite number is higher than mine.")
```

{{% /expand%}}

