+++
title = "07. Functions 👩‍🎓👨‍🎓"
weight = 7
tags = ["python"] 
+++

In this activity, you will write a function to compute the arithmetic mean (average) for a list of numbers.

## Instructions

* Write a function called `average` that accepts a list of numbers.

  * The function `average` should return the arithmetic [mean](https://en.wikipedia.org/wiki/Arithmetic_mean) (average) for a list of numbers.

* Test your function by calling it with different values and printing the results.

- - -

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```python
# Write a function that returns the arithmetic average for a list of numbers
def average(numbers):
    length = len(numbers)
    total = 0.0
    for number in numbers:
        total += number
    return total / length


# Test your function with the following:
print(average([1, 5, 9]))
print(average(range(11)))


```
{{% /expand%}}