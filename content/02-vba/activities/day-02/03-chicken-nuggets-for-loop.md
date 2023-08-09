+++
title = "03. Chicken Nuggets 👩‍🎓👨‍🎓"
weight = 3
tags = ["vba"] 
+++

# Looping on Through

Now, it's your chance to see how quickly we can create data using the power of a computer and `for` loops!

## Instructions

Create a `for` loop that will produce the following example. The lines signify new cells.

|  A | B  |  C |
|:---:|:---:|:---:|
| I will eat | 11 | Chicken Nuggets |
| I will eat | 12 | Chicken Nuggets |
| I will eat | 13 | Chicken Nuggets |
| I will eat | 14 | Chicken Nuggets |
| I will eat | 15 | Chicken Nuggets |
| I will eat | 16 | Chicken Nuggets |
| I will eat | 17 | Chicken Nuggets |
| I will eat | 18 | Chicken Nuggets |
| I will eat | 19 | Chicken Nuggets |
| I will eat | 20 | Chicken Nuggets |

## Bonus

If you finish early, consider why you may prefer using a `for` loop over the `range()` function.

—

## ✅ Solutions
{{%expand "Solutions Click Here" %}}
```vb
Sub loops_and_loops()

    ' Loop through first 10 rows
    For i = 1 To 10

        ' Set values in column 1 to "I will eat"
        Cells(i, 1).Value = "I will eat "

        ' Set values in column 2 to the sum of the counter + 10 
        Cells(i, 2).Value = i + 10

        ' Set values in column 3 to "Chicken Nuggets"
        Cells(i, 3).Value = "Chicken Nuggets"

    ' Call the next iteration
    Next i

End Sub
```
{{% /expand%}}

