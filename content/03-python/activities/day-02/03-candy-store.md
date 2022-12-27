+++
title = "03.  Kid in a Candy Store  👩‍🎓👨‍🎓"
weight = 3
tags = ["python"] 
+++

In this activity, you will create the code that a candy store will use in their state-of-the-art candy vending machine.

## Instructions

* Create a loop that prints all of the candies in the store to the terminal, with their index stored in brackets beside them.

  * For example: `"[0] Snickers"`

* Create a second loop that runs for a set number of times determined by the variable `allowance`.

  * For example: If allowance is equal to five, the loop should run five times.

  * Each time this second loop runs, take in a user's input, preferably a number, and then add the candy with the matching index to the variable `candy_cart`.

  * For example: If the user enters "0" as their input, "Snickers" should be added into the `candy_cart` list.

* Use another loop to print all of the candies selected to the terminal.

## Bonus

Create a version of the code that allows a user to select as much candy as they want until they say they do not want any more.

---


## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# The list of candies to print to the screen
candy_list = [
    "Snickers",
    "Kit Kat",
    "Sour Patch Kids",
    "Juicy Fruit",
    "Swedish Fish",
    "Skittles",
    "Hershey Bar",
    "Starbursts",
    "M&Ms"
]

# The amount of candy the user will be allowed to choose
allowance = 5

# The list used to store all of the candies selected inside of
candy_cart = []

# Print all of the candies to the screen and their index in brackets
for candy in candy_list:
    print(f'[{str(candy_list.index(candy))}] {candy}')

# Another option to run the for loop involves Python's enumerate method
# This method obtains both the index and the value of an item during a for loop
# for index, candy in candy_list:
#     print(index, candy)

# Run through a loop which allows the user to choose which candies to take home with them
print("Which candy would you like to bring home?")
for x in range(allowance):
    selected = input("Input the number of the candy you want: ")

    # Add the candy at the index chosen to the candy_cart list
    candy_cart.append(candy_list[int(selected)])

# Loop through the candy_cart to say what candies were brought home
print("I brought home with me...")
for candy in candy_cart:
    print(candy)

```

{{% /expand%}}

## ✅ Bonus Solutions
{{%expand "Solutions Click Here" %}}

```python
# The list of candies to print to the screen
candy_list = [
    "Snickers",
    "Kit Kat",
    "Sour Patch Kids",
    "Juicy Fruit",
    "Swedish Fish",
    "Skittles",
    "Hershey Bar",
    "Starbursts",
    "M&Ms"
]

# The amount of candy the user will be allowed to choose
allowance = 5

# The list used to store all of the candies selected inside of
candy_cart = []

# Print all of the candies to the screen and their index in brackets
for i in range(len(candy_list)):
    print("[" + str(i) + "] " + candy_list[i])


# Set answer to "yes" for while loop
answer = "yes"


while answer == "yes":

    # Ask which candy the user would like to bring ho
    print("Which candy would you like to bring home?")
    selected = input("Input the number of the candy you want: ")

    # Add the candy at the index chosen to the candy_cart list
    candy_cart.append(candy_list[int(selected)])

    # ask the user if they want more candy
    answer = input("Would you like to make another selection? ('yes' or 'no') ")


# Loop through the candy_cart to say what candies were brought home
print("I brought home with me...")
for candy in candy_cart:
    print(candy)

```


{{% /expand%}}
