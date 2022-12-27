+++
title = "06. Down to Input 👩‍🎓👨‍🎓"
weight = 6
tags = ["python"] 
+++

In this activity, you store inputs from the command line and run code based on those inputs.

## Instructions

* Create two different variables, one to take the input of your first name and one for your neighbour’s first name.

* Create two more inputs to ask how many months you and your neighbour have been coding.

* Finally, display a result with both your names and the total amount of months coding.


## ✅ Solutions
{{%expand "Solutions Click Here" %}}

```python
# Take input of you and your neighbour
your_first_name = input("What is your name? ")
neighbour_first_name = input("What is your neighbour's name? ")

# Take how long each of you have been coding
months_you_coded = input("How many months have you been coding? ")
months_neighbour_coded = input("How many months has your neighbour been coding? ")

# Add total months
total_months_coded = int(months_you_coded) + int(months_neighbour_coded)

# Print results
print("I am " + your_first_name + " and my neighbour is " + neighbour_first_name)
print("Together we have been coding for " + str(total_months_coded) + " months!")

```
{{% /expand%}}

